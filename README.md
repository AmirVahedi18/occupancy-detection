# Occupancy Detection
#### **Experimental data used for binary classification (room occupancy) from Temperature, Humidity, Light and CO2. Ground-truth occupancy was obtained from time stamped pictures that were taken every minute.**

Dataset Source: https://archive.ics.uci.edu/ml/datasets/Occupancy+Detection+#

## Summery:

### 1. Get the data: 
Extract, import data, and put it into train set and test set.

### 2. Explore the data to gain insights
##### Training set info: 

<pre>
Int64Index: 17895 entries, 1 to 17895
Data columns (total 6 columns):
 #   Column         Non-Null Count  Dtype  
---  ------         --------------  -----  
 0   date           17895 non-null  object 
 1   Temperature    17895 non-null  float64
 2   Humidity       17895 non-null  float64
 3   Light          17895 non-null  float64
 4   CO2            17895 non-null  float64
 5   HumidityRatio  17895 non-null  float64
dtypes: float64(5), object(1)
memory usage: 978.6+ KB
</pre>


##### Histogram of the training set




##### Scatter Matrix of the training set





### 3. Data Preparation
Creating transformers and putting the into a pipeline to automate preprocessing step.

Transformers:
1. AttributeCombination: to combine the most correlated attributes to come up with new features
2. DivideDate: to divde the date feature into day, hour, month, and weekday
3. StandardScaler: feature scaling


### 4. Explore many different models and shortlist the best ones
Creating a function to evaluate each model on the training set (seen data) and evaluation set (unseen data) to present its performance.

##### Result of Logistic Regression:
<pre>
Accuracy on seen data: 99.1282
Precision score on seen data: 0.9648
Recall score on seen data: 0.9950
AUC seen: 99.2633
----------------------------------------
Accuracy on unseen data: 99.0277
Precision score on seen data: 0.9649
Recall score on seen data: 0.9899
AUC unseen: 99.0154
</pre>


##### Result of Stocastic Gradient Decsent:
<pre>
Accuracy on seen data: 99.1674
Precision score on seen data: 0.9649
Recall score on seen data: 0.9968
AUC seen: 99.3560
----------------------------------------
Accuracy on unseen data: 99.1338
Precision score on seen data: 0.9646
Recall score on seen data: 0.9955
AUC unseen: 99.2862
</pre>


##### Result of KNN:
<pre>
Accuracy on seen data: 99.5921
Precision score on seen data: 0.9879
Recall score on seen data: 0.9929
AUC seen: 99.4797
----------------------------------------
Accuracy on unseen data: 93.1210
Precision score on seen data: 0.8929
Recall score on seen data: 0.7660
AUC unseen: 87.0717
</pre>


##### Result of SVM:
<pre>
Accuracy on seen data: 99.1953
Precision score on seen data: 0.9652
Recall score on seen data: 0.9979
AUC seen: 99.4124
----------------------------------------
Accuracy on unseen data: 97.7592
Precision score on seen data: 0.9676
Recall score on seen data: 0.9248
AUC unseen: 95.8270
</pre>




##### Result of Random Forest:
<pre>
Accuracy on seen data: 100.0000
Precision score on seen data: 1.0000
Recall score on seen data: 1.0000
AUC seen: 100.0000
----------------------------------------
Accuracy on unseen data: 97.4742
Precision score on seen data: 0.9514
Recall score on seen data: 0.9277
AUC unseen: 95.7530
</pre>



##### Result of XGBoost:
<pre>
Accuracy on seen data: 99.5362
Precision score on seen data: 0.9807
Recall score on seen data: 0.9976
AUC seen: 99.6188
----------------------------------------
Accuracy on unseen data: 87.8402
Precision score on seen data: 0.6767
Recall score on seen data: 0.8121
AUC unseen: 85.4112
</pre>


**Overal Logistic Regression gives us the best performance!**

### 5. Hyperparameter Tuning (Fine-tune)
Fine tuning the logistic regression model: 

``Accuracy of 99.13937126636709 for parameters: {'C': 0.5, 'penalty': 'l2', 'solver': 'lbfgs'}``


### 6. Evaluate Final Model on the Test Set
Final Result on the fine-tuned model:

<pre>
Accuracy on test set: 97.8612
Precision score on test set: 0.9463
Recall score on test set: 0.9979
AUC on test set: 98.2728
</pre>








