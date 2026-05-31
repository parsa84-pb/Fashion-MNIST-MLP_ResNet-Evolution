# 👕 Fashion-MNIST Evolution: From Deep MLPs to Ultimate Pre-Act ResNet + SE

<p align="center">
  <a href="#english-version">🌐 English Version</a> •
  <a href="#فارسی">🌍 نسخه فارسی</a>
</p>

---

<div id="english-version"></div>

## 🇬🇧 English Version

This repository showcases an architectural evolution on the **Fashion-MNIST** dataset. It documents the journey from optimizing traditional multi-layer perceptrons (MLPs) to engineering an elite, highly robust **Pre-Activation ResNet** combined with **Squeeze-and-Excitation (SE)** attention mechanisms, pushing the accuracy boundaries up to **95.20%**.

### 🚀 CRITICAL RUNTIME CONFIGURATION (READ BEFORE RUNNING)

> ⚠️ **IMPORTANT NOTE FOR EXECUTION**
> Inside the very first code block, there is a global control variable named `train`. 
>
> * **If `train = True`:** The entire training pipeline executes, generating loss/accuracy curves, and optimizing weights from scratch.
> * **If `train = False`:** The system **skips all training and validation learning blocks**, bypasses epoch visualizations, and directly deploys the evaluation engine. It will automatically load the pre-trained champion weights (`ultimate_fashion_mnist_checkpoint.pt`) from the root folder to run immediate test benchmarks, confusion matrices, and dynamic pruning stress tests.

### 📊 Dataset Insights
Before modeling, a strict exploratory data analysis was conducted to ensure class balance and structural clarity across the train/test splits.

<p align="center">
  <img src="images/image1.png" width="85%" alt="Fashion-MNIST Class Distribution Comparison">
</p>

#### Random Data Visualization
| Random Sample Images from Fashion-MNIST |
| :---: |
| ![](images/image2.png) |

### 📊 Architectural & Performance Benchmark
Below is the definitive experimental benchmark comparing both generations of neural architectures evaluated on 10,000 unseen test images:

| Architecture Generation | Model Name | Test Accuracy | Test Loss | Macro F1-Score | Training Dynamics |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **Gen 1: Baseline MLP** | Enhanced Lightweight MLP | `87.76%` | `0.3397` | `0.8779` | Early Stopped at Epoch 17 |
| **Gen 1: Baseline MLP** | Enhanced Pyramidal MLP | `89.30%` | `0.3037` | `0.8929` | Early Stopped at Epoch 22 |
| **Gen 2: Deep CNN (Ours)** | **Ultimate Pre-Act ResNet + SE** | **`95.20%`** | `0.4428` | **`0.9519`** | Fully Optimized (100 Epochs) |

### 📈 Training Dynamics & Optimization Trajectory
The charts below show the progressive learning behaviors, highlighting how Batch Normalization, Dropout, and Early Stopping rescued the Pyramidal and Lightweight MLPs from severe overfitting:

![](images/image3.png) ![](images/image4.png)

### 🛠️ Key Architectural Pillars of the Ultimate Model
1. **Pre-Activation Topology:** Shifts BatchNorm and ReLU prior to convolution layers, ensuring an unobstructed gradient highway across extreme depths.
2. **Squeeze-and-Excitation (SE) Attention:** Introduces channel-wise cross-examination, allowing the network to dynamically scale features based on critical item details.
3. **Stochastic Depth (DropPath):** Randomly deactivates residual blocks during training to enforce fierce regularization.
4. **Elite Optimization Regime:** Fueled by `AdamW`, scheduled via a smooth `Cosine Annealing LR`, and supervised using `Label Smoothing (0.05)`.

### 📋 Confusion Matrix & Error Analysis
The Ultimate ResNet heavily mitigates the historic *Shirt vs. T-shirt* confusion while locking absolute predictions on high-contrast structures:

#### Baseline Generation Error Profiles (MLPs)
![](images/image5.png)

#### Champion Generation Elite Profile (Ultimate ResNet)
<p align="center">
  <img src="images/image8.png" width="65%" alt="Ultimate Pre-Act ResNet Confusion Matrix">
</p>

### 🧠 Stress-Testing & Network Pruning Robustness
We subjected the networks to a dynamic pruning stress test by computing the Pearson Correlation Matrix across the final hidden representations and zeroing out the weights of highly redundant channels/neurons.

#### 1. Feature Representation Alignment (Correlation Matrices)

