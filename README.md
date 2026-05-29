
# CIC-NLP at MAHED 2025 TASK 1: Assessing the Role of Bigram Augmentation in Multiclass Arabic Hate and Hope Speech Classification

This repository contains the official codebase and experimental framework developed by the **CIC-NLP** team for **Task 1 of the MAHED 2025 Shared Task**.

This research investigates the performance boundaries of text-level data augmentation strategies when applied to the joint, multi-class classification of **hate speech**, **hope speech**, and **neutral content** in Arabic social media discourse.

---

##  Abstract

This study investigates the impact of bigram-based data augmentation on the joint classification of hate speech, hope speech, and neutral content in multilingual social media contexts, with a particular focus on Arabic. While previous research has shown the benefits of augmentation in text classification, its effectiveness in nuanced domains such as hate and hope speech remains underexplored.

Using the annotated MAHED dataset, we compare three scenarios:

1. **Baseline:** No data augmentation.
2. **Global Bigram Augmentation:** Standard bigram injection applied uniformly across the entire training pool.
3. **Classwise Bigram Augmentation:** Target-specific bigram manipulation tailored to individual class constraints.

The baseline achieved $68.25\%$ accuracy (macro-F1 = $0.6729$) on the test set. Global bigram augmentation slightly reduced accuracy to $63.0\%$ (macro-F1 = $0.62$), showing no improvement over the baseline. Classwise augmentation achieved $93\%$ accuracy on the validation set but dropped sharply to $59.65\%$ accuracy (macro-F1 = $0.4726$) on the test set, indicating severe overfitting. These results suggest that bigram-based methods are sensitive to class imbalance and may harm generalisation when applied unevenly across classes. We conclude by highlighting the need for more balanced, context-aware augmentation strategies in socially impactful NLP tasks.

---

##  Experimental Scenarios & Results

The codebase is split into three core experimental tracks designed to evaluate data-skew and generalization thresholds:

| Experimental Track | Validation Accuracy | Test Accuracy | Test Macro-F1 | Finding / Outcome |
| --- | --- | --- | --- | --- |
| **1. Unaugmented Baseline** | — | **68.25%** | **0.6729** | **Top Performer.** Highest out-of-domain generalizability. |
| **2. Global Bigram Augmentation** | — | 63.00% | 0.6200 | Degradation. Introduced semantic noise uniformly. |
| **3. Classwise Bigram Augmentation** | **93.00%** | 59.65% | 0.4726 | **Severe Overfitting.** Memorized validation splits, failed on test. |

> ⚠️ **Key Takeaway:** Naive n-gram or bigram-level synthetic injections fail to capture the subtle semantic and cultural nuances inherent in Arabic hope and hate speech. Classwise variations compound dataset imbalances, leading models to overfit localized validation patterns.

---

##  Getting Started

### Prerequisites

* Python 3.9+
* Scikit-Learn / PyTorch
* NLTK / AraNLP (for Arabic tokenization and text processing)
* Pandas, NumPy

### Installation

```bash
git clone https://github.com/YOUR_GITHUB_USERNAME/REPO_NAME.git
cd REPO_NAME
pip install -r requirements.txt

```

### Usage

1. **Preprocess Arabic Text & Tokenization:**
```bash
python src/preprocess.py --dataset mahed_2025

```



```
2. **Train the Unaugmented Baseline Pipeline:**
   ```bash
   python src/train.py --strategy baseline

```

3. **Train with Global Bigram Augmentation:**
```bash
python src/train.py --strategy global_bigram

```



```
4. **Train with Classwise Bigram Augmentation (Demonstrates Overfitting):**
   ```bash
   python src/train.py --strategy classwise_bigram

```

---

##  Citation

If you use this benchmarking framework or reference the CIC-NLP experimental findings on Arabic text augmentation, please cite our MAHED 2025 paper:

```bibtex
@inproceedings{faniyi2025cic,
  title={CIC-NLP at MAHED 2025 TASK 1: Assessing the Role of Bigram Augmentation in Multiclass Arabic Hate and Hope Speech Classification},
  author={Your Name and Sidorov, Grigori and Calvo, Hiram},
  booktitle={Proceedings of the MAHED 2025 Shared Task Workshop},
  year={2025}
}

```

---
