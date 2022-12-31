# Machine-Learning
Dataset:
For this project we have used our own dataset which we have collected from people who have completed their bachelor’s recently and are either working or are currently pursuing/completed master’s. The dataset consists of 195 examples and has 13 attributes and a final result.
The attributes in the dataset are Age, Dependants, FGGrad, CGPA, Job, PayCheck, GradDegReq, Expertise, CareerShift, GradDegInterest, FinSupport, ActiveResearch, AcademicExposure.
For the data collection we first decided by interviewing and brainstorming on some of major factors which affect the decision to pursue master’s and collected the data by using a google form.
 


Implementation:
So for the implementation we decided on the following models with our own implementation and scikit implementation:

•	Logistic Regression (Scikit): 
We chose this as it is the baseline to check if a data is linearly separable or not.

•	SVM (Scikit): 
We implemented this to see if our data is separable well when projected into a different dimensional space

•	Decision Trees (Own, Scikit): 
As we have categorical and continuous data, we implemented decision trees to see if it needs a complex decision boundary.

•	Gradient Boosting (Scikit): 
From the results of the previous models we could say that the data is linearly separable very well. So, we implemented gradient boosting as it does gradient descent and performs well.

•	AdaBoost(Scikit) : 
From the results of the previous models we could say that the data is linearly separable very well. So, we implemented boosting on logistic regression to improve performance.

•	K-means (Own, Scikit): We implemented this unsupervised learning on our data as we were curious to see if an unsupervised model would cluster the data as well as a supervised learner or not. And see the reason behind the results.
 



Logistic Regression:
Below is the performance from the logistic regression.
Reasons for choosing logistic regression: 
1. Our data is of binary classification.
2. Most of our features are Boolean.
To check if the data is linearly separable.

Expected:
High accuracy, precision and recall if the data is linearly separable else not.

Actual results:
Accuracy:  0.8367346938775511
F1 score:  0.8571428571428571

The scores from the logistic regression are high and thus, we can say that the data is most probably linearly separable.


SVM:
Reasons for choosing SVM:
1. The output from the logistic regression is high. So, we wanted to see if any other projection of our data in other dimension space could provide us with better accuracy.

When we tuned the hyper-parameters for the SVM, we have landed on linear kernel with some C allowing some soft margin.

Expected:
Better or equal performance as logistic regression.
Actual result:
Accuracy:  0.7755102040816326
F1 score:  0.8070175438596492

Speculations:
1. The dataset is small. So, the data points near the decision boundary (Support Vectors) may not be true representation of the actual decision boundary, thus may form false maximum margin classifier boundary.




Decision Tree:
Reasons for choosing:
1. The dataset contains noise as it’s collected in real time and may not be engineered properly.
2. The dataset contains both numerical and categorical data.
3. To see if our data needs a complex decision boundary.
Expected results:
Better results if our data is not linearly separable. Otherwise, not.
Actual results:
The accuracy is a little lesser when compared to logistic regression.
Accuracy :  0.7959183673469388
F1 score :  0.8148148148148149
 
Speculation:
1. When we tuned the hyper parameters, we got the better result at depth = 1 which is why we got better results with logistic regression. We got the same result for accuracy until depth = 4 which tells us that the initial split is enough to classify the data as accurately as the tree with depth = 4.
2. We may have the problem of underfitting but the training error and testing error has remained same for all the four depths.
2. The size of the dataset is pretty small which makes it enough for a decision stump to classify it. Had the data been larger, we might have gotten better results with higher depth trees. But in our case, decision stump was enough.

Own implementation of decision trees:
Accuracy :  0.7959183673469388
F1 score :  0.8148148148148149
 
Our own implementation of decision trees has given us the exact same result as the scikit learn decision tree classifier.




Gradient Boosting:
Reasons for choosing:
The gradient boosting works well when the weak learners(decision stump, logistic regression) are involved. These learners work well with gradient descent making it a perfect algorithm to apply to our data.
Expected results:
Better results than other algorithms and almost similar to logistic regression.
Actual results:
Better accuracy than all other algorithms implemented and almost similar to logistic regression.
Accuracy :  0.8163265306122449
F1 score :  0.8474576271186439
 
Speculation:
1. The weak learners have picked up well on gradient boosting giving better results.





Adaboost with logistic regression:
Reasons for choosing:
1. Boosting usually gives better results than individual weak learners.
2. Logistic regression gave better accuracy. So, boosting on top of it is expected to give better results.
Expected:
Better results than logistic regression.
Actual:
Lesser accuracy than logistic regression.
Accuracy :  0.7755102040816326
F1 score :  0.7999999999999999

Speculation:
1. Logistic regression works better if the data is linearly separable whereas boosting algorithms are tree based and works on information gain or gini impurity concepts. They perform well on dataset where you dont have linear relationship. 
2. The weak learner works well with gradient descent where as the adaboost focuses on weighing the wrongly classified examples which makes sense to not have better accuracy than logistic regression.






K-means clustering:
We wanted to see if our data is performing well if clustered into two groups.
Below are the results:
 
Anything after cluster k = 4 doesn’t impact much on our data. So, it seems logical to have 4 clusters for our data. For k = 2, we have the following figures when compared against the original dataset.
Confusion Matrix : 
 [[ 44   3]
 [ 47 101]]
Accuracy :  0.7435897435897436
F1 score :  0.8015873015873016
Which is exactly same as our own implementation for k-means. Hence, we could say that the data could be categorized into two clusters and that would give us acceptable results while clustering a new data point.

 


