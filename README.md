# Tanzanian-Water-Well-Classification

This project is for the Tanzanian water wells classification challenge. The stakeholder is the Tanzanian goverment, who wants to know how to correctly classify funtioning water wells. 

# Data Collection:

The data is given by Driven data: 
https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/page/23/

# Methodology
My approach to addressing the problem at hand was comprised of four distinct components: Data exploration, data preparation, creating data pipelines and model deployment/selection.

Data Exploration: This step involved exploring each variable in the data set. Their types, value ranges, distributions and if they were missing values.

Data Preparation: Developed strategies for imputing missing values, dropping variables because of collinearity and dealing with messy data. For example, multiple variables had 0's as a value and there were many spelling errors. 

Creating Data Pipelines: I created two data pipelines, one for transforming numerical variables and the other for categorical data. The data pipelines were then fed into model pipelines, which enabled me to try multiple models without having to write redundant code. 

Model deployment and selection: Water wells are in three classifications, funtional, non functional and functional but needing repair. I chose classification models, specifically Logistic regression, Decision trees, Random forests, KNN models and XGBoost. Models were refined using hyperparameter tuning techniques to find the most accurate model while reducing over fitting. 

Visual Presentation: I used visuals throughout the project, from initially exploring how the variables related to classifying water wells and displaying the results of the models. I have included them at the end of this file.

# Data Exploration: 
Water wells are in three categories:

Funtional: 53.62 %
Non Funtional: 38.78 %
Functional needs repair: 7.6 %

Varaibles with mising values:

funder                    3635
installer                 3655
subvillage                 371
public_meeting            3334
scheme_management         3877
scheme_name              28166
permit                    3056

Variables with 0's as a value:
 
amount_tsh:         41639
gps_height:         20438
longitude :         1812
num_private:        58643
district_code:      23
population   :      21381
public_meeting:     5055
permit:             17492
construction_year:  20709

# Data Cleaning

Variables with similar or duplicate data:

Basin, subvillage, region, region code, district_code, lga and ward are all variables given to determine geographic location. I chose to keep region code and district_code because they are numerical. I chose region because I wanted the names of regions and the variables didn't contain any null or 0's as a value. 

Scheme_management and scheme_name are data for who operates the waterpoint. I chose to use scheme_management because it has more complete data.

Extraction_type, extraction_type_group and extraction_type_class are all extraction methods. I chose extraction_type because it has the most granular data. 

Management and management_group tell us who manages the water well. I chose management because it has more granular data. 

Water_quality and quality_group are also very similar. I chose quality_group 

Source, source_type and source_class are closely related. I chose source because it has fewer unknowns.

Payment and payment_type are identical.

Quantity and quantity_group are identical. 

Funder and Installer had many spelling errors for institutions which needed to be corrected.

# Inputting missing data

Numerical data: amount_tsh, latitude and longitude, population and construction_year were all variables I used in the models. I chose to use to impute the median because it is not as sensitive as the mean and the data has a big range in values.

Categorical data: The majority of the variables in the data set were categorial and I chose to use the most frequent value to impute missing values.

# Creating Model pipelines

The data is imbalanced so I chose SMOTE and Random Class Under Sampler techniques to improve the predictive power of the models. The result of the best model is as follows:

Best Model was A tuned XGBoost Model: Accuracy 78.76%

The model was able to predict functioning water wells and wells that need repair fairly well. It struggled with non functional wells.

![BestXGBoost](https://user-images.githubusercontent.com/115169255/211090892-83c3724b-f674-438d-b522-dfa2acf6ab73.png)


**Other Models:**


Logistic regression with SMOTE: Accuracy score 65%

![LogisticSmote](https://user-images.githubusercontent.com/115169255/211089263-68eb9d95-725f-49e7-8e0c-351f72bd2fe8.png)


Logitic regression with UnderSampler: Accuracy score 65%

![LogisticUnderSampler](https://user-images.githubusercontent.com/115169255/211089293-4deb9893-2c06-41be-b4b1-f2b314dc047d.png)


Base desicion tree with SMOTE: Accuracy score 75%

![BaseDesicionTree](https://user-images.githubusercontent.com/115169255/211091325-3774ed8f-e940-4dac-9073-9820f7f8d669.png)


Base desicion tree with UnderSampler: Accuracy score 65 %

![BaseDesicionUnderSampler](https://user-images.githubusercontent.com/115169255/211089898-03da7103-f6fe-4856-833d-665bbd7e7276.png)


Decision Tree with calculated parameters and SMOTE: Accuracy score 68%

![DecisionSmoteParameters](https://user-images.githubusercontent.com/115169255/211090005-f3f1d6de-7cdc-406e-b46c-9f93ffda0cad.png)

Random Forest: Accuracy score 70%

![RandomForest](https://user-images.githubusercontent.com/115169255/211090148-72de6206-6c4e-45e8-a37a-001fa6f32809.png)

KNN Classification: Accuracy score 70%

![KNN](https://user-images.githubusercontent.com/115169255/211090373-d72b05f5-d850-481d-a851-5f915c898a14.png)

XGBoost: Accuracy 75%

![Base XGBoost](https://user-images.githubusercontent.com/115169255/211090564-9d9abeba-34cb-4755-bdc5-8abe1fcd911c.png)


**Two Class Models:**

I combined wells that need repair and non funtioning wells as a category and reran the models. They did have higher accuracy scores, however I did not choose them as the best models because it was not the intent of the original problem.

Logistic Regression: Accuracy 78%

![Logistic2Class](https://user-images.githubusercontent.com/115169255/211093805-78ca2ae8-d4d4-4b89-80a1-eaf21156f684.png)


Base Desicion Tree: 

![BaseDesicion2Class](https://user-images.githubusercontent.com/115169255/211093931-6a992501-241c-4741-9c9d-920c3c5c030b.png)


# Data Visuals:

![Water Pump Status](https://user-images.githubusercontent.com/115169255/211094553-9f8042e2-c2bb-49c4-9665-422f2d2d97b6.png)




![Top10Funders](https://user-images.githubusercontent.com/115169255/211094520-9baab239-907b-4afe-af1d-51d483219bd8.png)




![Top10Installers](https://user-images.githubusercontent.com/115169255/211094527-3b16713f-8129-4d5a-a9f0-dde911f5aa52.png)

![Water Quality](https://user-images.githubusercontent.com/115169255/211094585-341b4490-4a28-4e37-bdef-c3cfceb76bb2.png)



![Water Quantity](https://user-images.githubusercontent.com/115169255/211094588-b53c43eb-915b-4279-b17b-f898e559a7b3.png)


![Water source](https://user-images.githubusercontent.com/115169255/211094591-9e2bf7c3-9368-46ac-9006-921b76b69af8.png)


