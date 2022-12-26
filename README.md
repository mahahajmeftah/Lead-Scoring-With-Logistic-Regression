# Lead-Scoring-with-Logistic-Regression
<p>
<a align ='center'></a> •
<a href="#goal">Goal</a> •
<a href="#data">Data</a> •
<a href="#logistic regression">Logistic Regression</a> •
<a href="#preparation">Data Preparation</a> •
<a href="#training">Training </a> •
<a href="#evaluate">Evaluating the model</a> •
<a href="#conclusion">Conclusion</a> •

</p>

<a id='goal'></a>
## 1 Goal
The project aims to use logistic regression to predict the likelhood of the conversion for leads at X Education, a company that sells online courses to industry proffessionals.The goal is to assign a lead score to each lead. such that a lead with higher score have a higher chance of conversion and leads with lower score have a lower chance of conversion.

<a id='data'></a>
## 2 Data
The data used in this project was obtained from Kaggle,it contains around 9000 data points.it consists from various attributes such as Lead Source, Total Time Spent on Website, Total Visits, Last Activity, etc.The targert variable in this case is the column `Converted`.wich tells whether a past lead was converted or not wherein 1 means it was converted and 0 means it wasn't converted.

<a id="logistic regression"></a> 
## 3 Logistic Regression
Logistic regression is a linear model used in binary classification tasks where the target variable can take only 2 values such 0 or 1. Given a set of features the model predict the porability that  the target variable will take the value 1. The probabilty is computed using the logistic function. The it is compared to a threshold (0.5 usually), and if the probability is  greater than the threshold the target variable is classified as 1, Otherwise it is 0.
In terms of mathematical terms the logistic regression is has the following form:
$$g(X)=\sigma(W.X+b)$$
where:

- $\mathbf{X}$ :the input feautre vector
- $\mathbf{W}$: the Weights vector
- $\mathbf{b}$: the bias term
- $\mathbf{\sigma}$: the sigmoid function

$\mathbf{W}$ the  weight vector and $\mathbf{b}$ the bias term are the **parameters** of the model.They are updated during the training.By optimizing these parameters the model is able to make good predictions on new data.

For the implementation of the model, sklearn package is used.

<a id="preparation"></a> 
## 4 Data Preparation and Feature Engineering
 - Lowercase the columns name and remove the spaces.
 - Handle missing values.
 - Select relevant features using Mutual information and Coefficient of Correlation 
    - **The mutual information score** is used to measure the dependency between  2 categorical variables .We use it to tell how much the variables are   dependent to the target variable`converted`.
    ```
    def calculate_mi(series):
      return mutual_info_score(series,df.converted)
    
    
    df_mi = df[categorical].apply(calculate_mi)
    df_mi = df_mi.sort_values(ascending=False).to_frame(name="MI")
    df_mi
    ```
 - Split data into training, validation and test sets.
 - We transform the categories using One hot encoding.
 
 <a id="training"></a> 
 ## 5 Training 
 After the data is ready a logistic regression model can be trained on the training set. We made an instance of the class `LogisticRegression` from sklearn to define our model and we specify the solver `solver='liblinear'`.Then we use `fit()` to train the model.
 
<a id="evaluate"></a> 
## 6 Evaluating the model
To evaluate the permformance we use different metrics:
- Confusion matix
  - True positive: 57%
  - False positive: 3%
  - True negative: 34%
  - False negative: 3%
- Precision:0.9
- Recall :0.9
- ROC: 0.97
>- **The confusion matrix shows low number of false positive and false negative wich suggests that the model is making accuracte predictions.**
>- **The precision and recall values suggests that the model is correctly identifying a high proportion of positives and negatives samples.**
>- **The ROC is able to distinguish between negative and positive samples with high accuracy.**

<a id='conclusion'></a>
## Conclusion
We build a logistic regression model with accuracy of 92%.



