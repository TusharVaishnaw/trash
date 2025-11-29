# CHAPTER INDEX

+----+--------------------------------------------------------+-------+
| >  | > **TITLE**                                            | > *   |
| ** |                                                        | *PAGE |
| S. |                                                        | >     |
| ** |                                                        | NO.** |
| >  |                                                        |       |
| >  |                                                        |       |
|  * |                                                        |       |
| *N |                                                        |       |
| o. |                                                        |       |
| ** |                                                        |       |
+====+========================================================+=======+
|    | > **Certificate**                                      | >     |
|    |                                                        | **i** |
+----+--------------------------------------------------------+-------+
|    | > **Declaration**                                      | > *   |
|    |                                                        | *ii** |
+----+--------------------------------------------------------+-------+
|    | > **Preface**                                          | > **  |
|    |                                                        | iii** |
+----+--------------------------------------------------------+-------+
|    | > **Acknowledgement**                                  | > *   |
|    |                                                        | *iv** |
+----+--------------------------------------------------------+-------+
| >  | > **Introduction**                                     | > **  |
| ** |                                                        | 1-3** |
| 1. |                                                        |       |
| ** |                                                        |       |
+----+--------------------------------------------------------+-------+
|    | > 1.1 Introduction                                     | >     |
|    |                                                        | **1** |
+----+--------------------------------------------------------+-------+
|    | > 1.2 Purpose                                          | >     |
|    |                                                        | **2** |
+----+--------------------------------------------------------+-------+
|    | > 1.3 Scope                                            | >     |
|    |                                                        | **2** |
+----+--------------------------------------------------------+-------+
|    | > 1.4 Features                                         | >     |
|    |                                                        | **3** |
+----+--------------------------------------------------------+-------+
|    | > 1.5 Importance                                       | >     |
|    |                                                        | **3** |
+----+--------------------------------------------------------+-------+
| >  | > **Background And Literature Review**                 | > **  |
| ** |                                                        | 4-8** |
| 2. |                                                        |       |
| ** |                                                        |       |
+----+--------------------------------------------------------+-------+
|    | > 2.1 Understanding Deepfakes and Their Underlying     | >     |
|    | > Architecture                                         | **4** |
+----+--------------------------------------------------------+-------+
|    | > 2.2 The Emergence of AI Forensics                    | >     |
|    |                                                        | **5** |
+----+--------------------------------------------------------+-------+
|    | > 2.3 Ethical and Social Dimensions of Deepfake        | >     |
|    | > Technology                                           | **6** |
+----+--------------------------------------------------------+-------+
|    | > 2.4 Emerging Trends in Deepfake Detection and        | >     |
|    | > Forensics                                            | **7** |
+----+--------------------------------------------------------+-------+
|    | > 2.5 Related Research, Datasets, and Key Developments | >     |
|    |                                                        | **7** |
+----+--------------------------------------------------------+-------+

## **CHAPTER 1 INTRODUCTION**

### 1.1 Introduction

Artificial Intelligence has revolutionized the landscape of digital media creation, enabling unprecedented capabilities in image synthesis, voice cloning, and video manipulation. Among the most remarkable—and concerning—developments in this domain is the emergence of deepfake technology. Deepfakes are AI-generated synthetic media that can convincingly replicate human faces, voices, and behaviors with photorealistic precision. Powered by sophisticated deep learning architectures such as Generative Adversarial Networks (GANs), Variational Autoencoders (VAEs), and Diffusion Models, deepfakes have evolved from experimental research projects into widely accessible tools that anyone can use with minimal technical expertise.

While deepfake technology offers promising applications in fields such as entertainment, education, accessibility services, and digital art, its potential for misuse has raised severe ethical, social, and security concerns. The ability to create fabricated yet realistic videos of public figures, manipulate evidence, or generate non-consensual explicit content poses fundamental threats to individual privacy, democratic integrity, and societal trust in digital media.

The term **AI-Powered Deepfake Forensics** has emerged to describe the specialized field dedicated to detecting, analyzing, and mitigating the threats posed by synthetic media. This interdisciplinary domain combines expertise from computer vision, machine learning, signal processing, cybersecurity, and digital forensics to develop robust systems capable of distinguishing authentic content from AI-generated manipulations.

