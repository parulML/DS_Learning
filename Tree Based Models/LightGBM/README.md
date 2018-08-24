https://www.analyticsvidhya.com/blog/2016/04/complete-tutorial-tree-based-modeling-scratch-in-python/

Tree Based Models can do following tasks efficiently :
1) Create non-linear Models
2) Both Classification/Regression

In this we split the data into two or more sub-population based on most significant splitter/differentiater in input variables.

Descision tress are of two types based on the type of target variables:
1) Categorical variable decision tree
2) Continuous variable decision tree

Basic terminologies used in decision trees:
1) Root node : Represents entire population which further gets divided into 2 or more homogeneous sets
2) Spliting : Process of dividing a node into 2 or more sub-nodes
3) Decision Node : When a node splits into two or more sub-nodes it's termed as decision 	node
4) Leaf/terminal Node : Nodes that do not split are called leaf or terminal nodes
5) Pruning : When we remove sub nodes of decision tree it's called pruning which is opposite of splitting
6) Parent/Child Nodes : A node that is divided into sub nodes is called parent node and sub-nodes are called child nodes

Advantages of decision tree:
1) Easy to understand
2) Useful in data exploration
3) Less data cleaning required
4) Data type is not a constraint
5) Non-parametric method : probability distribution does not matter

Disadvantages:
1) Over-fitting
2) Not fit for continuous variables : While working with continuous variables it looses information while categorising variables into different categories

Regression vs Classification trees:
Since in decision trees terminal leaves are at the bottom hence decision trees are upside down.

Similarities and differences between classification and regression trees:
1) In regression tree value obtained by terminal node is mean response of observations falling into that region
2) In case of classification value obtained by terminal node is mode of observations falling into that region
3) Spliiting process continues until a user defined splitting criterion is reached for example we can tell an algorithm to stop when number of observations er node become less than 50
4) They follow recursive binary tree process
5) They follow top-down greedy approach known as recusrsive binary splitting because they start splitting from root node from top to the terminal node making sure that it uses the best predictor hence it's called greedy
6) In both cases , splitting results into fully grwon trees until stopping criterion is reached which might lead to overfit to overcome this problem pruning is used.

How does a tree decide where to split??
The decision of making stratergic split heavily affects tree's accuracy, which is different for classification and regression trees. decision tree uses multiple algos to decide the best split
The creation of sub nodes increases the homogenity of the sub nodes. Decision tree splits the nodes on all available variables and the decide the split which is most homogeneuos sub-node.

The algo selection is based on type of target variable. Let's look at four commonly used algos.

1) Gini Index:
Gini index says if we select two observations at random then they belong to same class and probability of this is 1 if the population is pure.
1) it works with categorical target variable "failiure" and "success"
2) It performs only bimary splits
3) Higher the gini value higher will be homogenity
4) CART uses GINI method to create splits

Steps to calculate Gini for a split:
1) Calculate Gini for sub-nodes using sum of square of proability of success and failire of that particular node (p^2+q^2)
2) Calculate gini for split using weighted gini score of each node of that split

Decision Tree, Algorithm, Gini IndexSplit on Gender:

Calculate, Gini for sub-node Female = (0.2)*(0.2)+(0.8)*(0.8)=0.68
Gini for sub-node Male = (0.65)*(0.65)+(0.35)*(0.35)=0.55
Calculate weighted Gini for Split Gender = (10/30)*0.68+(20/30)*0.55 = 0.59
Similar for Split on Class:

Gini for sub-node Class IX = (0.43)*(0.43)+(0.57)*(0.57)=0.51
Gini for sub-node Class X = (0.56)*(0.56)+(0.44)*(0.44)=0.51
Calculate weighted Gini for Split Class = (14/30)*0.51+(16/30)*0.51 = 0.51
Above, you can see that Gini score for Split on Gender is higher than Split on Class, hence, the node split will take place on Gender.

Chi-Square Analysis

This algo finds statistical difference between sub-node and parent node. We measure it by sum of square of difference between observed frequency and target frequency
Few points about Chi-Square analysis:
1) It can perform two or more splits
2) Higher the value of Chi ssquare higher is the statistical difference between sub-node and parent node
3) Chi-squre of each node is calculated using the formula (expected-actual)^2/(expected)^1/2
4) It generates a tree called CHAID(Chi-Squared automatic interaction detec
tor)

Steps to calculate Chi-Squre for a split:
1) calculate chi-square for individual nodes by calculating deviation of success and failiure
2) calculate chi-square of spilt using sum of chi-square of success and failiure of each node of split

Information Gain
Less impure node needs less information to describe it. Informartion theory is used to describe degree of disorganisation and this is called entropy.
If the sample is completely homogeneous it will have 0 entropy and if the sample is equally distributed it will have 1 entropy.

Formula to calculate entropy:
Entropy = -p log q -q log p

Where p and q is probability of success and failiure. Entropy is used with categorical target variable. it chooses the split with lowest entropy compared to parent node.
Lesser the entropy better is the split.

Entropy for parent node = -(15/30) log2 (15/30) – (15/30) log2 (15/30) = 1. Here 1 shows that it is a impure node.
Entropy for Female node = -(2/10) log2 (2/10) – (8/10) log2 (8/10) = 0.72 and for male node,  -(13/20) log2 (13/20) – (7/20) log2 (7/20) = 0.93
Entropy for split Gender = Weighted entropy of sub-nodes = (10/30)*0.72 + (20/30)*0.93 = 0.86
Entropy for Class IX node, -(6/14) log2 (6/14) – (8/14) log2 (8/14) = 0.99 and for Class X node,  -(9/16) log2 (9/16) – (7/16) log2 (7/16) = 0.99.
Entropy for split Class =  (14/30)*0.99 + (16/30)*0.99 = 0.99



