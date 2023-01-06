# Patient-Survival-Prediction

![dataset-cover](https://user-images.githubusercontent.com/108106393/210886304-f3fc9ee4-bbc1-4673-97d9-15a7856978e6.jpg)

# Objectives 
This project aims to analyze and clean an existing dataset called Patient Survival Prediction. This dataset includes a patients basic information like their Age, BMI, weight and their vitals when they get admitted to the hospital. It also includes health and sickness information like if a patient is responsive, if they have known diseases that could contribute to their increased mortality rate. This also aims to figure out which features play the biggest role when it comes to identifying a patients mortality. After the identification of these features, we create, use and tune different classification models that produces the best recall score. We are focusing on recall in this dataset 

# Business Problem
Maimonides Medical Center in Brooklyn is in need of a preliminary screening test to predict a patient's mortality after being admitted to the ICU

# Data 
This project used the Patient Survival Prediction Dataset from Kaggle.com. It contained 90,000 datapoints and 87 features.

# Methods 
Before modeling, I had to analyze, clean and filter my dataset. I dropped some duplicated rows and checked if the dataset was imbalanced. Since most of my numerical columns did not tell much, I used the categorical columns, calculated the percentages and visualized it using some graphs. After more analysis of the data, I separated the categorical from the nominal and numerical columns for preparation before plugging them into a column transformer. And before everything else, train test split. I used different pipelines for different types of classification models. Since I'm working on a predicting a patient's survival after admittance in the ICU, I used the metric recall score to determine the best classification model. A high recall score indicates a low amount of false negatives which in this case is what we want for our predictor. False Negatives pose a high risk considering that it's a misdiagnosis and a patient could die due to this. I also ran my models with some parameter tuning to find the parameters that works best for the model. I used multiple models starting with the simplest one, the Logistic Regression. I also used tree classifcation models like Decision Trees, Random Forest and XGBoost which came up with pretty good accuracy score. 
I also ended up dropping icu death probability and hospital death probability due to data leakage since I'm predicting hospital deaths. 

# Visualizations
This graph shows the imbalance in my dataset, I added some sampling techniques on my pipelines to deal with this imbalance.
![hospdeath](https://user-images.githubusercontent.com/108106393/211072368-0ba7f991-36e0-41a6-9817-1e7333aab036.png)

This graph shows that Age plays a vital role in predicting if a patient will die or not when they get admitted to the ICU 
![agedist](https://user-images.githubusercontent.com/108106393/211089478-ccd08ef6-4494-4d89-9a77-3373703fee8c.png)


These graphs shows the most common admit source, icu type and bodysystem amongst all the patients who died

![icutype](https://user-images.githubusercontent.com/108106393/211072635-cba82c24-818c-472d-bccd-9053fc3b6dae.png)

Out of all the patients who died, 56% were admitted to the medical surgery ICU

![ICUADMIT](https://user-images.githubusercontent.com/108106393/211072521-d73ce97f-9d65-4bdd-ba47-9804825c7338.png)

60% of the patients who died were admitted to accident and emergency

![BO](https://user-images.githubusercontent.com/108106393/211072650-56483179-eb4f-488e-83d4-da5533ef7006.png)

And the most prevalent bodysystem where the complications were found amongst the patients who died was cardiovascular, which is not surprising because according to the CDC, heart related diseases are the top leading cause of death worldwide.

# Summary of Best Models
![Screenshot (5)](https://user-images.githubusercontent.com/108106393/211073168-643a4ff3-b8b8-4a25-bdec-d00825d58a0a.png)

# Logistic Regression
After using and tuning multiple classification models, logistic regression was the best model. It yielded a recall score of 78.8% and an AUC of 86.96%

![confmat](https://user-images.githubusercontent.com/108106393/211087935-efbdcc48-e17a-4025-beee-d171e5b8ddb5.png)
![roc](https://user-images.githubusercontent.com/108106393/211087963-57435897-7f8f-48d5-a3b5-a097dd8fdf5e.png)

# Recommendations 
Gather more data about a patient's:
Lifestyle
Type of Job
Medications
Reason of admittance
Non-elective surgery

With more data about a patient, we can focus more on lowering false negatives and false positives at the same time considering that they are both misdiagnosis and could pose different risks for both the patient and the hospital involved.
