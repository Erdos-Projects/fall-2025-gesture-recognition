# fall-2025-gesture-recognition

**Authors:** Brian R. Mullen, Carrie Clark, Revati Jadhav, Philip Nelson, Sero Toriano Parel

**Erdős Institute Data Science Boot Camp Fall 2025 Project**

Implementing and evaluating personalized models for discrete hand gesture classification from surface electromyography (sEMG) signals, focusing on achieving robust performance for individual users. Personalization is a critical aspect, as surface electromyography (sEMG) signals exhibit high inter-user variability, such that models are evaluated on the same user's unseen data. The project utilizes the `discrete_gestures` in the `generic-neuromotor-interface` dataset to support robust wearable device design.

## Project Status and Deliverables

### Data Acquisition and Preparation

- [x] Data gathering and Key Performance Indicator (KPI): primary KPI is F1 Macro due to multi-class classification.
- [x] Raw sEMG data for 100 participants successfully loaded and preprocessed.
- [x] Data cleaning and alignment strategy finalized, including Z-score normalization applied separately to each of the 16 EMG channels.

### Feature Engineering and Selection

- [x] Exploratory data analysis (EDA) performed, generating a data audit summary.
- [x] Feature extraction pipeline implemented, extracting 160 features (10 features across 16 channels): features include root mean square (RMS), mean absolute value (MAV), and frequency-based metrics (e.g., median frequency).
- [x] Dimension reduction analysis performed (PCA and t-SNE) showing feature separation.
- [x] Feature selection complete, resulting in a smaller final feature set (e.g., 11 features selected for experiments), with channels ch05, ch04, ch06, ch03, and ch10 identified as high priority.

### Modeling and Evaluation

- [x] Personalized cross-validation split strategy defined and implemented: Stratified K-Fold per user to ensure evaluation mirrors deployment scenarios where a model generalizes within a single user.
- [ ] Baseline modeling implemented in `notebooks/baseline.ipynb`, including linear models (Logistic Regression L2) evaluated using cross-validation.
- [x] Complex models explored (RandomForest, XGBoost) in initial experiments.
- [x] Log cross-validation scores to comparison table (`model_comparison.csv`).
- [ ] Implement final chosen model execution/evaluation logic on the untouched test holdout set.
- [ ] Finalize executive summary (`summary.md`) and presentation slide deck (re: problem, data sources, KPIs, and results).

## References

- Kaifosh, P., Reardon, T.R. & CTRL-labs at Reality Labs. A generic non-invasive neuromotor interface for human-computer interaction. Nature (2025). https://doi.org/10.1038/s41586-025-09255-w
- Kaifosh, P., Reardon, T.R. & CTRL-labs at Reality Labs. A generic non-invasive neuromotor interface for human-computer interaction. (2025). GitHub repository, https://github.com/facebookresearch/generic-neuromotor-interface
