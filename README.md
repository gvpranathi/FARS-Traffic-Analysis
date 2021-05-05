# FARS-Traffic-Analysis
Analysis:
Data considered: 2019 (approximately 33,500 records)
Algorithms selected for study: Linear Regression, Logical Regression, SVM, and Naïve Byes
Data Preparation & Exploration:
Cleanse anomalies in data specially in feature columns that were used to derive Severity column. 
 
Analysis to select features:
Step 1:
•	Depended variable ‘Severity’ column derived from VE_TOTAL, PERSONS, and FATALS
•	Variables VE_TOTAL, PERSONS, and FATALS are standardized (Normalized) and the normalized values added together
•	Value from summation is used to derive Severity column. First 25% of distribution of summation is categorized as Low severity, 25% - 75% distribution is categorized as Medium severity, and 75% and above is categorized as High severity.
•	Latitude and Longitude columns are normalized to avoid negative numbers in dataset.
•	Because the dependent variable ‘Severity’ is derived from above 3 columns, those columns and their related attributed are removed from Dataset.
Step 2:
•	Among the remaining 45 columns in dataset top 20 features were evaluated based on the scores calculated using SelectKBest feature_selection algorithm offered by sklearn package.
 
•	Same set of 45 columns from dataset were also evaluated against ExtraTreesClassifier algorithm of sklearn to get top 20 highly important features that could account for predicting dependent variable (severity).
 
•	Set of 28 columns are gathered by combining outcome from above 2 runs (i.e. from feature_scores & from feature_importance) and a correlation matrix is executed on these 28 columns to find relation between features, and between individual features against Severity variable.
Features selected after analysis:
'MILEPT','COUNTY','STATE', 'CITY','ROUTE','LATITUDE','LONGITUD',
'MAN_COLL','HARM_EV','RD_OWNER','REL_ROAD','CF1','PVH_INVL','WEATHER',
'NOT_HOUR','ARR_HOUR','ARR_MIN','DAY_WEEK','DAY','NOT_MIN','MONTH','HOUR',
'PEDS','PERNOTMVIT','LGT_COND','HOSP_HR','HOSP_MN','FUNC_SYS'

Featured Planned Initially: 'DAY_WEEK', 'MONTH', 'HOUR', 'LGT_COND', 'WEATHER'
Modeling & Evaluation:
Algorithm	Accuracy (from feature selection process)	Accuracy (with initially Planned features)
Linear Regression	Mean Abs Err: 3.7871                  Mean Abs Err: 1.2844
 Mean Square Err: 84.2573	                              Mean Square Err: 2.4510
Logical Regression	64%                                 	45%
SVM – Support Vector Machine	44%                       	33%
Naïve Byes	59%	                                          41%                

