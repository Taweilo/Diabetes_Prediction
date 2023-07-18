# ⚡⚡ Diabetes_Prediction 🩺🩺
![Python version](https://img.shields.io/badge/Python%20version-3.10%2B-lightgrey)
![GitHub last commit](https://img.shields.io/github/last-commit/Taweilo/Red_Wine_Quality_Classification_Model)
![GitHub repo size](https://img.shields.io/github/repo-size/Taweilo/Red_Wine_Quality_Classification_Model)
![Type of ML](https://img.shields.io/badge/Type%20of%20ML-Binary%20Classification-red)
![License](https://img.shields.io/badge/License-MIT-green)

Badge [source](https://shields.io/)

 <img src="https://meddo.in/blog/wp-content/uploads/2020/09/onpage_Book-diagnostic-test-online-1024x575.jpeg" width="1000" height="450">
This project will follow the BA workflow to tackle red wine business issues using data mining techniques. A red wine retailer imports wine and sells it to customers. Thus, it needs to predict the wine quality for the business when importing. Via machine learning techniques, we can classify and predict the quality in advance. By evaluating the model performance, we can make better decisions and thus maximize profits in advance.
Overall, the Radom Forest classification model maximizes profits the most. Considering the non-ml and ml model, ml model always performs better than the non-ml model under different true positive rate conditions. 

### Repository structure

```
├── Image
│   ├── business value.jpg                        <- image used in the README.
│   ├── data statistics.jpg                       <- data statistics summary used in the README.
│   ├── evaluation.jpg                            <- model summary table used in the README.
│   ├── heatmap.jpg                               <- heatmap image used in the README.
│   ├── quality distribution.jpg                  <- quality distribution image used in the README.                             
│
├── Red Wine Classification Project.ipynb         <- code
├── WineQT.csv                                    <- dataset
```

## 1. Business Understanding

## 2. Data Understanding 
The Sales & Media Spend data was loaded via Colab. The dataset is from Kaggle: https://www.kaggle.com/datasets/harrimansaragih/dummy-advertising-and-sales-data (also please see Dummy Data HSS.csv attached). Basic data analysis was performed to identify the shape of data, get column names, find missing values, and generate descriptive statistics. The Pearson correlation matrix was calculated to find the pairwise correlation of the columns in the data. All columns in the data are visually represented as histograms. A correlation heatmap figure was generated to represent the correlation matrix.

* Original Dataset
 <img src="https://github.com/Taweilo/Sales_Prediction_from_Media_Spend/blob/main/Image/original%20dataset.jpg" width="400">
 
| Name | Modeling Role | Measurement Level| Description|
| ---- | ------------- | ---------------- | ---------- |
| **TV** | input | float | TV promotion budget (in million) |
| **Radio** | input | float | Radio promotion budget (in million) |
| **Social Media** | input | float | Social Media promotion budget (in million) |
| **Influencer** | input | Object | Type of Influencers |
| **Sales** | target | float | Sales in million |

* Statistics
 <img src="https://github.com/Taweilo/Sales_Prediction_from_Media_Spend/blob/main/Image/statistics.jpg" width="300">
 
* Heatmap
 <img src="https://github.com/Taweilo/Sales_Prediction_from_Media_Spend/blob/main/Image/heatmap.jpg" width="300">

* Pairplot
 <img src="https://github.com/Taweilo/Sales_Prediction_from_Media_Spend/blob/main/Image/pairplot.jpg" width="400">
 
## 3. Data Preparation 
1. Define variables (X and y)
2. Get dummy variables 
3. Split the data into train and test datasets <br>
   train: 2727 data<br>
   test:  1819 data<br>
  
## 4. Modeling   
   <img src="https://global-uploads.webflow.com/5d3ec351b1eba4332d213004/6026b7494be6481c635b0f84_axkJOrqGKDEK3a6U4mf8fRr5t0FKQIVvbJhDFVFyINVnpkEcv54vLydIg4BOcmyl-cSRakxD3L5-JR8GXMuNU67F5eTXD7ZpL6-MEekv50k8lkEMvIT8ludrUxWOjhAZ8i1_-7eY.png" width="400">
   
The trade-off between interpretability and performance of these ML models. Highly interpretable algorithms such as linear regression, are often inaccurate because of high bias but low variance. Very accurate DNNs are a classic example of black boxes, with low bias but high variance. However, the model performance is highly associated with the data type. Several models were included for further evaluation:

* SVM
* Logistic regression
* KNN
* Decision Tree
* Random Forest
* Random Forest with Tuning
* Adaboost

  
## 5. Evaluation
 <img src="https://github.com/Taweilo/Sales_Prediction_from_Media_Spend/blob/main/Image/evaluation.jpg" width="500" >
 
## 6. Recommendation
### Inferencing
The linear model has demonstrated superior performance, making it a compelling candidate for a detailed analysis. Its simplicity and interpretability allow us to draw meaningful inferences for the entire population. The below summary table shows the R-square, Global F, coefficient, and p-value of the model:

 <img src="https://github.com/Taweilo/Sales_Prediction_from_Media_Spend/blob/main/Image/lr%20summary%20table.jpg" width="500">

* Adjusted R-square: 0.999 indicates that the model can explain approximately 99.9% of the variation in the dependent variable based on the independent variables included in the model. 
* p-value of Global F: 0.00 means statistical significance, so we are reasonably sure at least one variable is not 0. There is a relationship between independent and dependent variables in the population. 
* Model: Sales = -0.204 + 3.563 * (TV spend) + 0.007 * (Radio spend) + (-0.043) * (Social media spend) <br>
                 + 0.057 * (Influencer_Mega) <br>
                 + (-0.047) * (Influencer_Micro) <br>
                 + (-0.069) * (Influencer_Nano) <br><br>
**Influence_Macro is the reference group.** 

* p-value: Only the variable TV is statistically significant suggesting that we are reasonably sure the coefficient of TV is not 0 in the population. 

### Deployment
* code to predict test data  
```
y_pred = linear_regressor.predict(X_test)
```
* Scatter plot of Prediction and Test data
 <img src="https://github.com/Taweilo/Sales_Prediction_from_Media_Spend/blob/main/Image/y_pred%20vs%20y_test.jpg" width="500">
 
### Limitation
1. The R-square is extremely high, only representing this dataset. It cannot suggest either the different marketing projects in this company, the other company's management, or the real situation. Different datasets would change the coefficient of the linear model, so the inferencing analysis is effective in this project. 
2. This model did not consider the interaction between the variables. The synergy effect could happen under a specific circumstance. Media channels could interact with each other. 
3. Even though the linear model explained the best, a further linear assumption can be checked: Homoscedasticity, Multicollinearity, Outlier, and Non-Constant Variance, etc.
