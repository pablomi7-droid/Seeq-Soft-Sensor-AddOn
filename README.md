# Seeq Soft-Sensor AddOn
This is a simple AddOn tool to predict a signal based on multiple regressor signals with Machine Learning models in Seeq. It can be packaged into a fully functional AddOn in your Seeq Server by following the instructions in https://github.com/seeq12/seeq-addon-templates. 

### Why use this AddOn?
This AddOn enables all kinds of Seeq users to build powerful Machine Learning models for signal predictions without creating specific DataLab projects. It can handle both regression and classification problems, automating data pre-processing steps (data cleaning, feature selection, scaling, one-hot encoding, PCA and SMOTE), testing different model types with cross-validation, tuning hyperparameters and pushing the predictions to a Seeq Worksheet with only a few clicks. 

### What types of models does the AddOn work with?
Currently, the tool searches through the following models:
- Classification: Knneighbors, Logistic Regression, Random Forest Classifier, and Gradient Boosting Classifier
- Regression: Knneighbors, Ridge Regression, Random Forest and Gradient Boosting

Additional model types, hyperparameters and number of cross-validation folds to include in GridSearchCV can easily be updated to adapt the AddOn to specific needs.

### What metrics are used to assess model performance?
The metrics to determine the best estimator depend on whether it's a regression or classification problem and the values of the variable to predict in the training data. The philosophy behind these metric choices is to choose the most representative metric based on the available data. They can be substituted for custom metrics if desired. 
- Classification: 
  - Balanced Accuracy 
- Regression:
  - Inverse of MAE if the values are close to 0
  - Complement of MAPE otherwise

### Loading a pre-trained model
By default, the AddOn will train a new model every time based on the selected training window. However, it is also possible to load a pre-trained model (.pkl), ignoring the training window, speeding up the predictions and ensuring consistent model behavior. To work correctly, the model must have been trained with the same features present in the regressors dropdown (with signal ID as feature headers). This feature works natively for scikit estimators, but XGB models may require additional steps (see https://xgboost.readthedocs.io/en/stable/tutorials/saving_model.html).

### Preview
https://github.com/user-attachments/assets/1a4461b4-4f53-4a3e-8d96-d896c56f4936

### Signal metadata
When the predicted signal is pushed to the Seeq Workbench, the signal metadata will contain:
- Estimator used for prediction and its parameters
- Regressors used
- Metric score
- Signal mapping (only for multiclass classification)

### Example Pipepline
<img width="408" alt="Captura de pantalla 2025-01-22 093936" src="https://github.com/user-attachments/assets/b41019e4-b0da-46f3-a64c-cfeb94bf5f2d" />
