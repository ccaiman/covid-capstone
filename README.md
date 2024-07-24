Author: Charles C Barnes

Institution: QuickStart Inc

Active Project Dates: July 9th, 2024 - July 24th, 2024

# Summary

During the peak of the COVID-19 pandemic, hospitals were at max capacity caring for people with coronavirus infection with severe symptoms. A local hospital has collected data in an effort to predict which people will require the ICU and help people at risk of sever symptoms make it to an ICU bed. I used supervised classification ML models to predict ICU need, including logistic regression, decision tree, and random forest. I selected best features from the dataset and parameters for the best model, random forest, to arrive at a final mode. The final model was 97% accurate at predicting `Yes` and 95% at predicting `No`. The model could be used to supplement medical expertise when deciding who to monitor closely and move to the ICU. See this link for a project presentaiton: https://c-c-barnes.quarto.pub/predicting-icu-need/

# Business problem

A local hospital wants to use their data to predict whether a person with coronavirus infection will need to be admitted to the ICU for treatment. The prediction has implication for improved recovery and better use of hospital resources for people who are most in need.

# Data

The data is from the Kaggle database "COVID-19 - Clinical Data to assess diagnosis": https://www.kaggle.com/datasets/S%C3%ADrio-Libanes/covid19

The dataset includes demographics, previous disease history, blood biomarkers, vital sign biometrics, and time window of ICU administration for all de-identified people treated in the hospital for coronavirus disease.

# Methods

## Exploratory data analysis (EDA)

EDA of data types with descriptive statistics and plots. I used eatmaps and scatterplots to analyze correlated features.

## Data cleaning/preprocessing

I engineered a feature, `target`, based off of the target feature in the dataset (`ICU`). I kept data entries before admission to the ICU to predict if someone will need the ICU. I removed highly correlated features.

## Model building

I balanced the `target` groups with random undersampling of `No` values. I then used a 70:15:15 train-test-validation split to build three different supervised classification ML models: logistic regression, decision tree, and random forest.

I used the area under the receiver operating characteristic curve to assess model performance. I used the standard deviation after 5-fold cross validation to measure model variance and overfitting.

For a best performing model, I selected the best features leading to better model accuracy and decrease model variance. I tuned hyperparameters with log loss scoring.

# Results

See this link for a project presentation:
https://c-c-barnes.quarto.pub/predicting-icu-need/

Random forest models perfomred best with the data. The final model had 50 features.

The model was 97% accurate predicting `Yes` with a recall of 70/73 true positive cases in the validation dataset.

The model was 95% accurate predicting `no` with a recall of 63/65 true negatives.

# Conclusions

The final model could be used to supplement medical expertise when making decisions about patient monitoring and transport to the ICU.

# Considerations

The model predicts whether someone will require admission to the ICU within 12 hours after being in the hospital.

The model does not include time as a feature/target and does not predict when a person will require the ICU.

With more time on this project, I might consider stratified resampling to improve model performance. Some `DISEASE GROUPING` features were rare in the dataset by EDA and I wonder if the model had difficulty learning any patterns that might there.