# Leveraging Code-Mixed Product Metadata and User Feedback for Personalized Recommendation on Daraz Bangladesh

[![Paper](https://img.shields.io/badge/arXiv-2606.16387-b31b1b.svg)](https://arxiv.org/abs/2606.16387)

**Paper:** https://arxiv.org/abs/2606.16387
**Authors:** KM Fahim A Bari, Muhammad Abdullah Adnan, Nafis Sadeq

---

## Overview

This repository contains the code, notebooks, and experimental results accompanying our paper:

> **Leveraging Code-Mixed Product Metadata and User Feedback for Personalized Recommendation on Daraz Bangladesh**

We present a comprehensive benchmark of recommendation algorithms on **Daraz Bangladesh**, the largest e-commerce platform in Bangladesh. The benchmark evaluates multiple recommendation paradigms under a realistic **per-user chronological leave-last-out evaluation protocol**, reflecting real-world recommendation scenarios.

### Key Contributions

* Benchmarking across **six recommendation model families**
* Evaluation on a large-scale Bangladeshi e-commerce review dataset
* Analysis of **Bangla-English code-mixed product metadata**
* Investigation of recommendation performance under varying sparsity levels
* Language-stratified evaluation for content-based recommendation

---

## Dataset

Experiments are conducted on the **BanglishRev** dataset:

**Hugging Face:**
https://huggingface.co/datasets/BanglishRev/bangla-english-and-code-mixed-ecommerce-review-dataset

### Dataset Setup

Download the dataset and place it in:

```text
data/BanglishRev.json.gz
```

Directory structure:

```text
project_root/
│
├── data/
│   ├── BanglishRev.json.gz
│
├── notebooks/
├── results/
└── ...
```

---

## Installation

Clone the repository and install dependencies:

```bash
pip install -r requirements.txt
```

---

## Reproducing the Benchmark

Run the notebooks in the following order.

| Notebook                           | Description                                                                  |
| ---------------------------------- | ---------------------------------------------------------------------------- |
| `01_eda.ipynb`                     | Dataset statistics, exploratory analysis, and language distribution analysis |
| `02_collaborative_filtering.ipynb` | Global Popularity, Category Popularity, UserCF, and ItemCF                   |
| `03_matrix_factorization.ipynb`    | Explicit Matrix Factorization (SVD) and Implicit Matrix Factorization (ALS)  |
| `04_content_based_filtering.ipynb` | TF-IDF based Content-Based Filtering and language-stratified evaluation      |

---

## Sparsity Ablation Study

To reproduce the sparsity analysis, modify the following configuration variables in each notebook:

```python
MIN_USER_INTERACTIONS
MIN_ITEM_INTERACTIONS
```

The following k-core filtering configurations are evaluated:

| Min User Interactions | Min Item Interactions |
| --------------------- | --------------------- |
| 5                     | 3                     |
| 10                    | 3                     |
| 15                    | 3                     |
| 15                    | 5                     |
| 20                    | 5                     |

---

## Evaluation Protocol

All recommendation models are evaluated using a **per-user chronological leave-last-out split**:

* Interactions are ordered by timestamp.
* The most recent interaction of each user is reserved for testing.
* Remaining interactions are used for training.
* Performance is reported using ranking-based recommendation metrics.

This protocol better reflects real-world deployment compared to random train-test splits.

---

## Pre-Computed Results

All experiment outputs, evaluation logs, and benchmark tables are available in:

```text
results/
```

The primary benchmark configuration reported in the paper uses:

```text
(Min User Interactions, Min Item Interactions) = (10, 3)
```

---

## Citation

If you use this repository, dataset, or benchmark results in your research, please cite:

```bibtex
@misc{bari2026leveragingcodemixedproductmetadata,
      title={Leveraging Code-Mixed Product Metadata and User Feedback for Personalized Recommendation on Daraz Bangladesh}, 
      author={KM Fahim A Bari and Muhammad Abdullah Adnan and Nafis Sadeq},
      year={2026},
      eprint={2606.16387},
      archivePrefix={arXiv},
      primaryClass={cs.IR},
      url={https://arxiv.org/abs/2606.16387}, 
}
```
