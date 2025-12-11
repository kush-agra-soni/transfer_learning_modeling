# 🌸 Transfer Learning on Oxford Flowers 102

### *Deep Learning Meets Gardening*

Welcome to **Transfer Learning on Oxford Flowers 102**, where neural networks learn to tell a *Sunflower* from a *Snowdrop*—even when you can’t. This project uses three popular pre-trained CNN architectures—**ResNet50**, **VGG16**, and **MobileNetV2**—to tackle the beautifully challenging **Oxford Flowers 102** dataset.

Think of it as teaching world-class ImageNet models to become refined botanists. Some do great… others forget their roots.

---

## 🌼 Project Overview

This project demonstrates how **transfer learning** can be used to train powerful image classifiers with limited data. Using TensorFlow and TensorFlow Datasets, we:

* Load and preprocess the *Oxford Flowers 102* dataset
* Plug images into three different pre-trained models
* Fine-tune each model for flower classification
* Evaluate performance and compare architectures
* Plot training curves and draw meaningful insights

Whether you’re into deep learning, flowers, or both, there's something blooming here for you.

---

## 📂 Dataset: Oxford Flowers 102

The **Oxford Flowers 102** dataset is a fine-grained image classification dataset featuring:

* **102 flower classes**
* Highly variable poses, lighting, scales, and backgrounds
* Pre-defined splits:

  * **Train:** 1020 images
  * **Validation:** 1020 images
  * **Test:** 6149 images

Every flower is prettier than the last, but the models don’t get distracted (usually).

---

## 🧪 Models Used

### 🔵 ResNet50

A very deep model with residual connections. Brilliant on CIFAR and ImageNet… surprisingly confused by flowers here.

### 🟣 VGG16

A classic architecture with stacked convolutional layers. Turns out VGG is the true flower enthusiast—best accuracy in this project.

### 🟢 MobileNetV2

Lightweight and mobile-friendly. Fast, efficient, and unexpectedly baffled by petals.

---

## 🔧 Workflow Summary

### 1️⃣ Data Loading & Preprocessing

* Using `tfds.load()`
* Resize images → **224 × 224**
* Apply model-specific preprocessing
* One-hot encode labels
* Batch + prefetch for GPU efficiency

### 2️⃣ Model Preparation

Each model is loaded **without the top layer**, then extended using:

* `GlobalAveragePooling2D`
* Dense layer(s)
* Dropout
* 102-class softmax output

Base layers are initially **frozen** to preserve ImageNet wisdom.

### 3️⃣ Fine-Tuning

We partially unfreeze the top layers of each model:

* ResNet50 → last 30 layers
* VGG16 → last 5 layers
* MobileNetV2 → last 40 layers

Then train for **3 epochs** (demo purpose, adjust as needed).

### 4️⃣ Evaluation

---

## 📊 Results

| Model           | Accuracy  | Notes                                   |
| --------------- | --------- | --------------------------------------- |
| **VGG16**       | ⭐ **48%** | Clear winner—VGG really loves flowers   |
| **ResNet50**    | 12%       | Shockingly low—still lost in the garden |
| **MobileNetV2** | 10%       | Lightweight, but not a botanist         |

**Key takeaway:** sometimes the “simplest” model is the best fit for fine-grained classification.

---

## 💡 Insights & Discussion

* **Transfer learning works**, even with small datasets—but model choice matters a lot.
* **VGG16 consistently outperforms** deeper or more efficient models here, likely due to its feature extraction style.
* Fine-grained classification can be tricky—flower species vary subtly.
* Preprocessing and careful unfreezing of layers can significantly impact results.

Optional improvements:

* Data augmentation
* More fine-tuning
* Learning rate schedules
* Confusion matrix analysis
* Trying EfficientNet or ViT models

---

## 📁 Repository Structure (suggested)

```
📦 flower-transfer-learning
 ├── data/                 # tfds-managed dataset
 ├── models/               # saved models
 ├── plots/                # accuracy & loss graphs
 ├── train.py              # training loop
 ├── evaluate.py           # evaluation script
 ├── README.md             # you're reading it!
 └── requirements.txt
```

---

## 🚀 Getting Started

### Install dependencies

```bash
pip install tensorflow tensorflow-datasets matplotlib
```

### Run training

```bash
python train.py
```

### Evaluate models

```bash
python evaluate.py
```

---

## 🌺 Final Thoughts

This project shows how transfer learning transforms powerful general-purpose CNNs into flower specialists. While some architectures flourished, others... wilted. But every experiment helps us grow (pun proudly intended).

If you like deep learning, botany, or models that struggle to distinguish roses from rhododendrons, you’ll enjoy exploring this codebase.

Happy training—and may your validation accuracy blossom! 🌷
