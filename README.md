# 🚗 ADAS Oriented Lane and Vehicle Detection Pipeline

This project implements a deep learning-based lane detection pipeline for Advanced Driver Assistance Systems (ADAS). It uses Convolutional Neural Networks (CNNs) to automatically identify lane markings from road video streams and overlay them onto the original footage.

---

## 📌 Overview

The system is designed as an end-to-end pipeline that handles model development, training, and inference for lane detection tasks.

At its core, the project uses a CNN-based architecture (inspired by LaneNet) built with PyTorch. The model processes video frames and performs pixel-wise segmentation to identify lane regions under varying road and lighting conditions.

The workflow consists of:

- A **training pipeline** that loads and preprocesses image data, then optimizes the neural network  
- A **detection module** that applies the trained model to video input  
- Supporting **utility functions** for preprocessing, visualization, and refinement  

---

## 🎥 Demo

The system processes road videos frame-by-frame and generates an output video with detected lane markings overlaid, demonstrating its effectiveness in real-world driving scenarios.

---

## ⚙️ Requirements

Ensure the following dependencies are installed:

- Python 3.x  
- PyTorch  
- OpenCV  
- MoviePy  
- Scikit-learn  
- NumPy  

Install all dependencies using:

```bash
pip install -r requirements.txt

## 🧠 How It Works

The model is designed to perform lane detection using a fully convolutional neural network for pixel-level prediction.

### 🔹 Input

The system processes individual frames extracted from road videos. These frames may contain variations in lighting conditions, road structure, and lane visibility.

---

### 🔹 Model Architecture

The neural network follows a fully convolutional design, enabling it to learn spatial features directly from input images:

- **Convolutional layers** extract key visual features such as edges, textures, and lane patterns  
- **Pooling layers** reduce spatial dimensions while retaining important information  
- **Feature refinement layers** help capture lane structures at multiple scales  
- **Prediction layers** generate segmentation maps identifying lane regions  
- The **final output layer** produces a lane mask highlighting detected lane areas  

---

### 🔹 Training Strategy

The model is trained using labeled datasets where each input image is paired with a corresponding lane mask. This allows the network to learn pixel-wise classification of lane versus non-lane regions.

---

### 🔹 Loss Function

A cross-entropy loss function is used to measure the difference between predicted lane masks and ground truth labels. The optimizer updates model parameters to minimize this loss during training.

---

### 🔹 Post-Processing

To improve the quality of predictions, several refinement steps are applied:

- Noise reduction to eliminate false detections  
- Lane smoothing for stable visualization  
- Curve fitting to generate continuous lane boundaries  

---

## 🏋️ Training Process

### 🔹 Dataset

Training requires a dataset of road images with annotated lane markings. Each image must have a corresponding ground truth segmentation mask.

---

### 🔹 Steps

1. Prepare and preprocess the dataset  
2. Train the model using `train.py`  
3. Monitor performance using metrics such as accuracy and Intersection over Union (IoU)  
4. Save trained weights (`model.pth`) for inference  

---

## ▶️ Usage

### 🔹 Train the Model

```bash
python train.py
