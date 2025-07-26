# A3-Codes
In this Repo you will find assignment codes for A3

R 
# Load required libraries 
library(car) 
# Load data 
data <- read.csv("D:\\Data\\NSSO68.csv") 
# Filter for Haryana 
hr_data <- subset(data, state_1 == "HR") 
# Select relevant columns 
subset_data <- hr_data[, c('foodtotal_q', 'MPCE_MRP', 'MPCE_URP', 'Age', 
'Meals_At_Home', 'Possess_ration_card',  
'Education', 'No_of_Meals_per_day')] 
# Impute missing values using column means 
subset_data$MPCE_MRP[is.na(subset_data$MPCE_MRP)] 
mean(subset_data$MPCE_MRP, na.rm = TRUE) 
subset_data$MPCE_URP[is.na(subset_data$MPCE_URP)] 
mean(subset_data$MPCE_URP, na.rm = TRUE) 
<- 
<- 
14 
subset_data$Age[is.na(subset_data$Age)] <- mean(subset_data$Age, na.rm = TRUE) 
subset_data$Meals_At_Home[is.na(subset_data$Meals_At_Home)] 
mean(subset_data$Meals_At_Home, na.rm = TRUE) 
subset_data$Possess_ration_card[is.na(subset_data$Possess_ration_card)] 
mean(subset_data$Possess_ration_card, na.rm = TRUE) 
<- 
<- 
subset_data$Education[is.na(subset_data$Education)] <- mean(subset_data$Education, na.rm 
= TRUE) 
# Fit linear regression model 
model <- lm(foodtotal_q ~ MPCE_MRP + Age + Meals_At_Home +  
Possess_ration_card + Education, data = subset_data) 
summary(model) 
# VIF for multicollinearity 
vif(model) 
# Diagnostic plots 
par(mfrow = c(2, 2)) 
plot(model) 
b) # Load Required Libraries 
library(dplyr) 
library(readxl) 
install.packages("ggplot2") 
library(ggplot2) 
15 
# STEP 1: Load Datasets 
ball_by_ball 
<- 
read.csv("D://Data//IPL_ball_by_ball_updated 
stringsAsFactors = FALSE) 
salaries <- read_excel("D://Data//IPL SALARIES 2024.xlsx") 
# STEP 2: Filter Ball-by-Ball Data for Shivam Dube (2022–2024) 
dube_perf <- ball_by_ball %>% 
filter(Striker == "S Dube", Season %in% c(2022, 2023, 2024)) 
# STEP 3: Aggregate Performance by Season 
dube_stats <- dube_perf %>% 
group_by(Season) %>% 
summarise( 
Runs = sum(runs_scored, na.rm = TRUE), 
Matches = n_distinct(Match.id)  # backticks fix the issue 
) 
# STEP 4: Use known salaries (in ₹ lakhs) 
dube_salary_all <- data.frame( 
Season = c(2022, 2023, 2024), 
Salary_Rs = c(400, 400, 400)  # From your confirmation 
) 
# Ensure both Season columns are numeric 
dube_stats$Season <- as.numeric(dube_stats$Season) 
till 
2024.csv", 
dube_salary_all$Season <- as.numeric(dube_salary_all$Season) 
16 
# Now join 
dube_combined <- left_join(dube_stats, dube_salary_all, by = "Season") 
# STEP 5: Merge Performance and Salary Data 
dube_combined <- left_join(dube_stats, dube_salary_all, by = "Season") 
# STEP 6: Fit Regression Model (Salary ~ Runs + Matches) 
model <- lm(Salary_Rs ~ Runs + Matches, data = dube_combined) 
summary(model) 
# STEP 7: Predict Salary 
dube_combined$Predicted_Salary <- predict(model) 
# STEP 8: Plot Actual vs Predicted Salary 
ggplot(dube_combined, aes(x = Season)) + 
geom_line(aes(y = Salary_Rs, color = "Actual"), size = 1.2) + 
geom_point(aes(y = Salary_Rs, color = "Actual"), size = 3) + 
geom_line(aes(y = Predicted_Salary, color = "Predicted"), size = 1.2, linetype = "dashed") + 
geom_point(aes(y = Predicted_Salary, color = "Predicted"), size = 3, shape = 17) + 
scale_color_manual(values = c("Actual" = "blue", "Predicted" = "red")) + 
labs( 
title = "Shivam Dube: Actual vs Predicted Salary (₹ Lakhs)", 
x = "IPL Season", 
17 
y = "Salary (₹ Lakhs)", 
color = "Legend" 
) + 
theme_minimal() 
# Load libraries 
library(dplyr) 
library(readxl) 
# STEP 1: Load both datasets 
ball_by_ball <- read.csv("D:/Data/IPL_ball_by_ball_updated till 2024.csv") 
salaries <- read_excel("D:/Data/IPL SALARIES 2024.xlsx") 
# STEP 2: Filter S Dube from ball-by-ball data (batting performance) 
dube_perf <- ball_by_ball %>% 
filter(Striker == "S Dube", Season %in% c(2022, 2023, 2024)) 
# STEP 3: Aggregate performance by season 
dube_stats <- dube_perf %>% 
group_by(Season) %>% 
summarise( 
Runs = sum(Runs, na.rm = TRUE), 
Matches = n_distinct(Match_ID) 
) 
18 
# STEP 4: Filter S Dube’s salary details 
dube_salary <- salaries %>% 
filter(Name == "S Dube", Season %in% c(2022, 2023, 2024)) %>% 
select(Season, Salary) 
# STEP 5: Merge salary and performance data 
dube_combined <- left_join(dube_stats, dube_salary, by = "Season") 
# STEP 6: Fit regression model: Salary ~ Runs + Matches 
model <- lm(Salary ~ Runs + Matches, data = dube_combined) 
summary(model) 
# STEP 7: Predict salary and plot comparison 
dube_combined$Predicted_Salary <- predict(model) 
# STEP 8: Plot actual vs predicted salary 
plot(dube_combined$Season, dube_combined$Salary, type = "b", col = "blue", 
ylim = range(c(dube_combined$Salary, dube_combined$Predicted_Salary)), 
xlab = "Season", ylab = "Salary (₹)", main = "S Dube: Actual vs Predicted Salary") 
lines(dube_combined$Season, dube_combined$Predicted_Salary, type = "b", col = "red") 
legend("topright", legend = c("Actual Salary", "Predicted Salary"), col = c("blue", "red"), lty 
= 1) 
Python: 
import pandas as pd 
import statsmodels.api as sm 
19 
from statsmodels.stats.outliers_influence import variance_inflation_factor 
import seaborn as sns 
import matplotlib.pyplot as plt 
# Load data 
df = pd.read_csv("NSSO68.csv") 
df = df[df["state_1"] == "HR"] 
# Select relevant features 
cols = ['foodtotal_q', 'MPCE_MRP', 'Age', 'Meals_At_Home', 'Possess_ration_card', 
'Education'] 
data = df[cols].copy() 
# Impute missing values 
for col in cols: 
data[col].fillna(data[col].mean(), inplace=True) 
# Regression 
X = sm.add_constant(data[['MPCE_MRP', 'Age', 'Meals_At_Home', 'Possess_ration_card', 
'Education']]) 
y = data['foodtotal_q'] 
model = sm.OLS(y, X).fit() 
print(model.summary()) 
# Import necessary libraries 
import pandas as pd 
20 
import matplotlib.pyplot as plt 
import seaborn as sns 
import statsmodels.api as sm 
# STEP 1: Load the datasets 
ball_by_ball = pd.read_csv("D:/Data/IPL_ball_by_ball_updated till 2024.csv") 
salaries = pd.read_excel("D:/Data/IPL SALARIES 2024.xlsx") 
# STEP 2: Filter data for Shivam Dube (2021–2024) 
dube_perf = ball_by_ball[(ball_by_ball['Striker'] == 'S Dube') &  
(ball_by_ball['Season'].isin([2021, 2022, 2023, 2024]))] 
# STEP 3: Aggregate performance stats 
dube_stats = dube_perf.groupby('Season').agg({ 
'runs_scored': 'sum', 
'Match.id': pd.Series.nunique 
}).reset_index().rename(columns={'runs_scored': 'Runs', 'Match.id': 'Matches'}) 
# STEP 4: Prepare salary data 
dube_salary = pd.DataFrame({ 
'Season': [2021, 2022, 2023, 2024], 
'Salary_Rs': [440, 400, 400, 400]  # in ₹ lakhs 
}) 
21 
# STEP 5: Merge stats and salary 
dube_combined = pd.merge(dube_stats, dube_salary, on='Season') 
# STEP 6: Regression model (Salary ~ Runs + Matches) 
X = dube_combined[['Runs', 'Matches']] 
X = sm.add_constant(X)  # add intercept 
y = dube_combined['Salary_Rs'] 
model = sm.OLS(y, X).fit() 
print(model.summary()) 
# STEP 7: Predict salary 
dube_combined['Predicted_Salary'] = model.predict(X) 
# STEP 8: Plot Actual vs Predicted Salary 
plt.figure(figsize=(10, 6)) 
sns.lineplot(data=dube_combined, x='Season', y='Salary_Rs', marker='o', label='Actual', 
linewidth=2) 
sns.lineplot(data=dube_combined, 
x='Season', 
label='Predicted', linestyle='--', color='red', linewidth=2) 
y='Predicted_Salary', 
plt.title("Shivam Dube: Actual vs Predicted IPL Salary (₹ Lakhs)") 
plt.xlabel("IPL Season") 
plt.ylabel("Salary (₹ Lakhs)") 
plt.legend() 
marker='s', 
22 
plt.grid(True) 
plt.tight_layout() 
plt.show() 
