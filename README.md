# Kaggle-Kickstarter-Project-Status-Prediction

The aim of the project is to predict the state of the Kickstarter projects (as 'Successful' and 'Failed') before its actual deadline

## Dataset:
The Dataset provided to us has projects till 2017, starting from 2009.
It is at a project ID level and has 331675 rows (331675 projects).

### Understanding Variables in the Dataset

The dataset has 15 variables including ID. Since ID is the level of the dataset, we can set it as the index of the ata later. Variables like name, currency, deadline, launched date and country as self explanatory. Explanations of some key variables are as follows:

Main_Category: There are 15 main categories for the project. These main categories broadly classify projects based on topic and genre they belong to.

Category: Main Categories are further sub divided in categories to give more general idea of the project. For example, Main Category “Technology” has 15 categories like Gadgets, Web, Apps, Software etc. There are 159 total categories.

Goal: This is the goal amount which the company need to raise to start its project. The goal amount is important variable for company as if it is too high, the project may fail to raise that amount of money and be unsuccessful. If it is too low, then it may reach its goal soon and backers may not be interested to pledge more.

Pledged: This is amount raised by the company through its backers. On Kickstarter, if total amount pledged is lower than goal, then the project is unsuccessful and the start-up company doesn’t receive any fund. If pledged amount is more than the goal, the company is considered successful. The variable “usd pledged” is amount of money raised in US dollars.

Number of Backers: These are number of people who have supported the project by pledging some amount.

## What are the steps followed?
1. EDA and data understanding
2. Feature engineering and manual (heuristic) feature selection
3. Model Building and Predictions
4. Feature Importance evaluation- to get the key drivers

### Models tested
1. Logistic Regression with Grid Search
2. XGBoost
3. Random Forest

## Best model 
### **Best Accuracy**: 
#### first iteration: 68.9 %
#### second iteration: 69.2 %

**Best Model**: XGBoost

**Key Drivers (top 15)**:

The below list has the top 15 features the corresponding importance from XGBoost (**first Iteration**)
1. duration-0.111218   %duration is the difference between deadline and launch date
2. participants-0.091028 %number of projects launched in the same year-quarter with the same goal bucket in the same category
3. avg_success_rate-0.084386 %probability of success of project on the basis of pledge (pledge per backer) and goal amount of similar projects in the project year
4. launched_month-0.075908
5. avg_ppb-0.070271 #average pledge per backer of similar projects (same category) in the given year
6. launched_quarter-0.063191
7. goal-0.060700
8. usd_goal_real-0.056942
9. launched_year-0.044968
10. goal_cat_perc-0.038937 %percentile bucket of goal
11. currency_USD-0.035004
12. currency_GBP-0.009265
13. main_category_Film_and_Video-0.007648
14. country_US-0.007604
15. main_category_Technology-0.005463


The below list has the top 15 features the corresponding importance from XGBoost (**second Iteration**)
1. duration	0.089933
2. name_len	0.067842 % length of names of the project
3. participants	0.067755
4. name_words	0.066489 % number of words in the characters
5. avg_success_rate	0.064787
6. launched_month	0.056317
7. avg_ppb	0.054222
8. launched_quarter	0.046669
9. usd_goal_real	0.036803
10. goal	0.033310
11.	goal_log	0.029468 % natural log of goal to shrink the scale
12.	launched_year	0.025452
13.	currency_USD	0.024884
14.	goal_cat_perc	0.023880
15.	Goal_1000	0.018772 %goal divided by 1000 to classify the ranges

## Contents of the repository
The [file](https://github.com/srishtis/Kaggle-Kickstarter-Project-Status-Prediction/blob/master/kickstarter_project_predictions_%20final_version_0109.ipynb) 'kickstarter_project_predictions_final_version_0109.ipynb' contains the first iteration with best accuracy of 68.9%.

The [file](https://github.com/srishtis/Kaggle-Kickstarter-Project-Status-Prediction/blob/master/kernel.ipynb) 'Kernel.ipynb' contains the second iteration with best accuracy of 69.2%

### What are the additional steps followed in the second iteration?
I have created additional features using the name of the project and the goal amount. The features have been explained in the notebook itself.
Although I tried ensembling models in the second iteration using a normal averaging approach and boosting(AdaBoosting), there was no improvement in the performance.

### What could be the probable next steps?

#### Feature Engineering
Create features around number of projects in the same category in the same month

Create features around number of projects in the same category in the same week

Create features on the average success rate of similar category projects with simlar duration

Create features on the mean/ median goal amount of projects with similar category and similar duration

#### Hyperparameters optimization of the XGBoost algorithm
Try different combinations of the learning_rate and number of trees parameters

#### Explore light GBM
Implement light GBM to see if it performs better than XGBoost
Expected improvements:
1. faster execution than XGBoost
2. improved accuracy due to the leaf-wise split (instead of level wise split- this should improve the amount by which the log loss reduces)


## Links
The Kaggle kernel for the first iteration can be found [here](https://www.kaggle.com/srishti280992/data-preprocessing-feature-engg-prediction)
The Kaggle kernel for the second iteration is [here](https://www.kaggle.com/srishti280992/xgboost-classifier-69-2-feature-engg-eda)
