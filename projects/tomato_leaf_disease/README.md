🍅 Tomato Leaf Disease Classification & Model Compression
📌 Project Overview

This project focuses on developing and optimizing deep learning models for tomato leaf disease classification, with the goal of deploying lightweight models on resource-constrained devices.

Three Convolutional Neural Network (CNN) architectures were trained and evaluated for recognizing tomato leaf diseases:

AlexNet
MobileNet
DenseNet

After training the models, several model compression techniques were applied to reduce their size and computational requirements while maintaining as much classification performance as possible.

The optimization process includes:

Pruning
Weight clustering
Quantization

The project explores the trade-off between model size, computational efficiency, and classification performance, which is particularly relevant for TinyML and edge AI applications in precision agriculture.

🎯 Project Objectives

The main objectives of the project are to:

Develop CNN-based models for tomato leaf disease recognition.
Compare the performance of different CNN architectures.
Reduce the size of trained models through compression techniques.
Investigate the impact of compression on classification performance.
Produce models suitable for deployment on resource-constrained devices.
Explore the application of TinyML to agricultural disease detection.
🌱 Disease Classification

The models are trained to distinguish between different tomato leaf conditions, including:

Healthy leaves
Bacterial Spot
Early Blight
Other disease classes included in the dataset

The classification pipeline processes tomato leaf images and predicts the corresponding disease category.

🧠 Deep Learning Models

Three CNN architectures are investigated:

AlexNet

AlexNet serves as a baseline CNN architecture for evaluating image classification performance and the effect of subsequent compression techniques.

MobileNet

MobileNet is designed specifically for computationally constrained environments and provides a lightweight architecture suitable for edge and mobile applications.

DenseNet

DenseNet uses dense connections between layers to improve feature propagation and parameter efficiency while maintaining strong image classification capabilities.

⚙️ Model Optimization

After training the models, different compression techniques are applied to reduce model size.

1. Pruning

Pruning removes less important weights from the neural network.

Original Model
      ↓
Identify Less Important Weights
      ↓
Remove / Zero Weights
      ↓
Pruned Model