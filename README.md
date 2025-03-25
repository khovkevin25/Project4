# Hair Loss Analysis

## **Overview**
Question: How do various factors, such as genetics, medication, stress, environmental factors, affect hair loss? Can we create a model that predicts if someone has reported hair loss based on their binary responses to the other questions?

The chosen dataset was used for exploratory data analysis, modeling, and predictive analytics aimed at understanding the relationship between various factors and the presence or absence of balding in individuals. With the use of the random forest model, we created a binary classifier to predict whether individuals will experience balding.

## **Data Processing and Cleaning**
- talk about pyspark
- features being used/not being used
- target variable

## **Visuals and Findings**
- paste visuals and insights

## **Random Forest**
### Initial Results
- The model has the accuracy of correctly predicting the presence and absence of balding in individuals 55% of the time. Given the following precision and recall scores, the model is not entirely reliable in predicting individuals who experience balding and those who do not, nor is it effective in capturing the majority of these individuals. 
  - Absence of balding had a precision of 55% and recall of 57%
  - Presence of balding had a precision of 54% and recall of 53%
    
- After evaluating the model against the training and testing set, there is a clear occurance of overfitting. In other words, the model is memorizing the training set to well that it is not able to make correct predictions on new data, the testing set.
  
### Model Optimization Steps and Results
- To optimize the model:
  - Removed any multicollinearity that was visibly present in the data
  - Lowered the number of n_estimators in the model: Beneficial because we have limited computational resources. Therefore, fewer trees (simplier model) is more effective since the dataset is relatively small
    
- Results:
  - The accuracy of the model slightly increased to 58%
  - After revewing the update precision and recall scores, the model continues to lack reliability in its predictions and ineffective to capturing majority of individuals who experience balding verse those who do not
    - Absence of balding had a precision of 58% and recall of 60%
    - Presence of balding had a precision of 57% and recall of 55%
  - Occurance of overfitting remains indicating possibilites of other limitations besides multicollinearity

## **Summary & Limitations**
Overall, the model has a poor performance in predicting the presence and absence of balding. This could be the result of the following limitations within the given datset: presence of multicollinearity where too many features are correlated to each other, the possibility of noise and/or irrelevant detail attributed to the model overfitting the data , and the lack of overall useful data entries such as gender, dietary factors, ethnicity, etc. 

## **Resources**
- Dataset Source: https://www.kaggle.com/datasets/amitvkulkarni/hair-health
- Matplotlib Documentation (https://matplotlib.org/stable/index.html) used to help create various visuals
