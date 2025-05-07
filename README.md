# Predicting EPL Soccer Player Wages Using Machine Learning Models

# Introduction
This project explores the use of machine learning to predict football player wages based on player attributes and performance data. By building and evaluating predictive models, it aims to understand how well on-field statistics can explain wage differences and highlights both the potential and the challenges of using data-driven approaches for salary prediction in professional football.

### Overall Goal
To analyze the factors that influence a soccer player's wages using FIFA 2022 data.

### Objectives
1. Identify attributes correlated with wage.
2. Develop machine learning models to predict wages.
3. Evaluate model performance and optimize hyperparameters.

### Study Significance
This study offers a framework for objective wage valuation, aiding stakeholders in financial planning and talent assessment.
   
## Data Source
Source of the Data: https://www.kaggle.com/datasets/bryanb/fifa-player-stats-database?select=FIFA22_official_data.csv   
Year: 2022
Structure:  1000R * 11 C

## Variables
Train a regression model on player attributes (independent variables) to predict market value (dependent variables).

### Justification of data choice and period
While more recent data might offer some advantages, the 2022 dataset proved to provide a strong foundation for achieving the project's objectives of exploring relationships, developing predictive models, and providing actionable insights for football because of the vast attributes it contained.


## Project Plan
Data Cleaning > Data Pre-Processing > Exploratory Analysis > Feature Engineering (PCA) > Model Training and Building > Model Evaluation > Model Selection

### Data Cleaning and Pre-Processing
Removed columns with >50% missing values (e.g., DefensiveAwareness, GKReflexes).
Imputed remaining missing values using mean/mode.
Standardized numeric features 
One-hot encoded categorical variables.

### Feature Engineering
Top Attributes: Positioning, Reactions, BallControl, and Values were retained based on EDA correlations.
Log Transformation: Applied to Values and Wage to address skewness.


### Exploratory Analysis

