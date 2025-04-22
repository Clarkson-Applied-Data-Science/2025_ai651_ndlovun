# Predicting EPL Soccer Player Market Value Using Machine Learning Models

# Introduction
The current subjective methods for determining soccer player value lead to inefficienct player recruitment, inequitable salary negotiations, and suboptimal contract offers for soccer players, hence the need to bridge the gap.

### Overall Goal
To analyze the factors that influence a soccer player's market value using FIFA 2022 data and develop predictive models to estimate these attributes based on key player characteristics based on the top 10 rated players.

### Objectives
1.	Explore the relationships between a player’s key attributes and their Market Value.
2.	Using supervised learnin techniques to develop predictive models to estimate player wages and overall ratings based on certain player attributes (e.g. age, position, potential, and skill moves). 
3.	Validate the models by assessing their performance and selecting the best-performing model based on evaluation metrics (like R-squared, Mean Absolute Error (MAE), and Mean Squared Error (MSE)).
4.	Provide actionable insights and recommendations that can assist soccer clubs in making informed decisions about player recruitment, salary negotiations, and contract offers.

## Data Source
Source of the Data: https://www.kaggle.com/datasets/bryanb/fifa-player-stats-database?select=FIFA22_official_data.csv   
Year: 2022
Structure:  1000R * 11 C
168 Nationalities represented
16 089 Unique players represented

## Variables
Train a regression model on player attributes (independent variables) to predict wages (dependent variables).
Use feature engineering to extract meaningful insights (e.g., impact of position, league, skill rating).
Validate against real-world transfer market data (e.g., Transfermarkt, soccer clubs financial reports).


### Justification of data choice and period
While more recent data might offer some advantages, the 2022 dataset proved to provide a strong foundation for achieving the project's objectives of exploring relationships, developing predictive models, and providing actionable insights for football because of the vast attributes it contained.


## Project Plan
Data Cleaning > Data Pre-Processing > Exploratory Analysis > Feature Engineering (PCA) > Model Training and Building > Model Evaluation > Model Selection

### Data Cleaning
![image](https://github.com/user-attachments/assets/ecc1da78-0adb-403e-b6ea-cd5c8bf371f1)

### Feature Engineering
-Assigning age-group for each age.
-Calculating age-to-potential ratio to identify undervalued young players

### Data Pre-Processing
-One Hot-encoding of categorical variables (Nationality, Club, and Position).
-Normalizing data as below:

![image](https://github.com/user-attachments/assets/c86beea0-4e8f-4e3c-81b7-d2bcb3e4389c)

![image](https://github.com/user-attachments/assets/6ab2e3c0-366b-4d5a-b7d0-8905462034c9)


### Exploratory Analysis

![image](https://github.com/user-attachments/assets/57683155-3951-4e6f-bf56-02e8d388d6c9)

Wages range from a few hundred € to over €500K/week
Most players cluster at the lower end of value/wage

![image](https://github.com/user-attachments/assets/fd339684-3131-450d-adc4-5a8326869949)

![image](https://github.com/user-attachments/assets/19cdc0cf-faa4-4d13-882d-1d864538c5b4)

![image](https://github.com/user-attachments/assets/06084b62-c40a-485e-bc48-a52c3e22f8bd)

![image](https://github.com/user-attachments/assets/1f003b7c-ed7a-4fb4-af8c-23afbfe24190)



![Corr-Matrx](https://github.com/user-attachments/assets/0b65f0a3-159a-41b4-8554-8c284fa4b296)

-Positioning is a key feature in the dataset and shows a strong correlation with various other attributes such as Finishing, Dribbling, and Longshots.
-Agility is another important factor, which is closely linked to Balance, Sprint Speed, and Acceleration. 

![image](https://github.com/user-attachments/assets/6f2660bd-a840-4a1e-984f-4301aaa7f542)

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
![image](https://github.com/user-attachments/assets/95cdf421-44a2-4533-9ee9-561c5ff47288)
SVM perfomed best upon initial evaluation


## Residual Plots
-We perform residual analysis to establish how well our model fits the data by analyzing the residuals as below:
![image](https://github.com/user-attachments/assets/f1612a92-10e7-41a5-a076-66279eda7ab0)

-We observe that Random Forest and XGBoost have the best performing models 

## Model Selection
-Since the MSE for Random Forest performed better, we proceed with selecting it as our best model.

-We establish which variable is most important as below:
![image](https://github.com/user-attachments/assets/0dffd696-851e-4c00-8f6d-d6cdc2eb3310)


Our model for this data is:
![image](https://github.com/user-attachments/assets/ba340fc3-bda5-4c4c-ab1e-246b34a34c9d)


# Future Work
-Experiment with neural networks for capturing complex interactions

-Include temporal evolution of player ratings from multi-year data

-Source and use a verified dataset


# Conclusion

-The models accurately predicted player market value with Random Forest performing best.

-Features such as Best Overall Rating, Overall Rating and  Potential were found to be the strongest predictors of market value.

-The modeling framework and feature importance analysis can be adapted for real-world scouting and valuation scenarios for soccer players.



























