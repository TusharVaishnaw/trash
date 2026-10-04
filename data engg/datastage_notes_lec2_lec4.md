# DataStage Notes: Lectures 2 & 4

---

# Lecture 2: Information Server Architecture & Job Types

## Information Server Suite
- Suite of ~10-11 products (Blueprint Director, Business Glossary, Information Analyzer, **DataStage**, QualityStage, FastTrack, Metadata Workbench, etc.)
- Flow: understand source (Info Analyzer) -> clean/transform/load (DataStage ETL) -> view across multiple warehouses (Federation Server, data virtualization)
- All products share the same architecture

## 4 Tiers
| Tier | Role | Where installed |
|---|---|---|
| **Client** | Admin / Designer / Director clients | Your local machine (any number) |
| **Service** | Services + application server | Server |
| **Engine** | Job execution, connectors, logging | Server |
| **Metadata Repository** | Stores everything in DB2 (`XMETA` schema, name fixed) | Server |

Can all go on one server or be spread across many. Client always separate.

### Service Tier
- **Common services**: reusable across all products (e.g., DB connectivity). One set installed no matter how many products. This avoids duplicate connectors for each product, saving resources.
- **Product-specific services**: only for that product (e.g., Info Analyzer column profiling; DataStage cloud connectivity to Salesforce/AWS/Redshift).
- **Application server**: makes the service tier behave like a server and responds to client login requests.
- **Login flow**: client logs into the *service tier only*. Engine credentials are stored once via **engine mapping in Web Console** (one-time setup). App server uses them to verify the engine. If missing/wrong, you get errors like "engine mapping not done / credentials not available".

### Engine Tier
- All **job execution** happens here
- Information Server Engine runs the 3 job types: server, parallel, sequence
- **Packs**: add-on features (e.g., Balanced Optimization, cloud connectors like Salesforce/AWS). Were separate in 9.1/11.0/11.1, bundled by default in 11.5 (at higher cost).
  - Why packs exist: new components may not be fully tested on real data. Packs can be removed if they cause issues, protecting the core product's reputation.
- **Connectors**: front-end placeholders where you enter connection info (IP, schema, user/pass, select/insert/update/delete, tuning). Actual connectivity is executed through the service tier.
- **Logging** sits in the engine tier (not service tier) because job logs are huge, and sending them across the network to a separate service tier would be a burden.
- Job monitor and resource tracker are service agents too.

### Metadata Repository Tier: how a DB job runs
1. Engine sends connection info from job executable to service tier
2. Service tier (common services) tests/opens the connection
3. It hands the open connection + statement to the Metadata Repository tier
4. That tier runs it (select/insert/update) and sends the response back via service tier -> engine tier

### Client connections
- Login / admin -> client to **service tier**
- Running a job -> client directly to **engine tier**
- Engine needs DB access -> engine to service tier (common services) -> repository

## Why tiers were split (history)
- DataStage was originally by Ascential, taken over by IBM around 2007-08
- Everything was once on one system, which was fine for small data/few users
- More users + more data = slow performance, so tiers were separated onto different servers, then multiple servers, then grid

## Two Engines
- **Server Engine**: runs server jobs + sequencer jobs (Basic compiler)
- **Parallel Engine**: runs parallel jobs (Orchestrate/OSH compiler)

## Job Types (very important)
| | Server | Parallel | Sequencer |
|---|---|---|---|
| Colour | Yellow | Red | Green |
| Execution | Sequential, one server | **Parallel** (partitioning + pipelining) | Sequential (control flow) |
| Engine | Server engine | Parallel engine | Server engine |
| Compiler | Basic | Orchestrate (OSH) | Basic |
| Stages | ~8-10 | ~30-40 | Job Activity, Execute Command, Routine Activity, File Watcher/Activity, etc. |
| Use | Legacy, slow | **Most widely used** | Controls order/dependency of other jobs |