![age distribution](https://github.com/user-attachments/assets/0b2699dc-fdeb-427f-a0a5-7497634ce56f)

Aging players (>30) are fewer, especially those above 35 years old. This age pattern is consistent with expectations in professional football, where the physical prime and club strategies often center around youth development and performance potential.

![top 10 player positions](https://github.com/user-attachments/assets/e3c8e7b1-3b40-4fc5-af61-9f37d68dfca6)

Subs are the most dorminant player positions.

![image](https://github.com/user-attachments/assets/b6617c70-c89c-4bab-9554-a682dc8ccfcb)

Player wages are highly variable within each position, with a small number of players earning much more than the rest. While median wages are relatively similar, attacking and goalkeeping roles show greater wage variability and more high earners. This reflects the market's premium for standout performers in these positions.

## Correlation 

### Correlation Matrix
![correlation matrix](https://github.com/user-attachments/assets/7bbd4ee8-813e-4ea8-87b1-3408194a58d7)

All correlations with Wage are weak and negative, ranging from about -0.12 to -0.29.

## Establishing the distribution of Wages
![wage distribution](https://github.com/user-attachments/assets/622b17e5-f5f9-4aba-b352-4bf7801530f4)

Football player wages are highly unequal, with most players earning modest amounts and a small elite group earning extremely high wages. This skewed distribution can make wage prediction challenging, as models must account for both the large number of low-wage players and the rare, high-wage outliers

### Analysing top Players by Strength

![radar](https://github.com/user-attachments/assets/666b0429-4a5c-400f-8447-7b51fa956f70)
-The radar chart visually highlights the strengths and weaknesses of each player based on their attributes.
-Messi and Neymar Jr dominate in technical skills (Dribbling, Finishing, Agility).
-Lewandowski is the strongest physically, making him an ideal target striker.
-De Bruyne excels in passing, making him a top playmaker.
-Oblak, as a goalkeeper, has significantly lower ratings in these outfield skills, reinforcing his specialized role.


# Principal Component Analysis

## Train/Test Split Criteria and Scaling

-80% of the data was used for training the model

-20% of the data was used for testing the model

-The dataset was divided into 80/20 train-test split using stratified sampling to maintain the distribution of the target variable (Wages). This approach ensured that the training set was large enough to learn the underlying patterns, while the test set provided an unbiased evaluation of the model’s performance.


## Scree Plot
![scree](https://github.com/user-attachments/assets/67033032-1892-4636-a37d-910e631ab671)
The PCA scree plot indicates that player data is complex, with no single feature or component capturing most of the variance.

## Biplot
![biplot](https://github.com/user-attachments/assets/085c1685-d33d-42c3-8a90-caa39f519609)

The biplot shows that technical and attacking skills (Dribbling, SprintSpeed, Crossing) are the most important for explaining differences among players in this dataset. No single attribute dominates, and the variance is spread across several features, highlighting the complexity and multidimensionality of player performance data.

## Quantifying Features Contributing the highest variance
![image](https://github.com/user-attachments/assets/dd7743c3-8545-4cac-8a5e-5fe080a400af)

This analysis reveals that technical skills (Dribbling) and player ratings strongly distinguish players in different ways along the principal components, with physical attributes (SprintSpeed) and market Values also playing significant roles in player differentiation.

# Model Training and Evaluation
![image](https://github.com/user-attachments/assets/c6aa97ce-319b-437f-8d5b-6454189f64ba)
Lower RMSE indicates better accuracy and higher R² indicates better explanatory power
The ranking from best to worst is:
Random Forest: RMSE = 6815.86, R² = -0.21
XGBoost: RMSE = 7655.01, R² = -0.53
Decision Tree: RMSE = 10745.75, R² = -2.01
However, it's worth noting that all models have negative R² values, suggesting they perform worse than simply using the mean value as a prediction. The Random Forest model still needs improvement, but it's the best option among these three. So we perform Grid Search.


## Hyperparameter Tuning
-Grid Search was applied to ensure robust model evaluation and minimize overfitting.
![image](https://github.com/user-attachments/assets/d4be9d9d-4343-4ac0-9421-92f42e9951f8)

Improvements from hyperparameter tuning were marginal but most significantly XGBoost R² improved from -0.53 to -0.17 hence it became the best model as below:
![model evaluation](https://github.com/user-attachments/assets/e7c4edba-f1d8-4618-8f38-251bd1861e94)



## Evaluation on Test
We performed residual plots to establish how well the models fit the data.

![model diagnostics](https://github.com/user-attachments/assets/5d8d4586-6bbc-44ee-887e-581537c3d61e)
Random Forest and XG-Boost showed better performance as the residuals were more random. However, we choose XG-Boost as the best model since it presented better accuracy upon hypertuning.

# Feature Importance
![feature importance-XG](https://github.com/user-attachments/assets/ee1b92a0-9067-45b2-ab0b-ec8a389f3a64)

The XGBoost model considers technical skills (like ShortPassing, LongShots, Dribbling) and overall player quality (Overall) as the most important factors in predicting wages.

## SHapley Additive exPlanations (SHAP)
We performed SHAP to establish how each feature contributes to the model's prediction.
![SHAP](https://github.com/user-attachments/assets/34e4adc7-3511-436e-8838-8133b1c8606f)

While Overall and SprintSpeed are the most influential, their effects are still moderate, and most features have only a small impact. This suggests that the model finds it difficult to explain wage variation using the available player attributes, aligning with earlier findings of weak predictive power.


## Model Deployment?
While XGBoost is the least poor model, none are viable for deployment. The project should pivot to address data gaps and nonlinear wage determinants rather than incremental tuning.

# Future Work
Future work should focus on expanding the feature set to include off-field and market-related variables, such as club finances, player marketability, and contract details, which are likely to have a stronger influence on wages. Developing position-specific or league-specific models may also improve predictive accuracy so we could consider cluster based models. Additionally, advanced modeling techniques and robust handling of wage outliers could help address the highly skewed wage distribution and improve model reliability. Most importantly, we could use a more verified data source that is not Kaggle.

# Key findings 

## Challenges:
Weak correlation of player features with wages meant gave our model a low predicitive power. Also, the negative R² in the trained models indicated that the models were not performing better than a simple mean-based baseline. This emphasizes the need for further feature engineering and data refinement.

## Potential Improvements:
Feature Engineering: Including more relevant features such as age, overall rating, international reputation, and club context could improve predictions.
Cluster-Specific Models: Dividing the dataset by player position or league might reveal more accurate patterns within specific player categories.
Handling Outliers: Using robust loss functions or transforming the target variable more effectively could help in dealing with outliers and extreme wage values.

## Conclusion:
Although we successfully established the XGBoost as the best model, its low predictive power demonstrates that predicting football player wages using only standard player attributes and performance metrics is highly challenging. The analysis revealed that these features have weak correlations with wages, and even advanced machine learning models like XGBoost and Random Forest failed to achieve meaningful predictive accuracy, as shown by negative R² values. The SHAP analysis further confirmed that no single attribute strongly influences wage predictions, highlighting the complexity and multifactorial nature of wage determination in professional football. To build more accurate wage prediction models, it is essential to incorporate additional data such as market factors, club finances, contract details, and player marketability. Overall, the project underscores the limitations of relying solely on on-field statistics for wage prediction and points toward the need for richer, more comprehensive datasets and modeling approaches. Future work will enhance the model performance by addressing the challenges that were presented by this model






















