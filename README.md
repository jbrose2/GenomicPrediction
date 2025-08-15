# Predicting Drought Tolerance from Genomic + Environmental Data (Demo)

This is a project that demonstrates an end-to-end workflow for genomic prediction
in a crop context (here using synthetic data shaped like maize trials). It mirrors the kind of workflow
you might run for genomic + environmental → phenotype prediction.

## Workflow

1. **Data**: SNP genotype matrix, environmental covariates (temperature, rainfall, VPD), and a continuous
   drought tolerance index.
2. **Preprocessing**: Filter SNPs by missingness, mean-impute, variance filter.
3. **Feature selection**: Univariate F-test to keep the top 1000 SNPs; concatenate env features.
4. **Model**: Gradient boosting regressor (XGBoost).
5. **Validation**: Train/validation split with holdout test; report R², RMSE, MAE and compare to a mean baseline.
6. **Explainability**: Global feature importance plot (top 25 features) and Observed vs Predicted.

## Files

- `data/`
  - `genotypes.snps.csv` — synthetic SNP genotypes (0/1/2) with realistic missingness.
  - `environment.csv` — synthetic environmental covariates.
  - `phenotypes.csv` — synthetic phenotype (drought tolerance index).
- `results/`
  - `metrics.csv` — R², RMSE, MAE + baselines on the held-out test set.
  - `figures/observed_vs_predicted.png`
  - `figures/feature_importance_top25.png`
- `run_demo.py` — script that executes the full pipeline.
- `requirements.txt` — Python packages.

## How to Run

```bash
pip install -r requirements.txt
python run_demo.py
```