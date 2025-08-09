# Automated-Detection-System-on-DDos-Attacks
Closed-loop Automated Detection System on Distributed Denial of Service (DDoS) Attacks via Machine Learning and Deep Learning Models


# DDoS Detection via Machine Learning

This repository contains the materials for **RP3: Closed-loop DDoS Detection via Machine Learning**.

## Project Overview
This project designs and implements a closed-loop detection system for Distributed Denial-of-Service (DDoS) attacks, integrating traffic generation, real-time monitoring, and machine learning-based classification. The goal is to simulate realistic attack scenarios, capture and process network data, and train models capable of accurately distinguishing between benign and malicious traffic patterns. The system is built to operate in an iterative loop, where detection results can be fed back to dynamically adjust monitoring strategies.

## Implementation
The system is composed of the following key stages:

1. **Traffic Simulation**  
   - Multiple Docker-based containers emulate various DDoS attack types (e.g., SYN flood, UDP flood, HTTP-based attacks) alongside normal traffic.  
   - Attacks are launched in controlled time windows to facilitate precise labeling.

2. **Data Capture and Processing**  
   - Network traffic is captured in `.pcap` format.  
   - A Python-based pipeline parses pcap files, segments flows, and labels each record according to the active attack phase.  
   - Extracted flow-level features include statistical metrics (e.g., packet counts, byte rates, inter-arrival times) and entropy-based measures.

3. **Feature Engineering**  
   - Direction-aware aggregation to differentiate inbound/outbound flow characteristics.  
   - Calculation of temporal and statistical indicators to improve model sensitivity to short-lived attacks.  

4. **Machine Learning Pipeline**  
   - Models such as Random Forest and Gradient Boosting are trained on the engineered features.  
   - Evaluation metrics (precision, recall, F1-score) are used to assess detection accuracy under various attack intensities.  

5. **Closed-loop Feedback**  
   - Detection outcomes can trigger adaptive monitoring, e.g., adjusting capture filters or allocating more resources to suspected attack flows.

## Contents
- `RP3_DDoS_ML_Detection.pdf`: Detailed project report covering design, methodology, experiments, and results.
- `project.zip`: Full source code, configuration files, and example datasets for reproduction.
