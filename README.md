# Gemstone Price Prediction - Raghu Murugankutty

### Introduction About the Data :

**The dataset** The goal is to predict the `price` of a given diamond (Regression Analysis).

There are 10 independent variables (including `id`):

* `id`: unique identifier of each diamond
* `carat`: Carat (ct.) refers to the unique unit of weight measurement used exclusively to weigh gemstones and diamonds.
* `cut`: Quality of Diamond Cut
* `color`: Color of Diamond
* `clarity`: Diamond clarity is a measure of the purity and rarity of the stone, graded by the visibility of these characteristics under 10-power magnification.
* `depth`: The depth of the diamond is its height (in millimeters) measured from the culet (bottom tip) to the table (flat, top surface)
* `table`: A diamond's table is the facet that can be seen when the stone is viewed face up.
* `x` : Diamond X dimension
* `y` : Diamond Y dimension
* `x` : Diamond Z dimension

Target variable:
* `price`: Price of the given Diamond.

Dataset Source Link :
[https://www.kaggle.com/competitions/playground-series-s3e8/data?select=train.csv](https://www.kaggle.com/competitions/playground-series-s3e8/data?select=train.csv)

### It is observed that the categorical variables 'cut', 'color', and 'clarity' are ordinal in nature

### Check this link for details : [American Gem Society](https://www.americangemsociety.org/ags-diamond-grading-system/)

# Azure Deployment Link :

Azure deployment link : (https://gemstonepriceprediction1.azurewebsites.net/)

# Screenshot of UI

<img width="613" alt="image" src="https://github.com/Raghu-murugankutty/gemstonePrediction/assets/41443395/0b397bc4-53a6-44bd-b7fb-74eaacfa9d81">

# Approach for the project 

1. Data Ingestion : 
    * In the Data Ingestion phase the data is first read as CSV. 
    * Then the data is split into training and testing and saved as CSV file.

2. Data Transformation : 
    * In this phase a ColumnTransformer Pipeline is created.
    * For numeric Variables first SimpleImputer is applied with strategy median, then Standard Scaling is performed on numeric data.
    * For categorical Variables SimpleImputer is applied with the most frequent strategy, and then ordinal encoding is performed after this data is scaled with Standard Scaler.
    * This preprocessor is saved as a pickle file.

3. Model Training : 
    * In this phase base model is tested. The best model found was catboost regressor.
    * After this hyperparameter tuning is performed on catboost and knn model.
    * A final VotingRegressor is created which will combine the prediction of catboost, xgboost and knn models.
    * This model is saved as a pickle file.

4. Prediction Pipeline : 
    * This pipeline converts given data into a data frame and has various functions to load pickle files and predict the final results in Python.

5. Flask App creation : 
    * Flask app is created with a User Interface to predict the gemstone prices inside a Web Application.

# Exploratory Data Analysis Notebook

Link : [EDA Notebook](./notebook/1_EDA_Gemstone_price.ipynb)

# Model Training Approach Notebook

Link : [Model Training Notebook](./notebook/2_Model_Training_Gemstone.ipynb)

# Model Interpretation with LIME 

Link : [LIME Interpretation](./notebook/3_Explainability_with_LIME.ipynb)
