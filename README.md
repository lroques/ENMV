# ENMV host adaptation model

This repository contains the code and posterior samples used to analyse host adaptation in **Endive necrotic mosaic virus (ENMV)** using a mechanistic evolutionary rescue model derived from Fisher’s geometric model.

The analysis infers host optima in an n-dimensional phenotypic space and compares models with different phenotype dimensions (n = 1, 2, 3).

---

# Repository contents

## Data

- `Data_RESISTE_ENMV.xlsx`  
  Experimental cross-inoculation dataset used in the analysis.

---

# Notebooks

## 1. Data exploration and statistical diagnostics

`ENMV_statistical_analysis.ipynb`

This notebook performs descriptive and diagnostic analyses of the experimental data without fitting the mechanistic model. It:

- reconstructs infection counts from the raw dataset
- visualizes infection success rates
- examines lineage variability
- quantifies overdispersion relative to a binomial model
- estimates the beta–binomial dispersion parameter $\kappa$

The notebook generates several diagnostic figures saved as PNG files.

---

## 2. Bayesian inference of the mechanistic model

- `ENMV_MCMC_n1.ipynb`
- `ENMV_MCMC_n2.ipynb`
- `ENMV_MCMC_n3.ipynb`

These notebooks perform Bayesian inference of the evolutionary rescue model for phenotype dimensions \(n=1,2,3\).

Each notebook:

- loads the experimental data
- runs a Metropolis MCMC sampler
- produces posterior predictive checks and summary figures
- saves posterior samples

Output files:

- `posterior_n1.pkl`
- `posterior_n2.pkl`
- `posterior_n3.pkl`

---

## 3. Model comparison

`Compare_dimensions.ipynb`

This notebook compares models with phenotype dimensions \(n=1,2,3\) using posterior samples.

For each model it computes:

- WAIC (Widely Applicable Information Criterion)
- PSIS-LOO approximate leave-one-out cross-validation
- an approximate BIC evaluated at the best posterior draw


---

# Requirements

The notebooks require Python with the following packages:

- numpy
- pandas
- scipy
- matplotlib
- openpyxl (for reading Excel files)

---

# Reproducibility

Posterior samples (`posterior_n*.pkl`) are included in the repository, so the analysis and model comparison notebooks can be run without recomputing the MCMC inference.

Random seeds are fixed where stochastic subsampling is used to ensure reproducibility.
