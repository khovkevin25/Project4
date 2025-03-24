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
- Against the testing data,  of overfitting
### Optimized Steps and Results
- Overfitting still present
## **Summary & Limitations**
Overall, the model has a poor performance in predicting the presence and absence of balding. This could the result of the following limitations within the given datset: presence of multicollinearity where too many features are correlated to each other, the possibility of noise and/or irrelevant detail attributed to the model overfitting the data , and the lack of overall useful data entries such as gender, dietary factors, ethnicity, etc. 

## **Resources**
- Dataset Source: https://www.kaggle.com/datasets/amitvkulkarni/hair-health
- Matplotlib Documentation (https://matplotlib.org/stable/index.html) used to help create various visuals