According to recent studies, the volume of deepfake content circulating online doubles approximately every six months, with over 90% involving malicious or deceptive uses including misinformation campaigns, financial fraud, political manipulation, and identity theft. This exponential growth has created an urgent need for effective forensic technologies that can authenticate digital media and preserve trust in visual and auditory evidence.

This seminar explores the foundations of deepfake technology, examines state-of-the-art forensic detection methodologies, evaluates current challenges and limitations, and discusses future directions for building resilient authentication systems capable of protecting digital integrity in an era of increasingly sophisticated synthetic media.

### 1.2 Purpose

The primary purpose of this seminar is to comprehensively study the field of **AI-Powered Deepfake Forensics** and investigate how advanced detection systems can identify, classify, and mitigate the threats posed by synthetic media. Specifically, the seminar aims to:

-   **Understand Deepfake Generation Mechanisms**: Examine the underlying architectures and algorithms—including GANs, autoencoders, and diffusion models—that enable the creation of photorealistic synthetic media.

-   **Analyze Forensic Detection Techniques**: Explore state-of-the-art detection methodologies spanning spatial analysis, temporal analysis, frequency domain analysis, biological signal detection, and multimodal approaches.

-   **Evaluate Detection Performance and Limitations**: Critically assess the effectiveness of current forensic systems, identifying challenges related to generalization, adversarial robustness, dataset bias, and real-world deployment.

-   **Review Datasets and Benchmarking Frameworks**: Survey prominent datasets such as FaceForensics++, DFDC, Celeb-DF, and ForgeryNet that enable standardized evaluation and comparison of detection systems.

-   **Examine Real-World Applications**: Investigate how deepfake forensics is being integrated into social media platforms, law enforcement agencies, digital evidence verification systems, and content authentication initiatives.

-   **Discuss Ethical and Legal Dimensions**: Consider the broader implications of deepfake technology on privacy rights, information integrity, democratic processes, and the need for regulatory frameworks.

-   **Propose Future Research Directions**: Identify promising avenues for advancement including explainable AI, cross-modal detection, blockchain-based provenance tracking, and international standardization efforts.

### 1.3 Scope

The scope of this seminar is primarily conceptual, analytical, and survey-oriented. It focuses on:

-   **Theoretical foundations** of deepfake generation and forensic detection methodologies.

-   **Comprehensive review** of existing detection techniques across spatial, temporal, frequency, biological, and multimodal domains.

-   **Critical evaluation** of prominent datasets, benchmarking protocols, and performance metrics used in the research community.

-   **Analysis of real-world case studies** demonstrating the application of forensic systems in social media moderation, law enforcement, and digital authentication.

-   **Discussion of challenges** including generalization limitations, adversarial attacks, compression artifacts, and ethical considerations.

-   **Exploration of emerging trends** such as GAN fingerprinting, self-supervised learning, edge-AI deployment, and blockchain integration.

Hands-on implementation of detection algorithms, creation of new datasets, or development of novel forensic architectures are beyond the scope of this seminar and are considered areas for future practical work. The focus remains on understanding the current state-of-the-art, identifying gaps in existing approaches, and outlining directions for continued research and development.

### 1.4 Features

The field of AI-Powered Deepfake Forensics is characterized by several key features and capabilities:

**Multi-Layered Detection Approaches**: Forensic systems employ diverse methodologies including spatial artifact analysis, temporal inconsistency detection, frequency domain examination, and biological signal verification to create robust multi-evidence frameworks.

**Deep Learning-Based Classification**: Modern detectors leverage sophisticated neural architectures such as Convolutional Neural Networks (CNNs), Recurrent Neural Networks (RNNs), Vision Transformers (ViTs), and hybrid models for automated feature extraction and classification.

**Multimodal Integration**: Advanced systems combine visual, audio, and metadata analysis to detect inconsistencies across multiple sensory modalities, significantly improving detection reliability.

**Biological Signal Analysis**: Exploitation of subtle physiological markers—including heart rate variations (remote photoplethysmography), micro-expressions, eye movements, and breathing patterns—that are difficult for AI models to replicate accurately.

**GAN Fingerprinting and Attribution**: Identification of unique signatures left by specific generative architectures, enabling not only detection but also attribution to particular synthesis methods or tools.

**Real-Time and Edge Deployment**: Development of lightweight, efficient models capable of operating on mobile devices and web browsers for immediate content verification.

**Explainable AI Integration**: Incorporation of interpretability mechanisms such as attention maps, gradient-based visualization, and decision explanation to make forensic verdicts transparent and legally admissible.

