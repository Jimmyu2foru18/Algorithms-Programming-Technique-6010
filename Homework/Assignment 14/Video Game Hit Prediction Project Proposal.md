# Video Game Hits from Pre-Release Metadata

James McGuigan

SUNY College at Old Westbury, Old Westbury, New York, USA

Project Proposal • December 3, 2026

## Project Proposal

I want to see if Random Forest and Xgboost use prerelease metadata to predict whether a video game reaches at least 1.0 million global sales. I also want to see how tree ensembles compare against single trees and distance-based models under class imbalance, and how changing the probability threshold affects expected return.

For the setup, I'm planning to use vgsales.csv covering the years 1980 to 2020. I set hit_game to 1 when Global_Sales is at least 1.0 million and 0 otherwise. Once the target is set, I will drop all sales and rank columns. I hold out an untouched test set with a stratified split and run stratified cross validation on the remaining games. Inside each training fold, I run imputation, encoding, and SMOTE to prevent data leakage, and I skip feature scaling for tree models.

### Starting Goals

- Clean the vgsales.csv file remove entries and drop any columns that could cause data leakage.
- Create pre-release features such as release decade, console generation across platforms and publisher frequency during training folds.
- Tune Random. Xgboost models using stratified cross-validation comparing balanced class weights and SMOTE.
- Evaluate the models using accuracy, F1 score, ROC AUC and PR AUC.
- Optimize decision thresholds based on assumed marketing costs.
- Use SHAP to explain model predictions.

The study uses the vgsales.csv dataset, which contains records and attributes spanning past years. The target variable assigns a hit_game label when Global_Sales reaches the threshold and leaves it negative otherwise. This label separates the dataset into hits and nonhits. Because Global_Sales comes from sales columns, the workflow removes all sales and rank columns after setting the target. A stratified split holds out a test set of games that remains untouched throughout training. The remaining games enter stratified fold validation. The workflow applies imputation, encoding, and SMOTE within each training fold to prevent data leakage. The tree model will be used to skip feature scaling.

## Process of Analysis

### Clean and Sanitize Dataset

Remove duplicates from vgsales.csv. Handle missing values and drop all columns that could leak information.

### Engineer Pre-Release Features

Create a release decade (1980s, 1990s). Identify console generation based on 31 platforms. Build publisher frequency features using training folds to avoid leakage.

### Train and Benchmark Classifiers

Use five algorithms: Logistic Regression, K-Nearest Neighbors, Decision Tree, Random Forest and Xgboost. Apply stratified cross validation and compare models using balanced class weights and SMOTE resampling.

### Evaluate, Optimize and Explain

Compare models using accuracy, precision, recall, F1 score, Cohens kappa, ROC AUC and PR AUC. Optimize decision thresholds by testing values from 0.05 to 0.95 using assumed marketing cost per predicted hit and net return per positive. Compute SHAP values to explain model predictions.

### Data Inspection

Check the dataset size, column types, number of categories and sample entries.

### Leakage and Hygiene Control

Remove duplicates. Look for Year values like 0. Handle missing Year and Publisher values by imputing or categorizing them. Make sure all post-release sales and rank columns are removed.

### Exploratory Data Analysis

Look at the class balance of games are hits. Check hit rates across genres, platforms and publishers then examine distributions of features and correlation matrices.

## Expected Outcomes

Both Random Forest and Xgboost are expected to outperform a majority class baseline on PR AUC, F1 score and balanced accuracy. They should capture relationships, between publisher size, console generation and game genre. Xgboost is expected to perform better than Random Forest overall, though this will be tested rather than assumed. Since the metadata does not include game quality or marketing spend there will be some variance with this. Threshold tuning is essential for this and to find best results.
