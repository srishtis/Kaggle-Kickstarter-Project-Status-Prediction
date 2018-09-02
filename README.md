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
Best Accuracy: 68.9 %
Best Model: XGBoost
Key Drivers (top 15):
features	XGB_imp
	duration	0.111218   %duration is the difference between deadline and launch date
	participants	0.091028 %number of projects launched in the same year-quarter with the same goal bucket in the same category
	avg_success_rate	0.084386 %probability of success of project on the basis of pledge (pledge per backer) and goal amount of similar projects in the project year
	launched_month	0.075908
	avg_ppb	0.070271 #average pledge per backer of similar projects (same category) in the given year
	launched_quarter	0.063191
	goal	0.060700
	usd_goal_real	0.056942
	launched_year	0.044968
	goal_cat_perc	0.038937 %percentile bucket of goal
	currency_USD	0.035004
	currency_GBP	0.009265
	main_category_Film_and_Video	0.007648
	country_US	0.007604
	main_category_Technology	0.005463
