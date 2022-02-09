# Predicting Potential Salaries using Data Science

### Background

Job hunting is a part and parcel of life. On average, a person changes jobs about five times during his/her working career. One of the biggest hurdle to overcome in job hunting is to negotiate salaries and this salary prediction models aims to eliminate this hurdle for both job seekers and hiring companies.

### Target Audience

**1. Primary stakeholders: Job seekers** <br/>
With this salary prediction model readily available, one will be able to gain insights into the industry from exploratory data analysis, and get a benchmark or an idea of the salary that might be offered before applying for the job. Not only job seekers can apply this model to his/her next potential job, existing employees will also be able to check if he/she is paid according to the market trend, and negotiate for a higher pay within the company. As the exploratory data analysis will show the market demand for such jobs, companies might need to offer competitive salaries in order to retain their existing employees.


**2. Secondary stakeholders: Companies seeking to hire** <br/>
Companies will be able to set realistic hiring budgets if they are setting up new data science teams. They will also be able to check hiring market trends, and are able to decide if they should offer competitive salaries if they are in urgent need of certain roles.


**3. Platform: Job Portals and Recruitment Agencies** <br/>
This salary prediction model can be utilized by job portals and recruitment agencies to reconcile these two stakeholders. As the companies post up their job listings, the job seekers are able 

### Data Source
The dataset used in this salary prediction model is scraped from Singapore job portal mycareersfuture.sg, and comprises of jobs in the data science industry including but not limited to roles such as data scientist, data analyst and data engineers. While this particular industry was selected as a form of personal research before embarking on my job hunt as a data scientist, it is merely a proof of concept, and can be easily tweaked to predict salaries from other industries.

### Project Workflow

This project consists of six notebooks:
* 01_API-Scraper-mycareersfuture
* 02_Data-Cleaning
* 03_Exploratory-Data-Analysis
* 04_Pre-processing-Dataset-for-Modelling
* 05a_Regression-Modelling
* 05b_Classification-Modelling

**1. Scraping the Data** <br/>

*Notebook - 01_API-Scraper-mycareersfuture*

Using an API scraper, datasets were obtained from mycareersfuture.sg using the following keywords to search for job listings:
* 'data scientist'
* 'data analyst'
* 'data enginner'
* 'business analyst'
* 'machine learning'
* 'python'
* 'data'

These datasets were then concatenated to create a comprehensive dataset that includes most jobs in the data science industry.

**2. Cleaning the Data** <br/>

*Notebook - 02_Data-Cleaning*

Several cleaning and transformation tasks were performed in order to prepare a dataset suitable for modelling. Some actions taken as this stage are:
* Feature engineering the target variable (average salary) from the minimum and maximum salary values of each job listing, and removing those that appeared invalid such as zero values and those that were too high.
* Several of the features in the dataset such as `job_title`, `position_level` were categorical with a huge number of possible unique values. Hence standardization and simplification of those features were required.

After cleaning the dataset, there was 4,000 rows and 10 columns in the dataset.

**3. Exploratory Data Analysis** <br/>

*Notebook - 03_Exploratory-Data-Analysis*

Correlations between the different features in the datasets are investigated in this section. Further feature engineering from text features such as `skills` was done to convert it to the categorical features for modelling.

**4. Pre-processing** <br/>

*Notebook - 04_Pre-processing-Dataset-for-Modelling*

This section involves one-hot encoding the standarized categorical variables in the dataset. The resultant dataset for modelling contained about 4,000 rows and 90 columns. 

A second target variable `salary_above_median` was also created for classification modelling. `salary_above_median` will represent if the salary offered will be above or below the median value according to the candidate's year of experience.
* 1 represents salary above median values for that given year of experience
* 0 represents salary below median values for that given year of experience.

**5. Modelling and Evaluation** <br/>

*Notebook - 05a_Regression-Modelling & 05b_Classification-Modelling*

There are two different types of modelling carried out in this project; regression and classification modelling. As the regression model was found to be insufficient for predicting salaries, a classification model was also implemented. For each of the models, the dataset was split into training and test sets using proportions of 75% and 25% respectively. A wide variety of models such as linear regression, logistic regression, gradient boosting, random forest, support vector machine are tested out on this dataset, with hyperparameter tuning to increase the accuracy of the models.

Some key take-aways from the modelling are:
* Training scores are on average, much higher than test scores across the models. This suggests that the models have a tendency to overfit, and cross-validation should be done in order to prevent overfitting. 
* While the classification model is more accurate in predicting salaries, it can only provide limited information which may not be useful in salary negotiations. To reconcile the two different modelling methods, the classification model can be used to narrow down the dataset, and the regression model applied on the filtered dataset to gain predictions with lower errors.
* Salaries in the real world are subjected to a lot of variation that cannot be fully accounted for by only the features in the dataset, as seen in the relatively low accuracy scores for even the best regression models.


### Future Development

* A NLP classification model to predict salaries from text features such as `job_description`. This project briefly touched on NLP, and the NLP classification modelling returned comparable results without much processing. Hence, this could be another way forward with predicting salaries.
* Scraping a dataset containing information of the hiring companies such as age, size and ratings of the companies and adding it to the modelling dataset. The type of companies e.g. MNC, SME will definitely have an effect on the salary offered.
* Collecting more detailed data from job seekers. Salaries are likely to be affected by a range of employee attributes that could not captured in job listings such as education level or the nature of previous work experience, and having this data might allow futher improvements to modelling predictions.
