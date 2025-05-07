# Predicting EPL Soccer Player Wages Using Machine Learning Models

# Introduction
Player wage determination in soccer involves factors like performance metrics, marketability, and positional demand. This project leverages FIFA 2022 player data to build a predictive model for wages, providing insights into key attributes influencing earnings.

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

Wage is most strongly influenced by technical and attacking attributes, with physical and defensive skills playing a secondary role. The strongest relationships are among technical attributes themselves.

### Analysing top Players by Strength

![radar](https://github.com/user-attachments/assets/666b0429-4a5c-400f-8447-7b51fa956f70)
-The radar chart visually highlights the strengths and weaknesses of each player based on their attributes.
-Messi and Neymar Jr dominate in technical skills (Dribbling, Finishing, Agility).
-Lewandowski is the strongest physically, making him an ideal target striker.
-De Bruyne excels in passing, making him a top playmaker.
-Oblak, as a goalkeeper, has significantly lower ratings in these outfield skills, reinforcing his specialized role.


# Principal Component Analysis

## Train/Test Split Criteria

-80% of the data was used for training the model

-20% of the data was used for testing the model

-The dataset was divided into 80/20 train-test split using stratified sampling to maintain the distribution of the target variable (Wages). This approach ensured that the training set was large enough to learn the underlying patterns, while the test set provided an unbiased evaluation of the model’s performance.


### Scree Plot
![scree](https://github.com/user-attachments/assets/67033032-1892-4636-a37d-910e631ab671)
The PCA scree plot indicates that player data is complex, with no single feature or component capturing most of the variance.

### Biplot
![biplot](https://github.com/user-attachments/assets/085c1685-d33d-42c3-8a90-caa39f519609)
The biplot shows that technical and attacking skills (Dribbling, SprintSpeed, Crossing) are the most important for explaining differences among players in this dataset. No single attribute dominates, and the variance is spread across several features, highlighting the complexity and multidimensionality of player performance data.

### 
Player Attribute	PC1	PC2	Total Contribution
Best Overall Rating	0.07408	0.697478	49%
Dribbling	0.613434	-0.078367	38%
Crossing	0.20129	-0.518911	31%
Values	0.545976	0.100749	31%
SprintSpeed	0.516042	0.187035	30%
Positioning	0.115341	-0.439297	21%
![image](https://github.com/user-attachments/assets/dd7743c3-8545-4cac-8a5e-5fe080a400af)

This analysis reveals that technical skills (Dribbling) and player ratings strongly distinguish players in different ways along the principal components, with physical attributes (SprintSpeed) and market Values also playing significant roles in player differentiation.

# Model Training




## Residual Plots
-We perform residual analysis to establish how well our model fits the data by analyzing the residuals as below:
![image](https://github.com/user-attachments/assets/f1612a92-10e7-41a5-a076-66279eda7ab0)

-We observe that Random Forest and XGBoost have the best performing models 

## Hyperparameter Selection
-A K-Fold Cross-Validation approach (K=5) was used to ensure robust model evaluation and minimize overfitting.
-Additionally, feature importance analysis was conducted to identify the most influential predictors of Wage and Value.

## Model Selection
-Since the MSE for Random Forest performed better, we proceeded with selecting it as our best model.

-We establish which variable is most important as below:
![image](https://github.com/user-attachments/assets/0dffd696-851e-4c00-8f6d-d6cdc2eb3310)


Our model for this data is:
![image](https://github.com/user-attachments/assets/ba340fc3-bda5-4c4c-ab1e-246b34a34c9d)

### Synthesized Prediction Example



# Key findings 

### Feature Selection & Transformation:
We focused on top features such as ball control, dribbling, sprint speed, and reactions, alongside a cluster variable representing player categories. After transforming the target variable (wage) with a log transformation, we experimented with different models to capture the relationships between these features and wages.

### Modeling Attempts:
We explored several machine learning models, including:
Linear Regression: Basic but interpretable, providing a baseline for the prediction.
Random Forest & XGBoost: Powerful tree-based models that allowed for better capture of non-linear relationships.
Ensemble Methods (Stacking & Voting): We attempted to combine multiple models, but the results didn’t significantly outperform the best individual models. This suggests that model diversity wasn’t enough to overcome the challenges posed by the data.

### Challenges:
Model Accuracy: Despite using advanced techniques like XGBoost and stacking, the models struggled to predict wages accurately, likely due to factors such as extreme outliers and lack of feature diversity.
Negative R²: The negative R² in many of the models indicated that the models were not performing better than a simple mean-based baseline. This emphasizes the need for further feature engineering and data refinement.

### Potential Improvements:
Feature Engineering: Including more relevant features such as age, overall rating, international reputation, and club context could improve predictions.
Group-Specific Models: Dividing the dataset by player position or cluster might reveal more accurate patterns within specific player categories.
Handling Outliers: Using robust loss functions or transforming the target variable more effectively could help in dealing with outliers and extreme wage values.

### Next Steps:
Future work should focus on deeper analysis of the dataset’s distribution and feature relationships. Additionally, experimenting with models tailored to specific player roles (e.g., forwards, midfielders) and incorporating new player-specific metadata would help refine the model and improve predictions.

### Conclusion:
In this project, we have successfully built machine learning models to predict football player wages, based on various attributes such as player statistics, club data, and performance metrics. XG-Boost was the favorable model because of its ability to handle non-linear relationships. Despite encountering challenges in improving model accuracy, we gained valuable insights into the nature of player wage predictions and the factors influencing them.This project demonstrates the challenges of predicting football player wages due to the complexity of the data and the high variance in wage distribution. While the models tested provide a starting point, further refinement is necessary to enhance predictive power. The insights gained here can inform future modeling efforts, with an emphasis on feature engineering and dataset segmentation.
























