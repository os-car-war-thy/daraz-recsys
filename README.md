# Leveraging Code-Mixed Product Metadata and User Feedback 
# for Personalized Recommendation on Daraz Bangladesh

**Paper:** [link to paper once published]  
**Authors:** [Your names]

## Overview
This repository contains the notebooks and results for our 
Top-N recommendation benchmark on the BanglishRev dataset, 
covering six model families evaluated under a temporally 
rigorous per-user chronological leave-last-out protocol.

## Dataset Setup
Download BanglishRev from [link] and place at `data/BanglishRev.json.gz`.  
See `data/README.md` for full instructions.

## Installation
```bash
pip install -r requirements.txt
```

## Reproducing Results
Run notebooks in order:

| Notebook | Description |
|---|---|
| 01_eda.ipynb | Dataset diagnostics and language analysis |
| 02_collaborative_filtering.ipynb | UserCF, ItemCF, GlobalPop, CatPop |
| 03_matrix_factorization.ipynb | ExplicitMF (SVD), ImplicitMF (ALS) |
| 04_content_based_filtering.ipynb | TF-IDF CBF + language-stratified eval |

**For sparsity ablation:** Change `MIN_USER_INTERACTIONS` and 
`MIN_ITEM_INTERACTIONS` in the config cell of each model notebook.  
Settings evaluated: (5,3), (10,3), (15,3), (15,5), (20,5).

## Pre-computed Results
Results from all runs are in `results/`. Primary benchmark uses (10,3).

## Citation
[BibTeX will go here once paper DOI is assigned]