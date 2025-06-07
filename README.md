# Drug Solubility and Metabolic Stability Prediction

This repository contains code, datasets, and pretrained models for predicting **aqueous solubility** (regression) and **mouse liver microsomal (MLM) stability** (classification) of drug-like molecules using machine learning. The models are based on a unified molecular featurization pipeline and state-of-the-art gradient boosting algorithms.

## Overview

We implemented two models:

- **Solubility Prediction**: A LightGBM Regressor trained on the AqSolDB dataset (from [TDC Benchmark Suite](https://tdcommons.ai)).
- **MLM Stability Prediction**: An XGBoost Classifier trained on a curated dataset from Dong et al. (2015), Journal of Pharmaceutical Sciences.

All feature generation is based on SMILES strings and uses a composite of:
- Morgan Fingerprints (1024-bit, radius=2)
- Avalon Fingerprints (1024-bit, count-based)
- ErG Pharmacophoric Fingerprints
- 208 RDKit Physicochemical Descriptors

## Results

| Task                | Metric      | Performance                   |
|---------------------|-------------|--------------------------------|
| Solubility (logS)   | MAE         | **0.729 ± 0.002**              |
|                     | R²          | **0.925**                      |
| MLM Stability       | ROC AUC     | **0.878 ± 0.019** (CV)         |
|                     | Accuracy    | **82.9%** (External test set)  |

## Repository Structure

```

├── data/
│   ├── solubility\_train.csv
│   ├── solubility\_test.csv
│   ├── mlm\_train.csv
│   └── mlm\_test.csv
├── models/
│   ├── solubility\_lgbm.pkl
│   └── mlm\_xgboost.pkl
├── notebooks/
│   ├── 1\_train\_solubility\_model.ipynb
│   ├── 2\_train\_mlm\_model.ipynb
│   └── 3\_evaluate\_models.ipynb
├── utils/
│   └── featurization.py
└── README.md

````

## Getting Started

Install dependencies:

```bash
pip install -r requirements.txt
````

Run the notebooks in order to reproduce training and evaluation.

## Citation

All datasets, code, and models are also archived on Zenodo:
**\[DOI: 10.5281/zenodo.15616176]**

## License

MIT License.
