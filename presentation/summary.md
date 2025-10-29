# Executive Summary

> - Executive summary document (summary.md or .pdf) with:
>   - Problem, data sources, KPIs, results.
>   - Final model choice with justification.
>   - Limitations and next steps.

## Problem, data sources, KPIs, and results

We are focused on building a robust, high-performance model while minimizing generalization error. Our core objective is personalized discrete gesture classification using surface electromyography (sEMG) data. Since sEMG signatures show significant inter-user variability, our main challenge is personalization: ensuring the model generalizes reliably to unseen actions by the same individual.

* Data source: sEMG recordings from the [generic neuromotor interface](https://github.com/facebookresearch/generic-neuromotor-interface) dataset, encompassing 100 participants ([Kaifosh et al. 2025 Nature](https://doi.org/10.1038/s41586-025-09255-w))
* Features: We extracted 160 features (10 types $\times$ 16 channels). Following analysis in the feature selection notebook, we successfully filtered these down to a stable subset (i.e., 11 selected features). The feature importance log suggests that channels 4 and 5 may be highly discriminative.
* KPIs: Our primary metric to maximize is the F1 macro score to handle classification imbalance across gesture categories. Secondary metrics include accuracy and classification error rate (CLER).

### Preliminary results

We employed a robust within-user cross-validation strategy across all 100 participants to simulate real-world personalization and assess generalization error. The performance comparison is logged in `model_comparison.csv`.

| Model | Mean F1 Macro Score (CV) | Std F1 Macro Score (CV) | Key Finding |
| :--- | :--- | :--- | :--- |
| **LogisticRegression\_L2** | TBD | TBD | (TBD) Best average performance? |
| **XGBoost** | TBD | TBD | (TBD) Ensemble did not improve performance? |

Our experiments show that the simpler, linear model (`LogisticRegression_L2`) outperformed the more complex ensemble methods (XGBoost, RandomForest), demonstrating that complex models did not justify their added complexity for this particular personalization task.

## Final model choice with justification

Final model: TBD

Justification: TBD (to confirm why the selected model (e.g., Logistic Regression) achieves the required balance of performance on the F1 macro KPI, interpretability, and operational efficiency, thereby minimizing generalization error)

## Limitations and next steps

### Current limitations

1. Data stratification: We encountered challenges managing low-count combinations of gesture-stage interactions, which complicated robust data splitting.
2. TBD

### Future directions

Potential future research avenues include:

1.  Deep learning models: Explore integrating advanced architectures like convolutional neural networks (Conv1D), which are used in related sEMG research, to potentially capture temporal dependencies missed by classical models
2.  Translational research: Test how effectively the personalized modeling techniques developed here can be applied or transferred to clinical populations with neuromuscular conditions
3.  TBD