- You **cannot** use server stages in parallel jobs or vice versa
- **Sequencer** can trigger server, parallel, or other sequence jobs. It hands control to the right compiler/engine for each, and gets it back when done.
- **Routines**:
  - *Server routines*: C/C++ code, only callable by server jobs. Written because server jobs had few stages.
  - *Parallel routines*: not real code, just an **interface** to invoke server-routine C++ in parallel. Rarely needed since parallel has so many stages.
- **Transformer** stage is coded in C++. Visual C++ must be installed. A job with a Transformer is compiled by **both** Orchestrate and C++ compiler.
- Runtime monitoring for all jobs is in **Director**
- Course covers **parallel + sequencer** jobs only, not server jobs
- In companies, client access usually via Citrix, and what you see (Designer, Director, Admin) depends on the Citrix admin

---

# Lecture 4: Deployment Topologies

4 types: **Two-tier -> Three-tier -> Cluster -> Grid**

## 1. Two-Tier
- Client on one machine; service + engine + repository all on **one server**
- Original setup. Fine for small teams/data.
- Fails with more users/data (one server for everyone, so it gets slow)

## 2. Three-Tier
- Client | Engine on one server | Service + Repository on another server
- The two servers know each other's IPs
- Better performance, but again slows down as data/users grow

## 3. Cluster
- Like three-tier but **multiple engine tiers** (e.g., 4 engine servers), with service + repository on a separate server
- **Problem 1:** which engine runs which job? Initially assigned per project (A->engine 1, B->engine 2...). If projects C/D shut down but A/B grow, engines 3-4 sit idle.
- **Fix: APT configuration file** (`node1, node2...`) lists the servers/engines a job runs on, plus things like scratch/dataset locations. You can have different config files pointing projects at different engines.
- **Problem 2:** if an engine crashes, jobs pointing to it abort (e.g., "node1 could not be reached"). Someone must **manually edit/create a new config file**. Developers may not have the access/knowledge to do that.
- Idle engines also require manual config changes
- Note: **dev boxes** are usually still cluster-style (small data, not much engine capacity needed)

## 4. Grid
- Adds a **Resource Manager (Workload Manager)** that **creates the APT config file dynamically (on the fly)**
- Jobs just go to the resource manager. It checks the job's **score**, resource needs, config + env variables, and picks servers with free capacity.
- Keeps a database of every server's load. Updates it after each allocation so new jobs go elsewhere.
- **Heartbeat**: resource manager constantly pings slave nodes; they report status, running jobs, free resources.
  - If a node stops responding, it's marked dead and its jobs are **moved automatically** to other nodes
- **Primary + secondary resource manager** for failover. When the primary returns, the secondary hands the job info back.
- **Multi-instance execution**: multiple instances of a job on the same server if resources allow (like many Chrome windows)
- **Architecture**: few high-end servers as resource managers, lots of cheap **commodity hardware** as compute nodes (similar to Hadoop)
  - Losing a few cheap nodes barely hurts
  - Cheaper, highly scalable (just add servers)
- Grid is only for products that process big data: **DataStage, QualityStage, Information Analyzer**

### Grid environment variables (9.1+)
| Variable | Meaning |
|---|---|
| `APT_GRID_ENABLED` | Use grid (dynamic config) vs normal cluster (config file path). **Only one you can change on the fly.** |
| `APT_GRID_QUEUE` | Queue where jobs wait when no resources are free |
| `APT_GRID_PARTITIONS` | Instances/partitions per compute node (default 1) |
| `APT_GRID_COMPUTE_NODES` | Number of servers a job runs on |

The last three are fixed by the admin. Don't change them yourself.

---

## Quick revision / likely interview questions
- What are the 4 tiers and what does each do?
- Why is logging in the engine tier?
- What is engine mapping, and when do you see the errors?
- Server vs Parallel vs Sequencer: colour, engine, compiler, stages
- What is a parallel routine really?
- Why does a Transformer need C++?
- Two-tier vs three-tier vs cluster vs grid, and what problem each solved
- What is the APT config file? What does the resource manager change about it?
- How does grid handle a failed node or failed resource manager?
