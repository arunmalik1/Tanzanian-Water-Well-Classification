**# Tanzanian-Water-Well-Classification**

This project is for the Tanzanian water wells classification challenge. The stakeholder is the Tanzanian goverment, who wants to know how to correctly classify funtioning water wells. 

**Methodology**
My approach to addressing the problem at hand was comprised of four distinct components: Data exploration, data preparation, creating modeling pipelines and model deployment/selection.

Data Exploration: This step involved exploring each varialbe in the data set. Thier types, value ranges, distributions and if they were missing values.

Data Preparation: Developed strategies for imputing missing values, dropping variables because of collinearity and dealing with messy data. For example, multiple variables had 0's as a value and there were many spelling errors. 

Creating Data and Model Pipelines: I created two data pipelines, one for transforming numerical variables and the other for categorical data. The data pipelines were then fed into model pipelines, which enabled me to try multiple models without having to write redundant code. 

Model deployment and selection: Water wells are in three classifications, funtional, non functional and funtional but needing repair. I chose classification models, specifically Logistic regression, Desicion trees, Random forests, KNN models and XGBoost. Models were refined using hyperparameter tuning techniques in order to find the most accurate model while reducing over fitting. 

Visual Presentation: I used visuals throughout the project, from initally exploring how the variables related to classifying water wells and diplaying the results of the models.

**Data Exploration:** 
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

**Data Cleaning**

Variables with similar or duplicate data:

Basin, subvillage, region, region code, district_code, lga and ward are all variables given to determine geographic location. I chose to keep region code and district_code because they are numerical. I chose region because I wanted the names of regions and the variables didn't contain any null or 0's as a value. 

Scheme_management and scheme_name are data for who operates the waterpoint. I chose to use scheme_management because it has more comeplete data.

Extraction_type, extraction_type_group and extraction_type_class are all extraction methods. I chose extraction_type because it has the most granular data. 

Management and management_group tell us who manages the water well. I chose management because it has more granular data. 

Payment and payment_type are identical.

Water_quality and quality_group are also very similar. I chose quality_group 

Quantity and quantity_group are identical. 

Source, source_type and source_class are closely realted. I chose source because it has less unknowns.

Funder and Installer had many spelling errors for institutions which needed to be corrected.

**Imputting missing data**

Numerical data: amount_tsh, latitude and longitude, polpulation and construction_year were all variables I used in the models. I chose to use to impute the median because it is not as sensative as the mean.

Categorical data: 





