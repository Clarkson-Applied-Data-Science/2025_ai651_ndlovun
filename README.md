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

![image](https://github.com/user-attachments/assets/57683155-3951-4e6f-bf56-02e8d388d6c9)

Wages range from a few hundred € to over €500K/week
Most players cluster at the lower end of value/wage

![image](https://github.com/user-attachments/assets/fd339684-3131-450d-adc4-5a8326869949)

![image](https://github.com/user-attachments/assets/19cdc0cf-faa4-4d13-882d-1d864538c5b4)

![image](https://github.com/user-attachments/assets/06084b62-c40a-485e-bc48-a52c3e22f8bd)

![image](https://github.com/user-attachments/assets/1f003b7c-ed7a-4fb4-af8c-23afbfe24190)

![image](https://github.com/user-attachments/assets/6f2660bd-a840-4a1e-984f-4301aaa7f542)


## Correlation 

### Correlation Matrix


### Analysing top Players by Strength
![radar](https://github.com/user-attachments/assets/87ebb238-3f89-4247-9ee4-64162f2416ff)

-The radar chart visually highlights the strengths and weaknesses of each player based on their attributes.
-Messi and Neymar Jr dominate in technical skills (Dribbling, Finishing, Agility).
-Lewandowski is the strongest physically, making him an ideal target striker.
-De Bruyne excels in passing, making him a top playmaker.
-Oblak, as a goalkeeper, has significantly lower ratings in these outfield skills, reinforcing his specialized role.


# Principal Component Analysis
![image](https://github.com/user-attachments/assets/bc7936d7-5406-4669-8949-eb71e76debec)

![image](https://github.com/user-attachments/assets/0ff31dd4-cf76-45f4-8ec9-76a64aae5c02)

![image](https://github.com/user-attachments/assets/5fc27a27-de35-4d50-bb50-7c1bb8341569)


# Clustering

![image](https://github.com/user-attachments/assets/10ec0fb4-ecd7-4762-a912-b7b02d859512)

![image](https://github.com/user-attachments/assets/ebbe0a7e-f2de-4523-9a1f-9a31007a927f)


# Model Training

## Train/Test Split Criteria

-80% of the data was used for training the model

-20% of the data was used for testing the model

-The dataset was divided into 80/20 train-test split using stratified sampling to maintain the distribution of the target variable (Value). This approach ensured that the training set was large enough to learn the underlying patterns, while the test set provided an unbiased evaluation of the model’s performance.


![image](https://github.com/user-attachments/assets/95cdf421-44a2-4533-9ee9-561c5ff47288)
SVM perfomed best upon initial evaluation


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

![Screenshot 2025-04-22 015746](https://github.com/user-attachments/assets/b96ceaed-aa2d-427b-8aaa-537ad2a404d8)



# Future Work
-Experiment with neural networks for capturing complex interactions

-Include temporal evolution of player ratings from multi-year data

-Source and use a verified dataset


# Conclusion

-The models accurately predicted player market value with Random Forest performing best.

-Features such as Best Overall Rating, Overall Rating and  Potential were found to be the strongest predictors of market value.

-The modeling framework and feature importance analysis can be adapted for real-world scouting and valuation scenarios for soccer players.



























