# modeling_plan.md

### Model Families Tried and Rationale

We evaluated three model families for discrete gesture classification:

1.  **Trivial/linear baselines:** `DummyClassifier`, `LogisticRegression_L2`, and `RidgeClassifier` to establish performance floors and maximize initial interpretability
2.  **Ensemble models:** `RandomForestClassifier` and `XGBoostClassifier` to capture non-linear interactions within the surface electromyography (sEMG) features

### Alignment with Project Goals

The objective is personalized discrete gesture classification, necessary due to high inter-user sEMG variability.

**Evaluation strategy:** We enforced within-user cross-validation using `StratifiedKFold` ($K=5$) per user across 100 participants to ensure we measure generalization performance on *unseen data from the same individual*.

**KPI alignment:** The primary optimization target is the F1 macro score to accurately measure classification performance across all gesture classes while addressing concerns regarding class imbalance.

### Justification for Final Chosen Model

TBD

### Notes on what didn’t work and why those approaches were discarded

TBD
