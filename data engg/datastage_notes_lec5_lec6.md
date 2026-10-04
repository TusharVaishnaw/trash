# DataStage Notes: Lectures 5 & 6 (Partitioning & Pipelining)

---

# Lecture 5: Partitioning & Pipelining – Part 1

## What partitioning is
- Heart of DataStage performance
- **Data gets divided, not the script.** The same (Orchestrate) script is pushed to every node; each node processes its own slice of the data.
- Number of partitions is decided by the **APT config file**. In grid topology, the resource manager generates it dynamically.
- Partition = node = server (same thing in DataStage terms)
- Analogy: 4 household tasks take 4 hrs alone, 2 hrs with a second person. Or a project manager adding people to hit a 30-day deadline.
- Ideal case: 1000 records / 4 nodes = 250 each. Union of all subsets = original data (if no group by/aggregate/join happens).
- Flow in a job: source -> **partitioning** -> transform -> **repartitioning** (if needed) -> target. All nodes run in parallel.

## APT configuration file
- Env variable: `APT_CONFIG_FILE` (visible in Administrator -> Environment Variables)
- Per node it has:
  - `node1`, `node2`... = partition 1, 2...
  - **fastname**: server name or IP. If all nodes are on one machine, they all show the same name (like opening Chrome 4 times).
  - **pools**: which operations run on that node. `""` = everything. Can restrict, e.g. `"sort"`, `"join"`, `"rmdp"` (remove duplicates).
    - Pinning an operation to one node is a bad idea. E.g. remove duplicates on node 4 means 3M records flood the network to node 4, then get re-sent out again.
  - **resource disk**: where **datasets** get created
  - **scratch disk**: where **temporary files** go during execution
- In **cluster** topology you write this manually. In **grid** topology it's generated at runtime, so you can't pin operations to specific nodes.

## Why it's faster: the 20,000 records example
Assumptions: 4 equal nodes, 5 stages that just "fetch and push", 20,000 records, 4 min per stage for the full 20k (the instructor first said 5 min, then simplified to 4).

| Mode | How | Time |
|---|---|---|
| **Sequential** | Each stage waits for the previous to finish all 20k, so 4 stages idle while 1 works | 20 min (5 stages x 4 min) |
| **Pipelining only** | Data split into 4 chunks of 5,000. Stage 2 starts on chunk 1 while stage 1 pulls chunk 2 (waterfall, like YouTube buffering) | 8 min |
| **Partitioning only** | 4 nodes x 5,000 records each, sequential on each node | 5 min |
| **Partitioning + Pipelining** | 4 nodes, each pipelines 4 chunks of 1,250 (15 sec per stage) | **2 min** |

- 10x faster in this best-case example (real gains are smaller, but still big)
- **Pipelining** = overlap stages on small chunks. **Partitioning** = split data across nodes. **Parallelism** = result of both.

---

# Lecture 6: Partitioning & Pipelining – Part 2 (Algorithms)

## 9 algorithms, in 2 groups
| Keyless | Keyed |
|---|---|
| Round Robin, Random, Entire, Same | Hash, Modulus, DB2, Range |

Plus **Auto** (generic, picks one of the above automatically).

## Keyless vs Keyed
| | Keyless | Keyed |
|---|---|---|
| Key column needed? | No | Yes (mandatory) |
| Records per node | Equal (or off by 1) | **Not guaranteed equal** |
| Same key -> same node? | **No** | **Yes (guaranteed)** |
| Problem | Wrong results for group by / join / aggregation | Possible skew (uneven load) |

**Why it matters (bank example):** account 1 has $100 and $300 on two nodes. With keyless, each node shows a partial sum ($100 and $300), not the true $400. With keyed partitioning on account number, both rows go to one node and the aggregate is correct.

## Keyless algorithms
1. **Round Robin**: record 1 -> node 1, record 2 -> node 2, 3 -> node 3, record 4 -> node 1 again (cyclic). No key, no calculation. **Default** when you don't pick anything. Leftover records (e.g., 17 / 3) mean one node gets one fewer.
2. **Random**: records assigned by a random number. Tries to balance counts, but has extra overhead. If used as the *first* stage (doesn't know the record count), counts can end up uneven (a few records off).
3. **Entire**: **every record goes to every node.** Used only on the **reference link of a Lookup stage**, so the lookup data is present wherever the master data lands (avoids mismatch between partitioning of master and reference).
4. **Same**: don't repartition, keep the previous stage's partitioning. Useful after a keyed partition when later stages use the **same key** (e.g., account + month -> then account -> then month totals), so you skip a repartition. Pointless after keyless methods.

## Keyed algorithms
5. **Hash**: **most used (80-90% of jobs).**
   - Accepts any data type, and **one or multiple (composite) key columns**
   - Concatenates key columns -> hashing algorithm -> node number
   - Same key always same node. Load can be uneven (one node could even be empty).
   - **Skew example:** key = gender (only 2 values) means only 2 nodes get data, the others sit idle. Fix: add another key column (e.g., account number) *only if the business logic allows it*. You can't for "total by gender", since grouping needs gender alone.
   - Has overhead from hashing, but gives the correctness that group by / join need.
6. **Modulus**: key must be a **single integer/numeric column**. Node = `key MOD number_of_partitions`. DataStage counts nodes from **0**, so node 1 in human terms is node 0. Same key -> same remainder -> same node. Limits: one column only, numeric only.
7. **DB2**: use the existing DB2 table partitioning (e.g., by month-year). Only useful if the source is partitioned DB2. **Rarely used.** Danger: if DB2 has 6 partitions but DataStage has 4 nodes, extra partitions have nowhere to go and data can be lost.
8. **Range**: partition by value ranges (like `WHERE amount BETWEEN 100 AND 500`). Used with Lookup. DataStage must first build a **range map** (internal index) then use it, so it's a multi-step process. Databases do this far more easily, so it's **rarely used in DataStage**.

## 9. Auto
- Picks the method based on the **stage** + **key columns**:
  - Stage needs a key (Join, Merge, Sort, Remove Duplicates, Aggregator...) -> **Hash**
  - No key needed -> **Round Robin**
  - Lookup reference link -> **Entire**
  - Consecutive stages with the same key -> **Same** (no repartition)
- From **version 8.7 onwards** DataStage is smart enough that you can just leave it on Auto. Before 8.7 you had to set partitioning on each stage explicitly.
- Still worth knowing the algorithms: when output is wrong or counts mismatch, partitioning knowledge helps you debug.

---

## Quick revision / likely interview questions
- Partitioning vs pipelining vs parallelism: difference?
- Does DataStage partition the script or the data?
- What's in the APT config file? (node, fastname, pools, resource disk, scratch disk)
- Keyed vs keyless: which guarantees same-key-same-node? Which guarantees equal counts?
- Why can keyless give wrong aggregation results?
- Default partitioning if you pick nothing? (Round Robin)
- Why use Entire on a Lookup reference link?
- Hash vs Modulus: data types and number of key columns?
- What causes skew in hash, and how do you fix it?
- What does Auto choose for Join/Sort? Lookup reference? (Hash / Entire)
- Why are DB2 and Range rarely used?
