# fall-2025-gesture-recognition

**Authors:** Brian R. Mullen, Carrie Clark, Revati Jadhav, Philip Nelson, Sero Toriano Parel

**Erdős Institute Data Science Boot Camp Fall 2025 Project**

Implementing and evaluating personalized models for discrete hand gesture classification from surface electromyography (sEMG) signals. Our core methodology addresses the necessity of achieving robust within-user generalization (evaluation on the same user's unseen data) due to the high inter-user signal variability inherent in sEMG signatures. The project utilizes the `discrete_gestures` in the `generic-neuromotor-interface` dataset ([Kaifosh et al. 2025](https://doi.org/10.1038/s41586-025-09255-w)) to support robust wearable device design.

## Key Performance Indicators (KPIs)

* **Primary KPI:** F1 Macro score, to maximize classification performance across all nine discrete gesture classes, robustly addressing challenges posed by multi-class classification and potential class imbalance stemming from gesture/stage combinations with low counts.
* **Secondary KPIs:** Classification accuracy, classification error rate
* **Evaluation Strategy:** Performance was measured using within-user cross-validation (CV) and confirmed on a final, untouched test holdout set

## Project Deliverables and Final Results

| Deliverable | Description |
| :--- | :--- |
| Problem Definition & KPIs | Project guiding question, stakeholders, and KPI definitions finalized (`kpis.md`) |
| Data Acquisition & Preparation | Raw sEMG data for 100 participants successfully loaded. Data cleaned, aligned (event-based peak detection), and preprocessed using Z-score normalization applied separately to each of the 16 EMG channels |
| Evaluation Plan | Personalized split implemented using stratified 80/20 K-Fold per user (within-user CV) to ensure evaluation mirrors deployment scenarios |
| Feature Engineering | Feature extraction yielded 160 features. Feature selection (by random forest ranking and correlation pruning) successfully reduced the feature space to 37 non-redundant metrics. Key features included RMS metrics, concentrated heavily on sEMG channels ch05, ch04, and ch10. |
| Modeling & Validation | Evaluated trivial, linear (Logistic Regression), and tree-based models (random forest, XGBoost). Final model selected: **Logistic Regression with L2 regularization (Logit\_L2)** due to robust CV performance and interpretability. |
| Final Results | **Strong within-user generalization** achieved on calibration data splits (CV Mean F1 Macro $\approx \mathbf{0.7164}$). **Poor generalization to unseen gestures** (Holdout Test F1 Macro $\approx \mathbf{0.3977}$), confirming significant performance heterogeneity across users. Error analysis revealed systematic confusion, particularly between specific finger release gestures and directional thumb movements. |
| Final Documentation | Executive summary (`summary.pdf`) and presentation slide deck (`presentation/`) finalized and stored. |

## Repository Structure Overview

| Directory | Key Files/Artifacts | Purpose |
| :--- | :--- | :--- |
| `deliverables/` | `summary.pdf`<br>`kpis.md`<br>`evaluation_plan.md`<br>`modeling_plan.md` | Written conceptual documentation deliverables |
| `results/` | `feature_selection.csv`<br>`model_comparison.csv` | Logs of feature elimination decisions and cross-validation KPI scores |
| `notebooks/` | `eda.ipynb`<br>`feature_selection.ipynb`<br>`modeling_experiments.ipynb`<br>`final_results.ipynb` | Exploratory analysis, modeling experiments, and final results evaluation |

## References

- Kaifosh, P., Reardon, T.R. & CTRL-labs at Reality Labs. A generic non-invasive neuromotor interface for human-computer interaction. Nature (2025). https://doi.org/10.1038/s41586-025-09255-w
- Kaifosh, P., Reardon, T.R. & CTRL-labs at Reality Labs. A generic non-invasive neuromotor interface for human-computer interaction. (2025). GitHub repository, https://github.com/facebookresearch/generic-neuromotor-interface
