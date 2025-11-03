# evaluation_plan.md

## Quick Summary

Our goal is to predict gestures from emg data. We have already extracted features (160 total = 10 features x 16 channels). There are 100 users, and 9 gestures which were recorded during various stages (e.g. thumb_swipes_static_arm_raised, pinch_release_dynamic_vertical_arm_translation,...).

## Splitting Strategy

We are taking a personalized approach, so we will be training the model for each user separately.

For each user, we will split the data into 80% train, 20% test, stratified by stage and gesture. This is meant to match a deployment where the user performs calibration gestures while setting up the device.

Important notes:
 - We must split the data before we perform feature selection, and only use the training data to select features
 - Extra care needs to be taken using the built in stratification functionality of train_test_split because some users have stage-gesture combinations with as few as 1 data point. See train_test_split_exploration.pynb for details.

When training the models, we will use per-user K-Fold cross-validation (K=5)

## Metrics

Primary KPI: (mean) F1 macro score. Since we are training for each user separately, we will consider the mean F1 macro score across users, as well as the min and max F1 macro score across users.
Reasoning: F1 macro score is the harmonic mean of precision and recall, calculated across all gesture classes using the macro average; addresses concerns regarding class imbalance within the gesture data.

Also consider: Accuracy

Important visualizations: swarm plot to see how accuracy varies across users, confusion matrix