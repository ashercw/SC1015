# SC1015
Reuploading a data analysis project from April 2024
# Cardiovascular-Health
## About
This is a SC1015 Mini-Project on Cardiovascular Health. In this project, we will analyse the dataset [Cardiovascular Disease](https://www.kaggle.com/datasets/colewelkins/cardiovascular-disease) to assess the reliability of Blood Pressure (BP) as an indicator for Cardiovascular Health. We will do so by finding the correlation between BP and various lifestyle variables, and comparing BP with other health indicators. For a detailed walkthrough, please view the source code in the following order:

1. Data Cleaning
2. Exploratory Data Analysis
3. Data Preprocessing
4. Machine Learning

## Problem Definition
- Are we able to predict BP based on various lifestyle variables (active, alcohol, cardio, and smoke) ?

## Models Used
- Decision Tree
- Random Forest
- Hypertuning using GridSearchCV

## Conclusion
EDA
- Negative lifestyle variables (alcohol, cardio, and smoke) have a stronger correlation with BP.
- Positive lifestyle variables (active) do not have a strong correlation with BP.
- Correlation between lifestyle variables and BP is strongest for participants with Stage 2 Hypertension.
- External sources suggest that all lifestyle variables are related to BP, but there is a timeframe associated with their impact.
- Cholesterol and BMI have a stronger correlation with BP. Thus, they might be caused by similar health conditions.
- Relationship between health variables and BP are not linear, either plateauing (cholesterol) or (BMI).

ML

Upsampled vs Downsampled:
- The upsampled model consistently shows better goodness-of-fit and classification accuracy than downsampled one for training and test sets.
- Across the BP classes, Class 1 (Elevated BP) from the upsampled model has the largest improvement over the downsampled one.
- For FPR, upsampled and downsampled datasets have similar results which means that upsampled would still be the better for predicting BP.

Decision Tree vs Random Forest:
- Random Forest has better goodness-of-fit and classification accuracy than Decision Tree.
- Random forest is a better model as it generates multiples decision trees and this will result in a better goodness-of-fit.
- To further increase prediction accuracy, we implemented hypertuning, which can improve goodness-of-fit of the random forest model.
- Hypertuning focused on optimizing the performance of the random forest by finding the most optimal parameters.

Thus, the upsampled data using the Random Forest model after hyperparameter tuning is the better overall predictor. This is primarily due to better accuracy and more balanced performance across the classes, particularly in handling the minority classes without overly sacrificing performance in other areas.

Class-specific:
- The ML model is most capable at predicting Class 0 (Normal Heart Rate) and 3 (Hypertension Stage 2) as these two classes have high TPRs and low-moderate FPRs.
- Class 1 (Elevated Heart Rate) can still be [redicted using the model but it will not be as accurate as class 0 and 3 as its TPR is lower.
- Class 2 (Hypertension Stage 1) cannot be predicted using this model as its TPR is too low.

## Lesson Learnt
Analysing data collection to detect any potential issues; the dataset only looks at cholesterol when there is good cholesterol, measured with the amount of high-density lipoprotein (HDL) and bad cholesterol, measured with the amount of low-density lipoprotein (LDL).

Handling imbalanced datasets by upsampling and downsampling the dataset and taking into consideration their implications on the datset and prediction model accuracy.

Employing GridSearch with increased cross-validation folds can refine model parameters. Exploring XGBoost or deep learning may also enhance results, and nested cross-validation could offer a more reliable performance assessment.

## References
- https://www.kaggle.com/datasets/colewelkins/cardiovascular-disease

## External Sources
- https://pubmed.ncbi.nlm.nih.gov/8728301/
- https://pubmed.ncbi.nlm.nih.gov/20550499/
- https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6316192/
- https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10243231/
- https://my.clevelandclinic.org/health/articles/11918-cholesterol-high-cholesterol-diseases
- https://www.mayoclinic.org/diseases-conditions/high-blood-pressure/in-depth/high-blood-pressure/art-20045206#:~:text=An%20inactive%20%E2%80%94%20also%20called%20sedentary,or%20computer%20may%20be%20helpful
- https://www.mayoclinic.org/diseases-conditions/high-blood-pressure/expert-answers/blood-pressure/faq-20058254
