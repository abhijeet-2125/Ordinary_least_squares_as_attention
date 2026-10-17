# Ordinary Least Squares as an Attention Mechanism

**Statistical Learning · Attention Mechanisms · Regression**

An empirical reproduction and evaluation of *Ordinary Least Squares as an Attention Mechanism*, investigating the mathematical equivalence between ordinary least squares (OLS) and attention-based prediction and extending the analysis to regularized regression and nonlinear attention regression.

## Overview

This project investigates how classical statistical estimators can be expressed through attention mechanisms. Rather than treating attention exclusively as a neural-network component, the study examines its relationship with least-squares estimation and explores how spectral transformations, dimensionality reduction, and regularization affect predictive performance.

The implementation reproduces three experimental components:

- **Experiment 1 — OLS as Attention:** Implements the spectral attention formulation and verifies its numerical equivalence to conventional OLS predictions.
- **Experiment 2 — Beyond OLS:** Extends the equivalence analysis to Principal Component Regression (PCR) and Ridge Regression.
- **Experiment 3 — Attention Regression:** Evaluates attention regression against conventional machine-learning baselines across six data-generating processes, varying sample sizes, and signal-to-noise ratios.

## Questions

1. Can ordinary least squares be represented as an attention mechanism without changing its predictions?
2. Can the attention formulation reproduce PCR and Ridge Regression under their corresponding spectral and regularization constraints?
3. How does attention regression compare with conventional regression and nonlinear machine-learning models across different data-generating processes?

## Methodology

### 1. OLS as an Attention Mechanism

The first experiment implements the spectral representation of OLS as an attention-based predictor. Conventional least-squares predictions are compared numerically with predictions obtained from the attention formulation.

**Key finding:** Across 960 evaluations, the two implementations produced numerically equivalent predictions, with a maximum absolute prediction difference of approximately \(2.27 \times 10^{-13}\).

### 2. Extensions Beyond OLS

The second experiment examines two extensions:

- **Principal Component Regression (PCR):** Varies the number of retained principal components to study the effect of dimensionality reduction.
- **Ridge Regression:** Varies the regularization parameter to examine the effect of coefficient shrinkage.

The conventional estimators are compared against their corresponding spectral attention formulations.

**Key findings:**
- PCR: 4,800 evaluations, with a maximum absolute prediction difference of approximately \(5.33 \times 10^{-14}\).
- Ridge Regression: 4,800 evaluations, with a maximum absolute prediction difference of approximately \(6.79 \times 10^{-13}\).

These results support the numerical equivalence of the implemented estimator pairs.

### 3. Attention Regression and Nonlinear Baselines

The third experiment compares Attention Regression with four conventional baselines:

- Ordinary Least Squares (OLS)
- Random Forest (RF)
- Multilayer Perceptron (MLP)
- Gradient Boosting Machine (GBM)

The benchmark spans six data-generating processes: Linear, Friedman 1, Friedman 2, Friedman 3, Rotated Sine, and Soft Radial. Each process is evaluated across four training-set sizes and four signal-to-noise ratios.

**Computational note:** Due to resource constraints, this reproduction evaluates one replication per configuration, compared with ten replications in the paper. Attention Regression also uses a time cap and early stopping. The results therefore represent a limited-compute empirical reproduction rather than an exact replication of the paper's full benchmark.

## Results

### Overall predictive performance

The table reports mean test \(R^2\) across the 96 Experiment 3 configurations. The paper's reported means are included for comparison.

| Model | Reproduction | Paper |
|---|---:|---:|
| OLS | 0.288 | 0.279 |
| Random Forest | 0.455 | 0.454 |
| MLP | 0.530 | 0.521 |
| GBM | 0.418 | 0.418 |
| Attention Regression | 0.479 | 0.476 |

The overall ranking matches the paper:

**MLP > Attention Regression > Random Forest > GBM > OLS**

The aggregate results are close to the reported values, although individual configurations differ. Attention Regression also shows larger condition-level deviations than the other models, which should be interpreted in light of the reduced replication count and computational limits.

### Interpretation

The experiments illustrate two complementary findings:

1. **Mathematical equivalence:** Classical estimators can be represented through attention-based formulations while preserving their predictions, provided the corresponding transformations and constraints are implemented correctly.
2. **Empirical performance:** Predictive performance depends on the data-generating process, sample size, noise level and model configuration. Attention Regression is competitive overall, but it does not outperform every baseline in every setting.

## Repository Structure

```text
ordinary-least-squares-as-attention/
├── notebooks/
│   ├── exp1_2.ipynb
│   └── exp3.ipynb
├── exp1_ols_as_attention_results/
│   ├── csv/
│   └── tables/
├── exp2_beyond_ols_results/
│   ├── csv/
│   └── tables/
├── exp3_attention_regression_results/
│   ├── condition_means_vs_paper.csv
│   ├── findings.txt
│   ├── results_long.csv
│   ├── table2_ours_vs_paper.csv
│   └── table_overall_and_per_dgp.csv
├── General/
│   ├── csv/
│   └── experiment_configuration.json
├── figures/
├── A11.pdf
├── report.pdf
├── README.md
└── .gitignore
```

*The folder names above assume the proposed renaming has been completed. The notebooks and result files contain the detailed implementations and exported experimental outputs.*

## Reproducibility

The repository includes Jupyter notebooks, exported CSV results, summary tables, visualizations and the report.

To explore the experiments:

1. Clone the repository.
2. Install the required Python libraries in an isolated environment.
3. Open the notebooks in Jupyter or a compatible notebook environment.
4. Run the experiments and compare the resulting predictions and metrics with the exported results.

Exact package versions, runtime requirements, and execution settings should be recorded alongside the notebooks when preparing a fully reproducible environment.

## Reference

Goulet Coulombe, Philippe. *Ordinary Least Squares as an Attention Mechanism.*

Reference implementation: [philgoucou/ols-attention](https://github.com/philgoucou/ols-attention)

---

**Research focus:** Connecting classical statistical estimation with attention mechanisms through mathematical derivation, numerical verification and empirical benchmarking.