**Adversarial Robustness**: Design of detection systems that maintain effectiveness even when attackers apply adversarial perturbations or compression techniques to evade detection.

**Blockchain and Cryptographic Authentication**: Integration with immutable provenance tracking systems that verify content authenticity from creation through distribution.

### 1.5 Importance

AI-Powered Deepfake Forensics has become critically important for several interconnected reasons:

-   **Preservation of Information Integrity**: In an era where "seeing is believing" no longer holds true, forensic systems are essential for maintaining trust in digital media, journalism, and public discourse. Without reliable authentication mechanisms, society faces a potential collapse of information credibility.

-   **Protection of Democratic Processes**: Deepfakes pose existential threats to elections, governance, and public deliberation by enabling sophisticated disinformation campaigns. Forensic detection helps safeguard democratic integrity by identifying and flagging manipulated political content before it spreads.

-   **Individual Privacy and Safety**: The majority of deepfakes involve non-consensual pornography and identity theft, causing severe psychological harm and reputational damage to victims. Forensic technologies provide crucial tools for victim protection and perpetrator identification.

-   **Financial Security**: Voice cloning and video impersonation enable sophisticated fraud schemes targeting individuals and corporations. Detection systems help prevent financial losses and protect organizational security.

-   **Legal Evidence Verification**: As deepfakes become more sophisticated, courts and law enforcement agencies require reliable forensic tools to authenticate evidence and prevent miscarriages of justice based on fabricated media.

-   **Social Media Content Moderation**: Platforms serving billions of users need scalable, automated detection systems to identify and remove malicious synthetic content while preserving legitimate creative expression.

-   **National Security**: Intelligence agencies and defense organizations require forensic capabilities to detect state-sponsored disinformation campaigns and protect critical infrastructure from manipulation.

-   **Ethical AI Development**: The forensics field drives broader conversations about responsible AI development, encouraging transparency, accountability, and ethical considerations in generative technology research.

-   **Global Standardization and Policy**: Forensic research informs international efforts to establish technical standards, legal frameworks, and regulatory mechanisms for addressing synthetic media challenges.

-   **Technological Arms Race**: As generative models continuously improve, forensic detection must evolve in parallel to maintain effectiveness. This co-evolution drives innovation in both security and AI research domains.

# CHAPTER 2  **BACKGROUND AND LITERATURE REVIEW**

### 2.1 Understanding Deepfakes and Their Underlying Architecture

The term **deepfake** emerged from the combination of "deep learning" and "fake," first gaining widespread attention in 2017 when AI-generated celebrity face swaps appeared on online platforms. What began as experimental research in computer vision has evolved into a sophisticated technology capable of creating synthetic media virtually indistinguishable from authentic content.

At the core of deepfake generation lies the concept of **Generative Adversarial Networks (GANs)**, introduced by Ian Goodfellow and colleagues in 2014. GANs represent a revolutionary approach to machine learning, operating through an adversarial process between two neural networks:

1. **The Generator**: Creates synthetic data samples by learning patterns from training datasets. It attempts to produce increasingly realistic outputs that can fool the discriminator.

2. **The Discriminator**: Acts as a classifier that attempts to distinguish between real samples from the training data and fake samples produced by the generator.

Through iterative training, these networks engage in a competitive game where the generator continuously improves its ability to create realistic samples, while the discriminator enhances its capability to detect fakes. This adversarial dynamic drives both networks toward optimal performance, ultimately resulting in a generator capable of producing highly convincing synthetic media.

**Evolution of Generative Architectures:**

Modern deepfake systems extend beyond basic GANs, employing advanced architectural variants that enhance realism, control, and quality:

- **Conditional GANs (cGANs)**: Allow conditioning on additional information such as class labels or text descriptions, enabling controlled generation of specific attributes or features.

- **StyleGAN and StyleGAN2/3**: Developed by NVIDIA, these architectures introduced style-based generation that provides unprecedented control over facial features, expressions, and visual attributes. StyleGAN3 particularly addresses temporal consistency and reduces artifacts, making it ideal for video synthesis.

- **CycleGAN**: Enables image-to-image translation without paired training data, facilitating domain transfer such as converting images from one style to another while preserving content.

- **Variational Autoencoders (VAEs)**: Employ probabilistic encoding and decoding to generate new samples from learned latent representations, offering an alternative approach to GANs with different trade-offs in quality and diversity.

