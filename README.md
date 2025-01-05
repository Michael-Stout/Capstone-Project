# Network Traffic Analysis for Botnet Detection
**Author:** Michael Stout

## Executive Summary
This project analyzes network traffic data to detect and classify botnet activities using machine learning techniques. The analysis processed over 107,000 network traffic records, identifying distinct patterns between normal and botnet traffic. The project successfully developed enhanced feature engineering techniques and visualization methods to improve botnet detection accuracy.

## Rationale
Modern cyber threats, particularly botnets and zero-day exploits, pose significant risks to network security. Traditional signature-based detection methods often fail to identify new or evolving threats. Machine learning approaches offer the potential for more adaptive and proactive defense mechanisms, crucial for protecting both individual users and organizations from emerging cyber threats.

## Research Question
How can machine learning techniques enhance the detection of zero-day exploits and botnet activities within network traffic? Specifically, what network traffic patterns and features are most indicative of botnet activity?

## Data Sources
This study utilized the CTU-13 Dataset, specifically Scenario 11, as part of a comprehensive botnet capture effort by the Czech Technical University (CTU) in Prague. The CTU-13 dataset is a labeled dataset of botnet, normal, and background traffic captured in 2011 from the CTU University network.

For this analysis, Scenario 11 contained:
- 107,251 total network traffic records
- 8,164 botnet traffic instances
- 2,718 normal traffic instances
- 96,369 background traffic instances

The dataset represents real botnet traffic mixed with normal traffic and background traffic. Scenario 11 specifically captured the behavior of the Rbot malware and included both benign and malicious traffic. Each row represents a network flow, summarizing communication between source and destination endpoints over a period. Rbot is a family of malware classified as a backdoor Trojan that provides attackers with remote control over infected machines.

Reference:
Sebastian Garcia, Martin Grill, Jan Stiborek and Alejandro Zunino. "An empirical comparison of botnet detection methods," Computers and Security Journal, Elsevier. 2014. Vol 45, pp 100-123.

Key data features include:
- Temporal information (StartTime, Duration)
- Network protocol information
- Source and destination addresses
- Traffic flow statistics (packets, bytes)
- Connection states

## Methodology
1. **Data Processing and Cleaning:**
   - Handled missing values in network traffic data
   - Processed 107,251 network traffic records
   - Created enhanced features including:
     - Duration categories
     - Bytes per packet ratios
     - Traffic flow metrics
     - Source and destination address entropy
     - Bytes/packets per second metrics

2. **Feature Engineering:**
   - Created categorical features for the duration (very_short, short, medium, long)
   - Developed byte-packet ratio analysis
   - Implemented traffic flow statistics
   - Generated entropy-based metrics for source and destination addresses

3. **Model Development:**
   - Implemented multiple classification algorithms:
     - Random Forest
     - Decision Tree
     - Naive Bayes
     - K-Nearest Neighbors (KNN)
     - Support Vector Machine (SVM)
     - Logistic Regression
     - Gradient Boosting
   - Used GridSearchCV for hyperparameter optimization
   - Implemented cross-validation for model validation

2. **Feature Engineering:**
   - Generated temporal features
   - Calculated entropy-based metrics
   - Created traffic flow statistics

3. **Analysis Techniques:**
   - Statistical analysis of traffic patterns
   - Time-series analysis of network flows
   - Advanced visualization techniques
   - Machine learning classification models

## Results
The analysis yielded comprehensive insights into botnet detection capabilities:

1. **Model Performance:**
   - KNN emerged as the top performer with:
     - Test Accuracy: 0.9991
     - Perfect ROC AUC: 1.0000
     - Lowest Log Loss: 0.0016
     - Perfect mAP score: 1.0000
   - All models achieved F1 scores > 0.999
   - Extremely high precision and recall across all models

2. **Feature Importance:**
   - BytePktRatio emerged as the most significant feature
   - SrcBytes and TotBytes showed high importance
   - Network entropy measures proved valuable for classification

3. **Traffic Distribution:**
   - Botnet traffic: 8,164 instances
   - Normal traffic: 2,718 instances
   - Clear distinctions in traffic patterns between botnet and normal flows

2. **Characteristic Patterns:**
   - Botnet packet sizes: 90.00-1066.00 bytes (mean: 1063.77)
   - Normal packet sizes: 60.00-1010.29 bytes (mean: 96.24)
   - Distinct duration patterns:
     - Botnet: 0.00-416.85 seconds
     - Normal: 0.00-969.98 seconds

3. **Network Behavior:**
   - Identified 3 unique botnet source IPs
   - Detected 9 unique botnet target IPs
   - Documented 8,155 unique botnet sockets

## Next Steps
1. **Model Deployment:**
   - Implement KNN model as the primary classifier and test in the datasets of the CTU-13
   - Develop an ensemble approach using top-performing models
   - Create a real-time classification pipeline

2. **Model Enhancement:**
   - Implement real-time detection capabilities
   - Develop adaptive learning mechanisms
   - Integrate additional network metrics

2. **Feature Development:**
   - Explore additional entropy-based features
   - Implement deep packet inspection features
   - Develop protocol-specific analysis

3. **Deployment Considerations:**
   - Design scalable implementation strategy
   - Develop monitoring and alerting systems
   - Create automated response mechanisms

*Note: Plots and logs are available in the project directory.*
