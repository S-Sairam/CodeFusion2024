# BotnetDetector - UDP-based DDoS Detection Using LSTMs

This project was developed for the Codefusion Hackathon. The **BotnetDetector** is designed to detect UDP-based DDoS attacks by leveraging Long Short-Term Memory (LSTM) networks. By analyzing network traffic, this model provides real-time botnet detection to identify and mitigate potential threats.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Dataset](#dataset)
- [Model Architecture](#model-architecture)
- [Results](#results)
- [Future Work](#future-work)
- [Acknowledgments](#acknowledgments)

## Overview
The BotnetDetector focuses on detecting Distributed Denial-of-Service (DDoS) attacks targeting the UDP protocol, a common vector for volumetric attacks. Using LSTM networks allows the model to capture temporal patterns in the traffic flow, which is crucial for accurately distinguishing between benign and malicious activities.

## Features
- **Focus on UDP Traffic**: Specialized in detecting UDP-based DDoS attacks.
- **LSTM Model for Temporal Analysis**: Employs LSTM to capture patterns over time, improving detection accuracy for botnet activities.
- **Easy to Expand**: A good base architecture to expand to other types of attacks

## Dataset
This project utilizes the [CIC 2019 DDoS Dataset](https://www.unb.ca/cic/datasets/ddos-2019.html), which includes extensive samples of DDoS attack traffic .

## Model Architecture
The BotnetDetector uses a type of artificial intelligence model called a **Long Short-Term Memory (LSTM)** network. This type of model is particularly effective for processing sequences of data, such as network traffic, because it can remember information over time and use it to make predictions. Below is a breakdown of the layers and their purpose:

1. **First Layer - LSTM**:
   - This layer contains 64 units, or "neurons," each of which learns patterns in the data over time.
   - We use the **ReLU** (Rectified Linear Unit) activation function here, which helps the model learn complex relationships by allowing it to "activate" neurons only when needed.
   - It also has `return_sequences=True`, meaning it outputs the entire sequence of learned information, which is useful for the following layers.
   - **Batch Normalization**: This is like giving the model a "refresh" by adjusting and scaling the output from this layer, which helps it learn faster and stay stable.
   - **Dropout (20%)**: A Dropout layer is a technique that temporarily "turns off" 20% of neurons in this layer while training. This helps prevent overfitting (where the model remembers the training data too well and struggles with new data).

2. **Second Layer - LSTM**:
   - This layer has 128 units, allowing it to capture even more detailed patterns from the sequence of data.
   - Again, **ReLU** is used for activation, and `return_sequences=True` allows it to output the full sequence, continuing to pass information to the next layer.
   - **Batch Normalization**: Like before, this normalizes the data to ensure smooth learning.
   - **Dropout (30%)**: Here, 30% of neurons are "turned off" temporarily, further improving generalization and reducing overfitting.

3. **Third Layer - LSTM**:
   - This layer uses 64 units and **ReLU** activation, but this time it only outputs the last piece of information in the sequence (with `return_sequences=False`), which contains the model's learned understanding of the data sequence.
   - **Batch Normalization**: Ensures stability in this final LSTM layer.
   - **Dropout (20%)**: The 20% dropout helps keep the model from overfitting on the training data.

4. **Fully Connected Layers**:
   - **Dense Layer (64 units)**: This layer is a more traditional type of neural network layer. It has 64 units and also uses the **ReLU** activation function to transform the output from the previous layers into more meaningful information.
   - **Output Dense Layer (1 unit)**: This final layer has a single unit that provides the model's prediction. Since our goal is to detect botnet activity, this layer outputs a single value that represents the likelihood of malicious activity.

### Why This Model Works for DDoS Detection
The LSTM layers are essential because they allow the model to remember previous parts of the network traffic sequence, helping it distinguish between regular traffic and the kinds of patterns you might see in a DDoS attack. The additional normalization and dropout layers make sure the model learns effectively without becoming too specialized to the training data.

This architecture is particularly suited to detecting DDoS attacks over the UDP protocol, as these attacks often follow specific patterns over time that the LSTM layers can recognize.


## Results
The BotnetDetector achieved the following results on the test set:
- **Accuracy**: 0.99957 OR 99.57%
- **Precision**: 0.9998 OR 99.98%
- **Recall**: 0.99976 OR 99.97%
  
These results demonstrate the model's effectiveness in detecting UDP-based DDoS attacks.

## Future Work
- Expand support to other DDoS attack vectors (e.g., TCP, ICMP, DNS).
- Optimize model for faster real-time processing.
- Improve accuracy and reduce false positives by incorporating other ML techniques.

## Acknowledgments
Thanks to the Codefusion Hackathon organizers and the University of New Brunswick for providing the CIC 2019 DDoS Dataset.

Thank you to my teammates for contributing and making this model work :
                                                                         [Krishna Sujit](https://www.github.com/haxthehacc),
                                                                         [Manit Bohra](https://www.github.com/Alex-Hunterz), 
                                                                          [Atharv](https://www.github.com/atharvrawal)   
