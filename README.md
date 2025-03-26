# Hair Loss Analysis

## **Overview**
Question: How do various factors, such as genetics, medication, stress, and environmental factors, affect hair loss? Can we create a model that predicts if someone has reported hair loss based on their responses to these various factors?

The chosen dataset was used for exploratory data analysis, modeling, and predictive analytics aimed at understanding the relationship between various factors and the presence or absence of balding in individuals. With the use of the random forest model, we created a binary classifier to predict whether individuals will experience balding/hair loss.

## **Data Processing and Cleaning**
We created a Spark session that hosts the database, allowing people to pull from the URL. We read the data into a dataframe and converted it into a Pandas for our initial cleaning. This dataset is actively managed from the user in Kaggle, so there was only a little bit of cleaning necessary: 
  - We dropped the ID column as it was superfluous
  - Some of the columns had a random space at the end so those were removed
  - A good chunk of the data were binary True/False values so we converted those to 0/1 to be a represented by a binary number

We did additional cleanings specific to the model creation and optimization process. 
  - After reading into a Panda dataframe, we removed the unneeded ID column and used the “get_dummies” function to replace the yes/no with true/false responses
  - To further optimize, we used the "get_dummies" function with the attribute "drop_first=True" to help prevent the multicollinearity in the regression model

There are a lot of columns in this dataset and we used nearly all of them - ranging from genetics to stress levels to environmental factors, throughout the visualizations you'll see the variety of data points.

Lastly, our target variable is _Hair Loss_ as we are seeing how these other columns and attributes influence or lead to it.   

## **Visuals and Findings**
- Binary Variables:
  
  - **Genetics:** Below is a chart that displays whether there is a hereditary factor in hair loss. On the x-axis, the 0 represents individuals who do not carry the gene(s) that contributes to hair loss while the 1 represents those who are carriers. Of the individuals who are non-carriers, 52.4% of them are not experiencing hair loss while 47.6% are. As for those who are carriers of the gene(s), 48.3% of them are not experiencing hair loss while 51.7% are. Overall, there doesn't appear to be a significant difference between the two groups.
    
 ![alt text](https://github.com/khovkevin25/Project4/blob/main/Visuals_Binary%20Charts/Genetics_Factor.png)

  - **Hormonal Changes:**
 

  - **Hair Care Habits:**
 

  - **Environmental Factors:**
    The chart helps determine whether environmental factors (such as pollution, UV exposure, or chemicals) contribute to an increased risk 
    of hair loss. If the proportion of hair loss is significantly higher in the exposed group, it suggests a strong correlation between 
    environmental factors and hair health.



  - **Smoking:**
    From the chart, we can observe the proportional differences in hair loss prevalence between smokers and non-smokers. 
    If the red segment is significantly larger for smokers, it suggests a higher incidence of hair loss among smokers compared to non-smokers. 
    Conversely, if both groups show similar proportions, smoking may have a weaker correlation with hair loss.
    This visualization helps in understanding whether smoking is a potential risk factor for hair loss based
 ![image](https://github.com/user-attachments/assets/e42d21eb-86ce-49f7-8af0-c1caa762e0ed)



  - **Weight Loss:**
  The chart helps identify whether weight loss is associated with increased hair loss. If the red portion is significantly larger for those 
  who experienced weight loss, it suggests a higher likelihood of hair loss due to weight loss.

![image](https://github.com/user-attachments/assets/4f3ebcf4-8164-42a3-9283-ea80838b570e)



- Non-Binary Variables:

Similar to the trends seen for the binary variables for this dataset, many of the non-binary variables also did not have a lot of variability between the outcomes and if each led to hair loss or not. Only Age displayed some visual differences between the outcomes.

  - **Medical Conditions:** The "No Data" outcome had the highest percentage of individuals that had no hair loss at 12.5%, but still 9.5% of individuals with hair loss also reported no medical conditions. On the other hand, the highest outcome of individuals with hair loss also had Alopecia Areata at 12.3%, but 9.2% of individuals with the same condition had no hair loss.

![alt text](https://github.com/khovkevin25/Project4/blob/main/Visuals/Non-Binary%20Charts/Medical_Conditions_Chart.png)

  - **Medications & Treatments:** There was also little variability between the different treatments and medications listed in the dataset for having or not having hair loss. Percentages of each outcome ranged between roughly 9% and 11% between both groups.

![alt text](https://github.com/khovkevin25/Project4/blob/main/Visuals/Non-Binary%20Charts/Medications_Chart.png)

  - **Nutritional Deficiencies:** The highest instance of nutritional deficiencies for individuals with hair loss was Zinc Deficiency, but this was also the highest instance for individuals without hair loss as well with 10.3% hair loss to 11.4% no hair loss.

![alt text](https://github.com/khovkevin25/Project4/blob/main/Visuals/Non-Binary%20Charts/Nutrition_Chart.png) 

  - **Stress Level:** The counts for individuals based on stress level were also fairly even across the board, with moderate stress levels having the most variability between showing hair loss and not.

![alt text](https://github.com/khovkevin25/Project4/blob/main/Visuals/Non-Binary%20Charts/Stress_Chart.png)

  - **Age Groups:** The age groups were determined based on quartiles calculated from the age ranges from the dataset. There seemed to be more variability with this feature, especially in the 27-34 and 43-50 age groups, compared to the other features.

![alt text](https://github.com/khovkevin25/Project4/blob/main/Visuals/Non-Binary%20Charts/Age_Chart.png)

## **Random Forest**
### Initial Results
- The model has the accuracy of correctly predicting the presence and absence of balding in individuals 55% of the time. Given the following precision and recall scores, the model is not entirely reliable in predicting individuals who experience balding and those who do not, nor is it effective in capturing the majority of these individuals.
  - Absence of balding had a precision of 55% and recall of 57%
  - Presence of balding had a precision of 54% and recall of 53%
    
- After evaluating the model against the training and testing set, there is a clear occurance of overfitting. In other words, the model is memorizing the training set so well that it is not able to make correct predictions on new data, the testing set.
  
### Model Optimization Steps and Results
- To optimize the model:
  - Removed any multicollinearity that was visibly present in the data
  - Lowered the number of n_estimators in the model: Beneficial because we have limited computational resources. Therefore, fewer trees (simplier model) is more effective since the dataset is relatively small (1000 data points)
    
- Results:
  - The accuracy of the model slightly increased to 58%
  - After reviewing the updated precision and recall scores, the model continues to lack reliability in its predictions and its effectiveness to capture majority of individuals who experience balding versus those who do not
    - Absence of balding had a precision of 58% and recall of 60%
    - Presence of balding had a precision of 57% and recall of 55%
  - Occurance of overfitting remains indicating possibilites of other limitations besides multicollinearity

## **Summary & Limitations**
Overall, the model has a poor performance in predicting the presence and absence of balding. We also tested additional models (logistic regression and SVM) to assess their performance against the data. The results of models proved to be inadequate as well. This leads us to believe that the following limitations (i.e.: presence of multicollinearity where too many features are correlated to each other, the possibility of noise and/or irrelevant detail attributed to the model overfitting the data , and the lack of overall useful data entries such as gender, dietary factors, ethnicity, etc.), and then some, may be attributing to the poor model performances.

## **Resources**
- Dataset Source: https://www.kaggle.com/datasets/amitvkulkarni/hair-health
- Matplotlib Documentation (https://matplotlib.org/stable/index.html) used to help create various visuals
