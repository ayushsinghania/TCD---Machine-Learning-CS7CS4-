# TCD ML Comp. 2019/20 - Income Prediction
**Goal**: Predict income.

This repository consists of the source code in the form a jupyter notebook used to participate in Machine Learning competition as part of the 2019/20 machine learning module at Trinity College Dublin.

It has the following files
- Income_Prediction.ipynb - The Jupyter Notebook was used to generate the final Code
- Local_Prediciton.ipynb - This was used to locally calculate the RMSE values test the model and experiment with the data
- Submission.csv - Final Solution File 

Two separate notebooks were maintained out of habit to not clutter the single notebook with everything being done in one, which often led to somethings being over-written or being misplaced.

## Method
The program follows the following sequence:

- Load Data
- Split Data [80-20]
- Combine Data [Train & Test]
- Clean Data
- Encode Data
- Normalize & Scale Data
- Final Data Pre-processing
- Model Selection
- Fit Data
- Predict
- Plot feature importance
- Redo with selected Features
- Save

## Data Cleanup & Scaling 

#### Concat
The two datasets train (with label) and test (without a label) was concatenated initially for encoding and handle the null values in the data. Add a flag (train:1, test:0) to sperate the two later.

#### Handle Null Value
The null values replaced with the mean of their respective columns.

#### Encode
Initially, One-Hot Encoding was applied to the datasets, which increased the dimension of the data to a very large value.

After that, Target Encoding was applied instead which was the better solution in my case.

Also, tried the label encoder which tuned out be a horrible decision as we had too many labels.

#### Split

Split again the data into two, tests & train.

#### Scale
StandardScaler() was used to scale the data

#### Final Pre-processing
PolynomialFeatures() was used to do it

## Model 
Initially started with Linear Regression, then went to experiment with many other such as Random Forest Regressor, KNN & Ridge before landing to XGBRegressor known as XGBoost which helped me produce the best result in the given time.

Hyper-parameter tuning was performed to find the best parametric value such as tress depth, learning rate etc. for the model.

### Feature Selection
a Plot feature importance was created to visualize the best features using the plot_importance() function.
It was used to drop features which had relatively less importance in our modelling.
and the complete process was repeated for the selected features.

I was able to get achieved a root mean square error (RMSE) value of:  
- 56773.793263 - in my local data-set 
- 59431.14546 - in the Public Leader Board
- 62468.87149 - in the Private Leader Board

