# Predicting Soccer Player Wages Using Machine Learning Models

# Introduction
The current subjective methods for determining soccer player value and wages often lead to inefficienct player recruitment, inequitable salary negotiations, and suboptimal contract offers for soccer players, hence the need to bridge the gap.

### Overall Goal
To analyze the factors that influence a soccer player's value and wages using FIFA 2022 data and develop predictive models to estimate these attributes based on key player characteristics based on the top 10 rated players.

### Objectives
1.	Explore the relationships between a player’s key attributes and their Wages.
2.	Using supervised learnin techniques to develop predictive models to estimate player wages and overall ratings based on certain player attributes (e.g. age, position, potential, and skill moves). 
3.	Validate the models by assessing their performance and selecting the best-performing model based on evaluation metrics (like R-squared, Mean Absolute Error (MAE), and Mean Squared Error (MSE)).
4.	Provide actionable insights and recommendations that can assist soccer clubs in making informed decisions about player recruitment, salary negotiations, and contract offers.

## Data Source
Source of the Data: https://www.kaggle.com/datasets/bryanb/fifa-player-stats-database?select=FIFA22_official_data.csv   
Year: 2022
Structure: 16 710R * 65C
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

### Data Pre-Processing

### Exploratory Analysis
![Age Dist](https://github.com/user-attachments/assets/cdd8faea-c15a-4cd5-becf-30dc86db67e2)

-The right-skewedness of the distribution shows that younger individuals dominate the dataset, while older ages are less frequent.
-The median age is 25 years



![Main Effects Plot](https://github.com/user-attachments/assets/5a301ba2-7ae7-46b1-aee4-215b82a9a473)

-There is a significant spike for the CF (Center Forward) position, with wages exceeding €50,000, making it an outlier.
-The RES (Reserve) position has a notably low mean wage, likely because reserves are typically lower-paid players.
-Goalkeepers (GK) and defenders (CB, RCB, LCB, etc.) have more stable and moderate wages.



![Corr-Matrx](https://github.com/user-attachments/assets/0b65f0a3-159a-41b4-8554-8c284fa4b296)

-Positioning is a key feature in the dataset and shows a strong correlation with various other attributes such as Finishing, Dribbling, and Longshots.
-Agility is another important factor, which is closely linked to Balance, Sprint Speed, and Acceleration. 




![radar](https://github.com/user-attachments/assets/87ebb238-3f89-4247-9ee4-64162f2416ff)

-The radar chart visually highlights the strengths and weaknesses of each player based on their attributes.
-Messi and Neymar Jr dominate in technical skills (Dribbling, Finishing, Agility).
-Lewandowski is the strongest physically, making him an ideal target striker.
-De Bruyne excels in passing, making him a top playmaker.
-Oblak, as a goalkeeper, has significantly lower ratings in these outfield skills, reinforcing his specialized role.


# Going Forward
Feature Engineering > One-Hot Encoding: Convert categorical variables like position into numerical form.Log Transformation: Apply to skewed features like wages to handle extreme outliers.

-Model Training and Building > Model Evaluation > Model Selection



# Alternative plan if proposed prediction does not work out
Source and use data for 1 big league for this prediction and recommend it to similar leagues.















