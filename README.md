# Final_Capstone

## Using The National Health and Nutrition Examination Survey (NHANES) to Predict Heart Disease


### Background 
Heart disease is the leading cause of death for men, women, and people of most racial and ethnic groups in the United States. About 647,000 Americans die from heart disease each year—that’s 1 in every 4 deaths. Heart disease costs the United States about $219 billion each year from 2014 to 2015, including the cost of health care services, medicines, and lost productivity due to death. 

The link between diet/nutrition and cardiac disease is long established. Understanding the nature of that link is incompletely understood and continues to evolve over time. Medical science continues to search for both prevention and treatment methods to tackle the morbidity and mortality presented by cardiac disease, including potential changes in diet. 

The goal of this capstone is to attempt to better understand the link between diet/nutrition and cardiac disease by exploring the relationship between various diet components, nutrients, and behaviors around nutrition. Although limited in size of data, much like a "pilot study," the results of this study may offer researchers an insight into a specific nutrient or dietary behavior that warrants further study on a larger scale. 





* Part I. Using Unsupervised Learning methods in feature engineering
* Part II. Using Supervised Learning methods to classify heart disease and feature importance 

## Part I: Unsupervised Learning :bow_and_arrow:

### The Data
The data was obtained from: https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?BeginYear=2015. The database was collected in January 2020. The data files are available only as SAS Transport files in .xpt format, and must be converted to .csv files in order to be used in Python. There are five categories of data availabe, each containing multiple data files. 

#### Original Data Files :card_index_dividers: 
- [x]  Demographics -- contains unique ID number, age, sex
- [x]  Medical Conditions -- combined 4 indicators of heart disease to create target value per subject; all values encoded
- [x]  Body Measurements -- includes height, weight, BMI, waist circumference, sagittal abdominal diameter per subject
- [x]  Blood Pressure questionnaire -- questions regarding subject's history of blood pressure status; values encoded
- [x]  Blood Pressure measurements -- combined 2 measures of blood pressure to create average blood pressure measure per subject
- [x]  Complete Blood Count laboratory results -- contains standard blood count measurements per subject
- [x]  Standard Chemistry laboratory results -- contains blood standard chemistry values per subject
- [x]  High Density Lipid laboratory results -- HDL values per subject
- [x]  Total Cholesterol laboratory results -- total cholesterol values per subject
- [x]  High Sensitivity C-Reactive Protein laboratory results -- HSCRP values per subject
- [x]  Total Dietary Intake Day 1 -- contains intake values for individual nutrients, day 1
- [x]  Total Dietary Intake Day 1 -- contains intake values for individual nutrients, day 2; day 1 & day 2 combined for average dietary intake of each nutrient, per subject
- [x]  Total Dietary Supplement Intake Day 1 -- contains intake values for individual supplement nutrients, day 1 
- [x]  Total Dietary Supplement Intake Day 2 -- contains intake values for individual supplement nutrients, day 2; day 1 & day 2 combined for average supplement intake of each nutrient, per subject; average dietary intake and average supplement intake combined for TOTAL average intake of each nutrient, per subject

#### Data cleaned/wrangled, files merged, outliers transformed, data normalized

### Unsupervised Clustering of laboratory values and body measurements: :eight_spoked_asterisk:
* **combined_cluster** (means shift, body measurements & labs) silhouette score: 0.258
* **lab_cluster** (means shift, lab measurements) silhouette score: 0.257
* **body_measure_cluster** (kmeans, body measurements) silhouette score: 0.172
#### Clusters added as features for Supervised Learning models

## Part II. Supervised Learning :chart_with_upwards_trend:

#### Models Tested:
- [x]  Random Forest Classifier
- [x]  Gradient Boosting Classifier
- [x]  Support Vector Classifier

#### Trials:
* imbalanced class distribution vs oversampling with SMOTE
* feature engineering with feature importance
* hyperparameter tuning with random grid search
* trial all 4 SVM kernels
* key metrics: 
  *   Recall & F-1 scores for target class 
  *   AUC-ROC vs accuracy; confusion matrix 
  *   goal to maximize number of true positives for target class

#### Supervised Models: Best Results: :bar_chart:
* Model: SVM, linear kernel, top 30 features, default hyperparameters, SMOTE balanced class distribution
* Results: 
  * Recall Target Class **0.73**, Recall Non-Target Class **0.77**
  * F-1 Score Target Class: **0.86**, F-1 Score Non-Target Class **0.29**

#### Evaluation: :clipboard:
Although the model produced a reasonable accuracy for predicting the target class of heart disease, there is much room for improvement. The model suffered from a lack of focus with multiple features. Rather than focus strictly on nutrients and dietary features, the model included many variables that focused on medical history, especially regarding blood pressure and cholesterol. It is well known that elevated blood pressure and cholesterol are risk factors for heart disease, and this was confirmed in the top important features in the best model. While the model did confirm well-known variables/risk factors for heart disease, it supplied little new actionable information. 

The model also suffered from a small data set. Although the initial merged data file contained ~10,000 records, due to missing labratory values and body measurements, the final file consisted of only ~4,500 records. Using only nutrient and dietary-related variables would have resulted in a much larger data file. 

### Future Goals: :dart:
* Reduce potential variable features by excluding all non-nutrient or dietary-related variables.
* Increase the data set by using additional survey cycles from previous years 
 
