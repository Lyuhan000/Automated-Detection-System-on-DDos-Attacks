# Automated-Detection-System-on-DDos-Attacks
Closed-loop Automated Detection System on Distributed Denial of Service (DDoS) Attacks via Machine Learning and Deep Learning Models


## Project Overview
The project addresses the growing challenge of detecting DDoS attacks in real-time, where high traffic volumes and evolving attack strategies demand robust and adaptive solutions. A closed-loop architecture is adopted, enabling the detection system not only to classify ongoing traffic but also to feed detection outcomes back into the monitoring process, allowing dynamic adjustment of capture parameters and resource allocation. The research explores the interplay between traffic generation, data preprocessing, and model training, with an emphasis on replicating realistic attack conditions and ensuring reproducibility of results.

## Implementation
The implementation begins with a traffic generation environment built on Docker, in which multiple containers are orchestrated to produce both benign network activity and a diverse range of DDoS attacks, including SYN floods, UDP floods, and HTTP-based attacks. These scenarios are executed in precisely defined time intervals to facilitate accurate ground-truth labeling.

Captured traffic is stored in `.pcap` format and processed through a custom Python pipeline. This pipeline parses raw packets into bidirectional flows, applies direction-aware aggregation, and computes a comprehensive set of statistical and temporal features. These include packet and byte counts, inter-arrival time distributions, throughput metrics, and entropy-based indicators designed to capture irregularities in traffic patterns. Attack labels are dynamically assigned based on synchronized attack schedules, ensuring precise correspondence between traffic segments and their classification.

The processed datasets are used to train and evaluate multiple supervised learning models, such as Random Forests and Gradient Boosting Machines. Model performance is rigorously assessed using precision, recall, and F1-score, with particular attention paid to the impact of attack type, intensity, and feature selection on detection accuracy. Benchmarking experiments are conducted under varying load conditions to evaluate scalability and latency in detection.

The closed-loop element of the system is realised by integrating the classification outputs into the traffic monitoring logic. In practice, this allows the system to adjust flow capture granularity, prioritise suspected malicious streams, and simulate potential defensive measures. This approach demonstrates the feasibility of a responsive detection pipeline capable of adapting to changing attack behaviours in near real-time.

## Significance and Potential Extensions
This work demonstrates a practical pathway for bridging the gap between static, offline detection models and dynamic, real-world network security operations. By simulating realistic attack traffic and embedding detection within a feedback-driven monitoring cycle, the system moves closer to operational deployment scenarios where automated mitigation is required.

Potential extensions of this work include:
- Integrating **real-time alerting and automated mitigation** by linking detection outputs to network firewalls or SDN controllers.
- Expanding the attack dataset to cover **low-rate and stealthy DDoS variants**, which are more challenging to detect.
- Incorporating **online learning techniques** to allow the model to adapt to novel attack patterns without full retraining.
- Deploying the system in a **distributed monitoring architecture**, enabling collaborative detection across multiple network vantage points.

Such improvements would further enhance the system’s robustness and scalability, making it applicable to high-traffic, mission-critical network environments.