- **Diffusion Models**: Recent innovations like Stable Diffusion and DALL·E 3 use iterative denoising processes to generate high-fidelity images and videos. These models have demonstrated exceptional quality and are increasingly being adapted for video synthesis.

- **Transformer-Based Models**: Architectures like Vision Transformers (ViTs) are being integrated into generative pipelines, leveraging attention mechanisms for improved spatial coherence and long-range dependencies.

**The Deepfake Creation Pipeline:**

Creating a deepfake typically involves three fundamental stages:

1. **Data Acquisition and Preprocessing**: Large datasets containing thousands of images or video frames of the target subject are collected. These undergo preprocessing including face detection, alignment, cropping, and normalization to ensure consistency.

2. **Model Training**: The preprocessed data feeds into neural architectures (typically GANs or autoencoders) that learn to encode facial features, expressions, and movements. Training can require days or weeks on high-performance GPUs, depending on dataset size and model complexity.

3. **Post-Processing and Refinement**: Generated outputs undergo enhancement through techniques such as:
   - **Face Blending**: Seamlessly merging synthetic faces with original backgrounds
   - **Color Correction**: Matching lighting and color tone to the source environment
   - **Temporal Smoothing**: Ensuring frame-to-frame consistency in videos
   - **Super-Resolution**: Enhancing output quality through upscaling networks
   - **Audio Synchronization**: Aligning lip movements with voice tracks for audio-visual deepfakes

**Technical Sophistication:**

Modern deepfake systems achieve photorealistic quality through several technical innovations:

- **High-Resolution Generation**: Models can now produce 1024x1024 or higher resolution outputs with fine-grained details including skin texture, hair strands, and subtle lighting effects.

- **Expression Transfer**: Advanced architectures can transfer facial expressions, head poses, and eye movements from driving videos to target faces while preserving identity.

- **Voice Cloning**: Text-to-speech (TTS) systems and voice conversion models enable synthesis of realistic speech in target voices with appropriate prosody, accent, and emotional tone.

- **Full-Body Synthesis**: Beyond faces, recent models can generate entire body movements, gestures, and interactions, expanding the scope of deepfake applications.

This level of sophistication has rendered traditional image forgery detection techniques—such as error level analysis, JPEG compression artifact detection, or simple pixel inconsistency checks—largely ineffective against modern AI-generated content. The arms race between generation and detection continues to accelerate, necessitating equally sophisticated forensic approaches.

### 2.2 The Emergence of AI Forensics

As deepfake technology proliferated and its potential for misuse became apparent, the research community recognized the urgent need for robust detection mechanisms. This gave rise to **AI Forensics**—a specialized discipline focused on identifying, analyzing, and attributing AI-generated manipulations in digital media.

**Early Detection Approaches:**

Initial deepfake detection efforts relied on identifying visual artifacts and biological inconsistencies that generative models failed to replicate accurately:

- **Eye Blinking Analysis**: Early GAN-generated faces exhibited abnormal or absent blinking patterns because training datasets predominantly contained images with open eyes. Researchers exploited this limitation by analyzing blink frequency and duration.

- **Facial Geometry Inconsistencies**: Subtle distortions in facial proportions, asymmetries, or unnatural head poses provided detection signals, particularly in low-quality deepfakes.

- **Lighting and Shadow Anomalies**: Inconsistent illumination across facial regions or mismatched shadows indicated synthetic manipulation.

- **Color Space Irregularities**: Unusual distributions in RGB or YCbCr color channels revealed artifacts introduced during the generation process.

While these methods showed promise initially, they quickly became obsolete as generative models improved and learned to address these obvious shortcomings.

**Transition to Deep Learning-Based Detection:**

Recognizing that manually designed features could not keep pace with advancing generation techniques, researchers shifted toward **deep learning-based forensic systems** capable of automatically learning discriminative patterns:

- **Convolutional Neural Networks (CNNs)**: Architectures such as XceptionNet, ResNet, EfficientNet, and VGG were adapted for binary classification (real vs. fake) by training on large datasets of authentic and manipulated media.

- **Transfer Learning**: Pre-trained models from image classification tasks were fine-tuned on deepfake datasets, leveraging learned representations to detect subtle manipulation artifacts.

- **Feature Extraction**: CNNs automatically learn hierarchical features from low-level edges and textures to high-level semantic concepts, enabling detection of complex forgery patterns invisible to human observers.

