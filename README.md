# DA3410 Assignment 11: Ordinary Least Squares as an Attention Mechanism

## Overview

This repository contains my implementation and experimental evaluation of the paper *Ordinary Least Squares as an Attention Mechanism* by Philippe Goulet Coulombe.

The objective of this project is to investigate how ordinary least squares (OLS) and related regression estimators can be represented as attention operations, and to evaluate Attention Regression against conventional machine-learning models on simulated datasets.

## Experiments

### Experiment 1: OLS as an Attention Mechanism

- Implemented conventional OLS and its attention-based representation.
- Compared predictions to verify numerical equivalence.
- Evaluated attention-weight properties and numerical differences across simulation configurations.

**Key result:** The maximum absolute prediction difference across the full benchmark was approximately \(2.274 \times 10^{-13}\).

### Experiment 2: Beyond OLS

- Extended the attention representation to Principal Component Regression (PCR) and ridge regression.
- Compared conventional estimator predictions with their spectral-attention counterparts.
- Evaluated different numbers of principal components and ridge regularisation parameters.

**Key result:** The maximum prediction differences were approximately \(5.33 \times 10^{-14}\) for PCR and \(6.79 \times 10^{-13}\) for ridge regression.

### Experiment 3: Attention Regression and Baseline Comparison

- Evaluated Attention Regression against OLS, Random Forest, Multilayer Perceptron (MLP), and Gradient Boosting.
- Tested six simulated data-generating processes across four training sizes and four signal-to-noise ratios.
- Compared average test \(R^2\) values and individual data-generating-process results with the paper.

**Key result:** The overall model ranking matched the paper. Attention Regression achieved an average test \(R^2\) of 0.479 in my run, compared with 0.476 in the paper.

**Reproduction limitation:** Experiment 3 used one replication per condition under a limited-compute configuration, whereas the paper reports averages over ten replications. The results should therefore be interpreted as a resource-constrained reproduction, not an exact numerical replication.

## Repository Structure

- `notebooks/` — Jupyter notebooks for the experiments.
- `Exp_1_OLS_as_Attention_results/` — Experiment 1 outputs.
- `Exp_2_Beyond_OLS_results/` — Experiment 2 outputs.
- `Exp3_attention_retention_results/` — Experiment 3 results and paper comparisons.
- `figures/` — Generated experimental plots.
- `General/` — Supporting materials.
- `A11.pdf` — Assignment document.
- `report.pdf` — Final experimental report.

## Evaluation Metric

Predictive performance is measured using the out-of-sample coefficient of determination, \(R^2\). Higher test \(R^2\) indicates better predictive performance relative to predicting the test-set mean.

## Tools and Technologies

- Python
- NumPy and Pandas
- scikit-learn
- PyTorch
- Matplotlib
- Jupyter Notebooks / Kaggle

## Reference

Philippe Goulet Coulombe, *Ordinary Least Squares as an Attention Mechanism*.

Author's research code: https://github.com/philgoucou/ols-attention