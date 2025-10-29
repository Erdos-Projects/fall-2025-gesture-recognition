# kpis.md

### KPI Definition (Key Performance Indicators)

#### Primary KPI

**Metric:** F1 macro score (`f1_macro`)

- **Definition/Formula:** Harmonic mean of precision and recall, calculated across all gesture classes using the macro average; addresses concerns regarding class imbalance within the gesture data.

- **Improvement Direction:** Maximize the F1 macro score.

#### Secondary KPIs

**Metric 1:** Accuracy

- **Definition/Formula:** Proportion of correctly classified gesture instances.

- **Improvement Direction:** Maximize the accuracy.

**Metric 2:** Classification error rate (CLER)

- **Definition/Formula:** Proportion of ground-truth labels for which the corresponding prediction is incorrect; vital for assessing neuromotor interface performance.

- **Improvement Direction:** Minimize the CLER

**Metric 3:** TBD

- **Definition/Formula:** TBD

- **Improvement Direction:** TBD

#### Baseline Definition

Baseline performance was recorded for all primary and secondary KPIs using models such as trivial (`DummyClassifier`), linear (`LogisticRegression`), and tree-based models (`RandomForestClassifier`). These baselines were evaluated using a cross-validation strategy specifically designed for personalization, reflecting performance on the *same user's* unseen data.