**Landmark Datasets and Competitions:**

The advancement of AI forensics was significantly accelerated by the release of standardized datasets and competitive challenges:

- **FaceForensics++ (2019)**: A pioneering dataset containing over 1,000 original videos and manipulations created using FaceSwap, Face2Face, DeepFakes, and NeuralTextures. It established evaluation protocols with multiple compression levels (c0, c23, c40) to simulate real-world degradation.

- **DeepFake Detection Challenge (DFDC, 2020)**: Organized by Meta AI and Kaggle, this initiative provided over 100,000 videos featuring diverse demographics, lighting conditions, and manipulation techniques. The accompanying competition attracted thousands of participants worldwide, catalyzing innovation in detection methodologies.

- **Celeb-DF (2020)**: Addressed the quality limitations of earlier datasets by providing high-resolution videos with natural facial expressions and subtle manipulations more representative of sophisticated real-world deepfakes.

**Evolution of Detection Architectures:**

As the field matured, detection systems evolved from simple binary classifiers to sophisticated multi-stage pipelines:

- **Attention Mechanisms**: Integration of attention modules enabled models to focus on forensically relevant regions such as facial boundaries, eyes, and mouth areas where artifacts commonly appear.

- **Recurrent Neural Networks (RNNs) and LSTMs**: Temporal analysis architectures captured inconsistencies across video frames, detecting unnatural motion patterns or frame-to-frame discontinuities.

- **Vision Transformers (ViTs)**: Recent adoption of transformer architectures leverages self-attention mechanisms for both spatial and temporal analysis, achieving state-of-the-art performance on benchmark datasets.

- **Ensemble Methods**: Combining multiple detection models with complementary strengths (e.g., spatial CNN + temporal RNN + frequency analysis) improves robustness and reduces false positives.

**Current State-of-the-Art:**

Contemporary forensic systems employ multi-modal, multi-scale approaches that analyze:

- **Spatial Features**: Pixel-level inconsistencies, texture anomalies, and compression artifacts
- **Temporal Features**: Motion patterns, optical flow, and frame consistency
- **Frequency Features**: Spectral signatures and frequency domain anomalies
- **Biological Features**: Physiological signals and behavioral patterns
- **Semantic Features**: Contextual inconsistencies and logical implausibilities

Despite significant progress, challenges remain. Detection models trained on specific datasets often fail to generalize to unseen manipulation techniques, compression artifacts from social media reduce detection accuracy, and adversarial attacks can evade even state-of-the-art systems. These limitations drive ongoing research into more robust, adaptive, and explainable forensic methodologies.

### 2.3 Ethical and Social Dimensions of Deepfake Technology

The proliferation of deepfake technology has raised profound ethical concerns that extend far beyond technical considerations. These concerns intersect with fundamental rights, social trust, and the integrity of digital communication:

-   **Privacy Violations and Non-Consensual Content**: The majority of deepfake videos circulating online involve non-consensual pornography, primarily targeting women. This represents a severe violation of personal dignity and privacy rights, causing psychological trauma and reputational damage to victims.

-   **Misinformation and Democratic Integrity**: Deepfakes pose existential threats to democratic processes by enabling the creation of fabricated speeches, statements, or actions by political figures. Such content can influence elections, incite violence, or undermine public trust in legitimate media.

-   **Identity Theft and Fraud**: Synthetic media enables sophisticated impersonation attacks, including voice cloning for financial fraud, fake video calls for corporate espionage, and fabricated evidence in legal proceedings.

-   **Erosion of Trust in Digital Media**: As deepfakes become more sophisticated, society faces a "reality crisis" where authentic evidence can be dismissed as fake, and fabricated content can be perceived as real. This phenomenon, known as the "liar's dividend," threatens the foundations of digital evidence and journalistic integrity.

-   **Social Manipulation and Cyberbullying**: Malicious actors exploit deepfake technology for harassment, extortion, and reputation destruction, disproportionately affecting vulnerable populations including minors, public figures, and marginalized communities.

The ethical imperative for deepfake forensics extends beyond detection—it encompasses prevention, education, and the establishment of legal frameworks that balance innovation with protection of fundamental human rights.

### 2.4 Emerging Trends in Deepfake Detection and Forensics

The field of deepfake forensics is rapidly evolving, with several promising research directions and technological innovations:

