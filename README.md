# Seeq Soft-Sensor AddOn
This is a simple AddOn tool to predict a signal based on multiple regressor signals with Machine Learning models in Seeq. It can be packaged into a fully functional AddOn in your Seeq Server by following the instructions in https://github.com/seeq12/seeq-addon-templates. 

### Why use this AddOn?
This AddOn enables all kinds of Seeq users to build powerful Machine Learning models for signal predictions without creating specific DataLab projects. It can handle both regression and classification problems, automating data pre-processing steps (data cleaning, feature selection, scaling, one-hot encoding, PCA, SMOTE/SMOGN etc.) testing different model types with cross-validation, tuning hyperparameters and pushing the predictions to a Seeq Worksheet with only a few clicks. 

### What types of models does the AddOn work with?
Currently, the model searches through the following models:
- Classification: Knneighbors, Logistic Regression, Random Forest Classifier, and Gradient Boosting Classifier
- Regression: Knneighbors, Ridge Regression, Random Forest and Gradient Boosting

Additional model types, hyperparameters and number of cross-validation folds to include in GridSearchCV can easily be updated to adapt the AddOn to specific needs.

### What metrics are used to assess model performance?
The metrics to determine the best estimator depend on whether it's a regression or classification problem and the values of the variable to predict in the training data. The philosophy behind these metric choices is to choose the most representative metric based on the available data. These metrics can be substituted for custom metrics if desired. 
- Classification: 
  - F1 Score if the variable is binary
  - Balanced Accuracy if the variable is multiclass
- Regression:
  - Inverse of MAE if the values are close to 0
  - Complement of MAPE otherwise
