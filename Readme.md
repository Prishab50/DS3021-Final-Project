# Banana Quality Project

## Introduction and Background 

**Background:** Our original idea for this project utilized a Shark Tank dataset to predict whether or not a contestant received a deal on their startup. However, after encountering large amounts of irrelevant features, many missing values, and an overwhelming amount of binary features that did not accurately predict the target variable, we decided to switch courses. We instead sought a dataset that contained a good mix of numerical and categorical features that could actually be used to predict a declared target variable. 

Upon searching for such a dataset, my roommate was experiencing a grave predicament: our old stash of bananas had begun to wither. In order to decide whether these bananas could still be eaten, utilized for banana bread, or thrown out, the quality of the banana needed to be assessed urgently. That’s where our model comes in. 

The Banana Quality Dataset from Kaggle [(Dataset)](https://www.kaggle.com/datasets/mrmars1010/banana-quality-dataset/data) provides an overview of 1000 banana samples, including features such as region, variety, ripeness, length, and more. Most importantly, it provides an evaluation of quality— presented as both a numerical score and categorical classification— to determine the banana’s appeal and potential for use. This measure of quality takes into account factors such as appearance, texture, and lack of defects. 

With this project, we find the best model to predict banana quality based on other properties of the banana sample, including those of its origin as well as physical features. We create two models— one that predicts the numerical quality score and one that predicts the quality category (Unripe, Processing, Good, or Premium) of the banana. Furthermore, we determine which features most directly contribute to these target variables. With our work, the quality—and therefore usefulness—of a banana can be thoroughly assessed and predicted by the observer, rather than using mere intuition. 




## Conclusion

### Model Specific Results: 

**Results of Regression Model:**  

The linear regression model that we created performs very well on both known and unknown banana data and generates a highly accurate prediction of the quality score of the banana. Overall, according to normalized RMSE, the model’s predictions of score were typically around 0.025 points off from the true value, which is impressive considering the range of the score is 3.06. Further evaluation shows that a linear model is a very good fit for the data, as the residuals follow a random, normalized distribution. 

An analysis of the feature coefficients of the linear regression model reveals that ripeness, sugar content, and length contribute most directly to the overall quality score of the banana. This means that these features should be emphasized when assessing the quality of a banana. On the other hand, the altitude and rainfall of the area where the banana was grown have the least effect on the quality of the banana. 


**Results of Decision Tree Model:**  

The decision tree model we created performed well on the test dataset with an accuracy of 0.88 on the test set. However, a more in-depth analysis revealed the weakness and strengths of the model. The model is strong in classifying “Good” and “Processing” categories, with F1 scores above 0.85, demonstrating a strong balance between precision and recall. On the other hand, the “Premium” class has an F1 score of 0.57 indicating the model struggles to identify the highest quality bananas and is confusing them with nearby classes. Looking at the confusion matrix, the model has difficulty separating the “Premium” bananas from the “Good” bananas. This pattern is likely driven by the class imbalance in the dataset along with feature similarity for the “Good” and “Premium” bananas. Because “Premium” bananas are less frequent and don’t differ drastically from “Good” bananas, the tree is unable to learn clear boundaries between the two. 

The macro-averaged ROC AUC score of 0.8586 also suggests the model performs well overall in distinguishing between classes, even if not for each class individually. When broken down into the individual AUC scores for each class, the same trend as before is clear: “Premium” has the weakest separability and is the weakness of the model.

Overall, the decision tree does provide a strong baseline performance, but it performs much weaker on the minority class highlighting its limitations.


### Final Evaluation: 

**Which model is better:**  

By a direct comparison of the two models’ performance, we determined the best model for our goals to be the linear regression model. While the decision tree model did perform well, it has clear limitations with a weaker performance on the “Premium” class due to class imbalance and overlapping feature values between categories. These issues make it less reliable for consistent results across all the classes.

The linear regression model, in contrast, performed very strongly with a very high R2 and a low RSME across the test set. Its predictions are both accurate and consistent across the dataset. Moreover, the quality categories are derived from the continuous quality score so the regression model is more representative of the fundamental structure of the data.

Thus, the linear regression model is preferred due to higher predictive accuracy and direct representation of a banana’s quality. 

**Relation to Question:**

Our model demonstrates that a banana’s quality is directly linked to its physical and categorical features which can be used to determine a banana’s appeal and potential for use. The model predicts a quality score between 1 - 4 (with a higher score corresponding to better quality) that can then be used to objectively determine how to use the banana.


**Possible Limitations:**

The dataset used was clean and structured before preprocessing with minimal noise or missing values. In practice, the dataset being used is unlikely to be in as good shape; instead, it will likely include errors, missing values, and inconsistencies that would lead to a lower model accuracy. 
There is a risk of data leakage with features that are closely tied to the target variable. For instance, ripeness index is strongly associated with the quality of a banana and could potentially lead to data leakage that would create an overly optimistic model.
The linear regression model is assuming a linear relationship between the variables and the quality score and could end up oversimplying more complex interactions between them.


## Contributions

**Caroline:**  
* Data Preprocessing 
  * Did EDA to compare two possible target variables (quality score vs category)
  * Pre-Processed X variables
* Linear Regression Model
  * Built model, including preprocessor and pipeline
  * Used evaluation metrics such as RMSE, R2, residual plots, and cross-validation and explained their meaning
  * Evaluated coefficients to see which features contribute more to target variable
* Wrote Intro/Background and Research question
* Wrote part of conclusion
  * Results of regression model



**Prisha:** 

* Data Preprocessing
  * Did EDA on numerical and categorical features in tandem with the target variables to determine what features may play the largest role in the models as well as check distributions prior to model building
* Decision Tree Model
  * Built model, including encoding target variable and pipeline
  * Used evaluation metrics such as Accuracy, Confusion Matrix, and ROC AUC Curve + Scores and explained their meaning
* Wrote part of conclusion
  * Results of decision tree model
  * Final evaluation
