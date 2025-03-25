# Hair Loss Analysis

## **Overview**
Question: How do various factors, such as genetics, medication, stress, environmental factors, affect hair loss? Can we create a model that predicts if someone has reported hair loss based on their binary responses to the other questions?

The chosen dataset was used for exploratory data analysis, modeling, and predictive analytics aimed at understanding the relationship between various factors and the presence or absence of balding in individuals. With the use of the random forest model, we created a binary classifier to predict whether individuals will experience balding.

## **Data Processing and Cleaning**
We began by creating a spark session that we then use to host the database so it is hosted somewhere people can pull from. We then read the data into a dataframe and converted it into a pandas for our initial cleaning. This data set is actively managed from the user in kaggle so there was only a little bit of cleaning necessary: 
  - We dropped the ID column as it was superfluous 
  - Some of the columns had a random space at the end so we deleted those
  - Lastly, a good chunk of the data was binary true/false values so we converted those to 0/1 to be a represented by a binary number

We did additional cleanings specific to the model creation and optimization process. 
  - After reading into a panda dataframe, she removed the unneeded ID column, used “get_dummies” function to replace the yes/no with true/false responses.
  - To further optimize, she used the get_dummies function with the attribute drop_first=True to help prevent the multicollinearity in the regression model. 

There are a lot of columns in this dataset and we used nearly all of them - ranging from genetics to stress levels to environmental factors, throughout the visualizations you'll see the variety of data points.

Lastly, our target variable is _Hair Loss_ as we are seeing how these other columns and attributes influence or lead to it.   

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
Overall, the model has a poor performance in predicting the presence and absence of balding. We also tested additional models (logistic regression and SVM) to assess their performance against the data. The results of models proved to be inadequate as well. This leads us to believe that the following limitations (Ie: presence of multicollinearity where too many features are correlated to each other, the possibility of noise and/or irrelevant detail attributed to the model overfitting the data , and the lack of overall useful data entries such as gender, dietary factors, ethnicity, etc.), and then some, may be attributing to the poor model performances.

## **Resources**
- Dataset Source: https://www.kaggle.com/datasets/amitvkulkarni/hair-health
- Matplotlib Documentation (https://matplotlib.org/stable/index.html) used to help create various visuals
