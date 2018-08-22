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
3) Decision Node : When a node splits into two or more sub-nodes it's termed as decision node
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
6) In both cases , splitting results into fully grwon trees until stopping criterion is reached which might lead to overfit to overcome this problem prining is used.

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









What is Covariance : Property of a function of retaining it's form even when the variables get linearly transfored. 