Reduction in Variance
Till now, we have discussed the algorithms for categorical target variable. Reduction in variance is an algorithm used for continuous target variables (regression problems). This algorithm uses the standard formula of variance to choose the best split. The split with lower variance is selected as the criteria to split the population:

Decision Tree, Reduction in Variance

Above X-bar is mean of the values, X is actual and n is number of values.

Steps to calculate Variance:

Calculate variance for each node.
Calculate variance for each split as weighted average of each node variance.
Example:- Let’s assign numerical value 1 for play cricket and 0 for not playing cricket. Now follow the steps to identify the right split:

Variance for Root node, here mean value is (15*1 + 15*0)/30 = 0.5 and we have 15 one and 15 zero. Now variance would be ((1-0.5)^2+(1-0.5)^2+….15 times+(0-0.5)^2+(0-0.5)^2+…15 times) / 30, this can be written as (15*(1-0.5)^2+15*(0-0.5)^2) / 30 = 0.25
Mean of Female node =  (2*1+8*0)/10=0.2 and Variance = (2*(1-0.2)^2+8*(0-0.2)^2) / 10 = 0.16
Mean of Male Node = (13*1+7*0)/20=0.65 and Variance = (13*(1-0.65)^2+7*(0-0.65)^2) / 20 = 0.23
Variance for Split Gender = Weighted Variance of Sub-nodes = (10/30)*0.16 + (20/30) *0.23 = 0.21
Mean of Class IX node =  (6*1+8*0)/14=0.43 and Variance = (6*(1-0.43)^2+8*(0-0.43)^2) / 14= 0.24
Mean of Class X node =  (9*1+7*0)/16=0.56 and Variance = (9*(1-0.56)^2+7*(0-0.56)^2) / 16 = 0.25
Variance for Split Gender = (14/30)*0.24 + (16/30) *0.25 = 0.25
Above, you can see that Gender split has lower variance compare to parent node, so the split would take place on Gender variable.

Until here, we learnt about the basics of decision trees and the decision making process involved to choose the best splits in building a tree model. As I said, decision tree can be applied both on regression and classification problems. Let’s understand these aspects in detail.


Tree Pruning Steps:
1) We first make the decision tree to a large depth.
2) Then we start at the bottom and start removing leaves which are giving us negative returns when compared from the top.
3) Suppose a split is giving us a gain of say -10 (loss of 10) and then the next split on that gives us a gain of 20. A simple decision tree will stop at step 1 but in pruning, we will see that the overall gain is +10 and keep both leaves.


Are tree based models better than linear models?
1) If the relationship between dependent & independent variable is well approximated by a linear model, linear regression will outperform tree based model.
2) If there is a high non-linearity & complex relationship between dependent & independent variables, a tree model will outperform a classical regression method.
3) If you need to build a model which is easy to explain to people, a decision tree model will always do better than a linear model. Decision tree models are even simpler to interpret than linear regression!


What are ensemble methods in tree based modeling ?
The literary meaning of word ‘ensemble’ is group. Ensemble methods involve group of predictive models to achieve a better accuracy and model stability. Ensemble methods are known to impart supreme boost to tree based models.

Like every other model, a tree based model also suffers from the plague of bias and variance. Bias means, ‘how much on an average are the predicted values different from the actual value.’ Variance means, ‘how different will the predictions of the model be at the same point if different samples are taken from the same population’.

You build a small tree and you will get a model with low variance and high bias. How do you manage to balance the trade off between bias and variance ?

Normally, as you increase the complexity of your model, you will see a reduction in prediction error due to lower bias in the model. As you continue to make your model more complex, you end up over-fitting your model and your model will start suffering from high variance.

A champion model should maintain a balance between these two types of errors. This is known as the trade-off management of bias-variance errors. Ensemble learning is one way to execute this trade off analysis.

Some of the commonly used ensemble methods include: Bagging, Boosting and Stacking. In this tutorial, we’ll focus on Bagging and Boosting in detail.


What is Bagging? How does it work?
Bagging is a technique used to reduce the variance of our predictions by combining the result of multiple classifiers modeled on different sub-samples of the same data set. The following figure will make it clearer:

Create Multiple DataSets:
Sampling is done with replacement on the original data and new datasets are formed.
The new data sets can have a fraction of the columns as well as rows, which are generally hyper-parameters in a bagging model
Taking row and column fractions less than 1 helps in making robust models, less prone to overfitting

Build Multiple Classifiers:
Classifiers are built on each data set.
Generally the same classifier is modeled on each data set and predictions are made.

Combine Classifiers:
The predictions of all the classifiers are combined using a mean, median or mode value depending on the problem at hand.
The combined values are generally more robust than a single model.

It can be theoretically shown that the variance of the combined predictions are reduced to 1/n (n: number of classifiers) of the original variance, under some assumptions.

There are various implementations of bagging models. Random forest is one of them and we’ll discuss it next.


Random Forest is a versatile machine learning method capable of performing both regression and classification tasks. It also undertakes dimensional reduction methods, treats missing values, outlier values and other essential steps of data exploration, and does a fairly good job. It is a type of ensemble learning method, where a group of weak models combine to form a powerful model.

XGBOOST Tutorial
https://www.analyticsvidhya.com/blog/2016/03/complete-guide-parameter-tuning-xgboost-with-codes-python/






What is Covariance : Property of a function of retaining it's form even when the variables get linearly transfored. 