<p align="center">
  <img src="images/image6.png" width="60%" alt="MLP Hidden Layer Correlation">
  <br>
  <em>Figure 1: High multi-collinearity and parameter redundancy observed within the hidden representations of the baseline MLP model.</em>
</p>

<p align="center">
  <img src="images/image9.jpg" width="60%" alt="Ultimate ResNet Feature Correlation">
  <br>
  <em>Figure 2: Highly decoupled, orthogonal, and sparse latent feature channels enforced by the Ultimate Pre-Act ResNet + SE blocks.</em>
</p>

#### 2. Network Breakdown Curves (Pruning Sensitivity)
* **Pyramidal MLP (64 Neurons):** Extremely fragile. Pruning 31.2% of its capacity led to severe decay, and hitting 78.1% caused a **Catastrophic Breakdown** (`images/image7.png`).
* **Ultimate ResNet (512 Channels):** Demonstrates flawless decentralized intelligence. Removing up to **100 feature channels (19.5% of the entire layer) resulted in 0.00% accuracy drops**, holding firmly at 95.14% (`images/image10.png`).

<p align="center">
  <img src="images/image7.png" width="60%" alt="MLP Pruning Breakdown Curve">
  <br>
  <em>Figure 3: Severe performance collapse curve of the MLP network under random neuron elimination.</em>
</p>

<p align="center">
  <img src="images/image10.png" width="60%" alt="Ultimate ResNet Pruning Breakdown Curve">
  <br>
  <em>Figure 4: Exceptional, rock-solid structural robustness of the Pre-Act ResNet model under aggressive feature channel pruning.</em>
</p>

---

<div id="فارسی"></div>

## 🌍 نسخه فارسی

این مخزن یک تحول معماری را بر روی مجموعه داده **Fashion-MNIST** به نمایش می‌گذارد. فرآیند توسعه از بهینه‌سازی شبکه‌های پرسپترون چندلایه سنتی (MLP) آغاز شده و به طراحی یک مدل نخبه و بسیار مستحکم **Pre-Activation ResNet** همراه با مکانیزم توجه **Squeeze-and-Excitation (SE)** منتهی شده است که دقت تست را به مرز **۹۵.۲۰٪** می‌رساند.

### 🚀 تنظیمات حیاتی زمان اجرا (قبل از اجرا بخوانید)

> ⚠️ **نکته بسیار مهم برای اجرای کد**
> در اولین بلوک کد، یک متغیر کنترل سراسری به نام `train` تعریف شده است:
>
> * **در صورت `train = True`:** کل فرآیند آموزش از ابتدا اجرا شده، نمودارهای لوس و دقت تولید می‌شوند و وزن‌ها بهینه‌سازی خواهند شد.
> * **در صورت `train = False`:** سیستم **تمامی بلوک‌های یادگیری و آموزش را نادیده می‌گیرد**، از تصویرسازی اپاک‌ها عبور کرده و مستقیماً موتور ارزیابی را فعال می‌کند. سیستم به طور خودکار وزن‌های از پیش آموزش‌دیده قهرمان (`ultimate_fashion_mnist_checkpoint.pt`) را از پوشه اصلی لود می‌کند تا تست بفرمارک، ماتریس تداخل و تست استرس هرس پویا را فوراً اجرا کند.

### 📊 تحلیل اولیه مجموعه داده‌ها
پیش از مدل‌سازی، یک ارزیابی آماری دقیق روی داده‌ها انجام شد تا از تعادل کلاس‌ها و شفافیت ساختاری میان داده‌های آموزش و تست اطمینان حاصل شود.

<p align="center">
  <img src="images/image1.png" width="85%" alt="بررسی توزیع کلاس‌های دیتاست">
</p>

#### تصویرسازی تصادفی داده‌ها
| نمونه تصاویر تصادفی فشن ام‌نیست |
| :---: |
| ![](images/image2.png) |

### 📊 جدول مقایسه عملکرد و بنچمارک معماری‌ها
جدول زیر بنچمارک تجربی و نهایی عملکرد دو نسل از معماری‌های عصبی را روی ۱۰,۰۰۰ تصویر تست دیده نشده نشان می‌دهد:

| نسل معماری | نام مدل | دقت تست (Accuracy) | میزان لوس تست | شاخص Macro F1 | دینامیک آموزش |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **نسل ۱: مدل مبنا** | Enhanced Lightweight MLP | `87.76%` | `0.3397` | `0.8779` | توقف زودرس در اپاک ۱۷ |
| **نسل ۱: مدل مبنا** | Enhanced Pyramidal MLP | `89.30%` | `0.3037` | `0.8