-   **Multimodal Detection Systems**: Integration of visual, audio, and physiological signals to create comprehensive detection frameworks that analyze multiple evidence streams simultaneously.

-   **Biological Signal Analysis**: Exploitation of subtle biological markers such as heart rate variations (remote photoplethysmography), micro-expressions, eye movement patterns, and breathing rhythms that are difficult for AI models to replicate accurately.

-   **GAN Fingerprinting**: Identification of unique signatures left by specific generative architectures, enabling not only detection but also attribution to particular synthesis methods or tools.

-   **Adversarial Robustness**: Development of detection models that remain effective even when attackers intentionally introduce perturbations or apply adversarial techniques to evade detection.

-   **Real-Time Detection Systems**: Creation of lightweight, edge-deployable forensic tools capable of performing authenticity verification on mobile devices and social media platforms in real-time.

-   **Blockchain and Cryptographic Authentication**: Integration of immutable provenance tracking and digital signatures at the content creation stage, complementing algorithmic detection with cryptographic verification.

-   **Explainable AI for Forensics**: Development of interpretable detection models that provide visual evidence maps and transparent reasoning, essential for legal admissibility and building trust in automated verification systems.

-   **Cross-Domain Generalization**: Research into detection models that maintain high performance across different datasets, compression levels, and unseen generative architectures, addressing the critical limitation of dataset-specific overfitting.

### 2.5 Related Research, Datasets, and Key Developments

The advancement of deepfake forensics has been significantly accelerated by collaborative research initiatives, standardized datasets, and open-source tools that enable reproducible evaluation and benchmarking.

**Major Research Contributions:**

Pioneering work by Rossler et al. (2019) with the FaceForensics++ dataset established standardized evaluation protocols for deepfake detection. This dataset, containing over 1,000 manipulated videos across four major synthesis methods, enabled fair comparison of detection algorithms and became the foundation for subsequent research.

Meta AI's DeepFake Detection Challenge (DFDC) in 2020 represented a quantum leap in scale and diversity, providing over 100,000 videos with varied demographics, lighting conditions, and environmental settings. The accompanying Kaggle competition attracted global participation, accelerating innovation in robust detection methods.

Research by Li and Lyu (2020) addressed quality limitations through the Celeb-DF dataset, featuring higher resolution videos with natural expressions and subtle manipulations that more closely approximate real-world deepfakes encountered on social media platforms.

**Emerging Dataset Paradigms:**

Recent initiatives recognize the importance of multimodal analysis. ForgeryNet (2021) integrated both video and audio manipulations across 2.9 million samples, enabling research into cross-modal inconsistency detection. The WildDeepfake dataset (2020) pioneered the collection of "in-the-wild" content from actual internet sources, providing realistic evaluation scenarios with compression artifacts and quality degradation typical of social media distribution.

**Technical Frameworks and Tools:**

The research community has developed several open-source frameworks for deepfake detection:

- **FaceForensics Benchmark**: Standardized evaluation pipeline with multiple compression levels
- **DFDC Framework**: Meta's open-source detection infrastructure
- **DeepFake-o-meter**: Web-based service for public deepfake analysis
- **Sensity AI Platform**: Commercial-grade detection API for enterprise applications

**Interdisciplinary Collaboration:**

Recent developments emphasize collaboration between computer vision researchers, cybersecurity experts, legal scholars, and policymakers. Initiatives such as the Content Authenticity Initiative (CAI) by Adobe and the Coalition for Content Provenance and Authenticity (C2PA) represent industry-wide efforts to establish technical standards for media authentication.

The European Union's Horizon 2020 Project and similar governmental initiatives demonstrate increasing recognition of deepfakes as national security concerns, funding research into forensic tools for law enforcement and intelligence agencies.

**Current Limitations and Research Gaps:**

Despite significant progress, the field faces persistent challenges:

- **Generalization Gap**: Models trained on specific datasets often fail on unseen manipulation techniques
- **Demographic Bias**: Most datasets focus on celebrities, lacking diversity in ethnicity, age, and gender
- **Adversarial Vulnerability**: Detection systems remain susceptible to intentional evasion techniques
- **Compression Artifacts**: Social media compression often removes forensic traces, reducing detection accuracy
- **Lack of Standardization**: Absence of universally accepted metrics for comparing detection performance

These limitations inform ongoing research directions and highlight the need for continued innovation in deepfake forensics methodologies.
