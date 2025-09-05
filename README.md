# Predicting Superconductor Critical Temperature (Tc) with a WSO-Tuned MLP

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](
  https://colab.research.google.com/github/MedBelhoucha/tc-prediction/blob/main/notebooks/Predicting_Superconductor_Tc.ipynb
)

**Main test results:** R² 0.907, RMSE 10.46 K, MAE 6.26 K, r 0.952.

**How to run in Colab**
1. Open the notebook with the badge above.
2. Put `train.csv` (and `unique_m.csv` if used) in `MyDrive/TcProject/`.
3. Run all cells top → bottom.

**Notes**
- 81 engineered features + Tc (same as the article)
- Stratified splits by Tc deciles; train-only scaling
- MLP tuned with White Shark Optimizer (WSO); early stopping on val RMSE

## Dataset & Source

We use the UCI Machine Learning Repository dataset **“Superconductivty Data”** (Hamidieh, 2018).  
It contains **21,263** materials. `train.csv` has **81 engineered numeric features** + the target (critical temperature, K); `unique_m.csv` contains the element breakdown per formula.

- Dataset page: http://archive.ics.uci.edu/dataset/464/superconductivty+data
- License: **CC BY 4.0** (follow UCI terms)
- Citation: Hamidieh, K. (2018). *Superconductivty Data* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C53P47

> Note: The UCI page states the original records come from the **SuperCon** database (NIMS). We do **not** include raw data in this repo; please download it from UCI and follow their license.
.

## Related Work (Article)

We compare against the article that uses **MARS** optimized by a meta-heuristic and linear baselines (Ridge/Lasso/Elastic-Net) on the **same 81 features**.

- Reported performance (approx.): R² ≈ 0.80, RMSE ≈ 15 K, MAE ≈ 10–11 K (numbers depend on their split).
- Our method: a **WSO-tuned MLP** with stratified splits and train-only scaling.

**Reference (fill exact citation):**  
García-Nieto, P.J., García-Gonzalo, E. & Paredes-Sánchez, J.P. Prediction of the critical temperature of a superconductor by using the WOA/MARS, Ridge, Lasso and Elastic-net machine learning techniques. Neural Comput & Applic 33, 17131–17145 (2021). https://doi.org/10.1007/s00521-021-06304-z
