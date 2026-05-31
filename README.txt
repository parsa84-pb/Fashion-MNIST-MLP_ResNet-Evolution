# 👕 Fashion-MNIST Evolution: From Deep MLPs to Ultimate Pre-Act ResNet + SE

This repository showcases an architectural evolution on the **Fashion-MNIST** dataset. It documents the journey from optimizing traditional multi-layer perceptrons (MLPs) to engineering an elite, highly robust **Pre-Activation ResNet** combined with **Squeeze-and-Excitation (SE)** attention mechanisms, pushing the accuracy boundaries up to **95.20%**.

---

## 🚀 CRITICAL RUNTIME CONFIGURATION (READ BEFORE RUNNING)

> ⚠️ **IMPORTANT NOTE FOR EXECUTION**
> Inside the very first code block, there is a global control variable named `train`. 
>
> * **If `train = True`:** The entire training pipeline executes, generating loss/accuracy curves, and optimizing weights from scratch.
> * **If `train = False`:** The system **skips all training and validation learning blocks**, bypasses epoch visualizations, and directly deploys the evaluation engine. It will automatically load the pre-trained champion weights (`ultimate_fashion_mnist_checkpoint.pt`) from the root folder to run immediate test benchmarks, confusion matrices, and dynamic pruning stress tests.

---

## 📊 Dataset Insights

Before modeling, a strict exploratory data analysis was conducted to ensure class balance and structural clarity across the train/test splits.

<p align="center">
  <img src="images/image1.png" width="90%" alt="Fashion-MNIST Class Distribution Comparison">
</p>

### Random Data Visualization
Below are random visual samples directly fetched from the dataset pipelines, displaying the various fashion categories with their respective index tags:
<p align="center">
  <img src="images/image2.png" width="90%" alt="Random Sample Images from Fashion-MNIST">
</p>

---

## 📊 Architectural & Performance Benchmark

Below is the definitive experimental benchmark comparing both generations of neural architectures evaluated on 10,000 unseen test images:

| Architecture Generation | Model Name | Test Accuracy | Test Loss | Macro F1-Score | Training Dynamics |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **Gen 1: Baseline MLP** | Enhanced Lightweight MLP | `87.76%` | `0.3397` | `0.8779` | Early Stopped at Epoch 17 |
| **Gen 1: Baseline MLP** | Enhanced Pyramidal MLP | `89.30%` | `0.3037` | `0.8929` | Early Stopped at Epoch 22 |
| **Gen 2: Deep CNN (Ours)** | **Ultimate Pre-Act ResNet + SE** | **`95.20%`** | `0.4428` | **`0.9519`** | Fully Optimized (100 Epochs) |

---

## 📈 Training Dynamics & Optimization Trajectory

### 1. Baseline MLP Multi-Stage Evolution
The charts below show the progressive learning behaviors, highlighting how Batch Normalization, Dropout, and Early Stopping rescued the Pyramidal and Lightweight MLPs from severe overfitting:

<p align="center">
  <img src="images/image3.png" width="49%" alt="Loss Convergence Comparison">
  <img src="images/image4.png" width="49%" alt="Validation Generalization Benchmark">
</p>

---

## 🛠️ Key Architectural Pillars of the Ultimate Model

The champion model bypasses the classic MLP limitations by integrating four state-of-the-art deep learning paradigms:
1. **Pre-Activation Topology:** Shifts BatchNorm and ReLU prior to convolution layers, ensuring an unobstructed gradient highway across extreme depths.
2. **Squeeze-and-Excitation (SE) Attention:** Introduces channel-wise cross-examination, allowing the network to dynamically scale features based on critical item details (e.g., collars, sleeve borders).
3. **Stochastic Depth (DropPath):** Randomly deactivates residual blocks during training to enforce fierce regularization and prevent over-parameterization.
4. **Elite Optimization Regime:** Fueled by `AdamW`, scheduled via a smooth `Cosine Annealing LR`, and supervised using `Label Smoothing (0.05)`.

---

## 📋 Confusion Matrix & Error Analysis

The