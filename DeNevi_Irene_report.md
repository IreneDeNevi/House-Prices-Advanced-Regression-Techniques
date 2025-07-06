## Report
**Kaggle username** : irenedenevi99 \
**Number in a team** : 1 \
**Position** : 1427

![Submission](submission.png)
![Leaderboard](Leaderboard.png)

### Detailed Description of the Data Used

The dataset used in this analysis is the "House Prices: Advanced Regression Techniques" dataset from Kaggle. I chose it because I found it more challenging than the famous "Boston Housing Dataset", with more features and more data to work with. Also, it is perfect for practice at the end of an ML Fundamentals class, as you can do EDA, feature engineering, and try to see how different
models learn from this kind of dataset, including more dvanced regression techniques like random forest and gradient boosting.
Having a data_description.txt attached is a plus, so in conclusion this dataset is the perfect playground to hone ML skills before trying out a featured competition.

The dataset consists of two main files: a training set and a test set. 

- **Training Set**: Contains 1460 observations with 81 features, including both numerical and categorical variables. The target variable is `SalePrice`, which represents the sale price of the houses. Other features include:
  - **Numerical Features**: These include continuous variables such as `LotArea`, `YearBuilt`, `TotalBsmtSF`, etc., which provide quantitative information about the properties.
  - **Categorical Features**: These include variables like `Neighborhood`, `HouseStyle`, and `OverallQual`, which represent qualitative attributes of the houses.

- **Test Set**: Contains 1459 observations with the same features as the training set, except for the target variable `SalePrice`, which is not provided. This set is used to evaluate the model's performance on unseen data.

### Approach Taken to Develop the Model

1. **Data Loading and Exploration**: The data was loaded using Pandas, and basic exploratory data analysis (EDA) was performed to understand the structure of the dataset, identify missing values, and visualize distributions of features.

2. **Data Preprocessing**:
   - **Handling Missing Values**: Columns with more than 20% missing values were dropped, and remaining missing values were filled using the mean for numerical features and the mode for categorical features.
   - **Feature Engineering**: New features were created to enhance the model's predictive power, such as `TotalSF` (total square footage) and `TotalBathrooms`.
   - **Encoding Categorical Variables**: Categorical features were transformed into numerical format using Label Encoding.
   - **Scaling Numerical Features**: Numerical features were standardized using `StandardScaler` to ensure they are on the same scale.

3. **Model Training and Evaluation**:
   - The dataset was split into training and validation sets.
   - Multiple regression models were trained, including Linear Regression, Ridge, Lasso, ElasticNet, Random Forest, and XGBoost.
   - Hyperparameter tuning was performed using GridSearchCV to find the best parameters for each model.
   - Model performance was evaluated using metrics such as RMSE and R² score, and a function was implemented to plot the learning curves for underfitting or overfitting.

4. **Model Comparison and Selection**: The results of the models were compared using visualizations, and the best-performing model was selected based on validation RMSE.

5. **Final Predictions**: The best model was used to make predictions on the test set, and the results were saved in a submission file.

### Reflections on the Modeling Process
1. **Data Quality**: The quality of the data significantly impacted the model's performance. Handling missing values and outliers was crucial to ensuring that the models could learn effectively from the data.

2. **Feature Engineering**: Creating new features like TotalSF (total square footage) and TotalBathrooms was made to improve the model's ability to capture patterns in the data.

3. **Model Selection**: The choice of using multiple models was driven by the desire to compare different types of models, as discussed in class. Starting with the standard Linear Regression and gradually progressing to more complex models like Ridge, Lasso, ElasticNet, Random Forest, and XGBoost allowed for a comprehensive comparison. This approach is particularly relevant for competitive platforms like Kaggle, where understanding and comparing various models is important in terms of performance.


4. **Iterative Process**: The modeling process was iterative, requiring multiple rounds of tuning and evaluation.

Here a description of the parameters used for each model:
   1. Linear Regression:
   - fit_intercept: True
   The model is fitted with an intercept term for capturing the relationship between the features and the target variable. 
   2. Ridge: 
   - alpha: [0.1, 1.0, 10.0]
   - fit_intercept: [True, False]
   The Ridge model is regularized with an alpha parameter that controls the strength of the regularization. The fit_intercept parameter determines whether the model includes an intercept term. The values [0.1, 1.0, 10.0] were chosen to explore a range of regularization strengths.
   3. Lasso:
   - alpha: [0.1, 1.0, 10.0]
   - fit_intercept: [True, False]
   The Lasso model is regularized with an alpha parameter that controls the strength of the regularization. The fit_intercept parameter determines whether the model includes an intercept term. The values [0.1, 1.0, 10.0] were chosen to explore a range of regularization strengths and the same values were used for the Ridge model to maintain consistency and allow for a direct comparison between the two models.
   4. ElasticNet:
   - alpha: [0.1, 1.0, 10.0]
   - l1_ratio: [0.2, 0.5, 0.8]
   - fit_intercept: [True, False]
   5. The ElasticNet model:
   - alpha: [0.1, 1.0, 10.0]
   - l1_ratio: [0.2, 0.5, 0.8]
   - fit_intercept: [True, False]
   It is regularized with an alpha parameter that controls the strength of the regularization. The l1_ratio parameter controls the mix between L1 and L2 regularization. The fit_intercept parameter determines whether the model includes an intercept term. The values [0.1, 1.0, 10.0] were chosen to explore a range of regularization strengths, and [0.2, 0.5, 0.8] were chosen to explore different proportions of balance between L1 and L2 regularization.
   6. Random Forest:
   - n_estimators: [50, 100, 200]
   - max_depth: [5, 10, 15]
   - min_samples_split: [2, 5]
   - min_samples_leaf: [1, 2]
   The parameters were chosen to provide a balance between model complexity and performance. The values for n_estimators were set to [50, 100, 200] to explore the effect of tree count, while max_depth, min_samples_split, and min_samples_leaf were varied to control tree growth and prevent overfitting.
   7. XGBoost:
   - n_estimators: [50, 100, 200]
   - max_depth: [5, 10, 15]
   - learning_rate: [0.01, 0.1, 0.2]
   - gamma: [0, 0.1, 0.2]
   - subsample: [0.5, 0.75, 1]
   - colsample_bytree: [0.5, 0.75, 1]
   It is a gradient boosting model and generally used in this competition. The chosen values for n_estimators were [500, 1000] to explore a range of boosting rounds. The learning_rate values [0.01, 0.1] were selected to balance convergence speed and model performance. The max_depth, subsample, and colsample_bytree parameters were included to control model complexity and prevent overfitting.

### Conclusion

The final model, XGBoost, based on the RMSE metric, is the best model for this dataset.

As the learning curve shows, the gap between the training score and validation score narrows as the training size increases, suggesting that the model is generalizing better and reducing overfitting. However, the training score remains higher than the validation score, implying that the model could still be slightly overfitting.
The model with futher tuning or regularization techiniques could narrow that gap.