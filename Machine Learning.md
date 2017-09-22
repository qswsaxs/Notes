# Machine Learning
## Class 1: Forming of learning problem
### Train set & Test set
- We generally assume that the training and test examples are independently drawn from the same overall distribution of data
- We call this "i.i.d" which stands for "independent and identically distributed"
- If examples are not independent, requires **collective classificartion**
- If test distribution is different, requires **transfer learning**
### ML in a Nutshell
- Three components:  
1. **Representarepresentation**
2. **Optimization**  
3. **Evaluation**
### ML in practice
- Understand domain, prior knowledge, and goals
- Data integration, selection, cleaning, pre-processing, etc.
- Learn models
- Interpret results
- Consolidate and deploy discovered knowledge
### Lessons Learned about Learning
- Different search methods' advantages and disadvantages
## Class 2:Decision Trees
### Function Approximation
#### Problem Setting
- Set of possible instances X
- Set of possible labels Y
- Unknown target function f:X-Y
- Set of function hypotheses H={h|h:X-Y}
#### Input:
- Training examples of unknown target function f  
*{(x1,y1),(x2,y2),...,(xn,yn)}*
#### Output:
- Hypothesis h belongs to H best approximates f
### Decision Tree Learning
#### Problem Setting:
- Set of possible instances X(contains feature vectors)
*such as <Humidity=low,Wind=weak,Outlook=rain,Temp=hot>*
- Unknown target function f:X-Y(Y is discrete)
- Set of function hypotheses H
*Each hypotheses h is a decision tree*
*trees sorts x to leaf, which assigns y*
![Decision Tree Example](https://image.slidesharecdn.com/l7decision-treetable-130318112451-phpapp01/95/l7-decision-tree-table-21-638.jpg?cb=1363605932)
### Stages of batch machine learning
#### Given __labeled__ data
- X & Y
#### Train the model:
- model<-classifier.train(X,Y)
#### Apply the model to new data:
- y<-model.predict(x)
### Decision Tree Induced Partition
- What a dicision tree really do is dividing the instance(feature) space into axis-parallel hyper-rectangles
- Each rectanglar region is labeled with one label
### Expressiveness
- Decision trees can represent any boolean function of the input attributes
- In the worst case, the tree will require exponentially many nodes
- As the depth increases, the hypothesis space grows
### Preference bias: Ockham's razor
- Entities are not to be multiplied beyond necessity
- In this case, we are trying to find the simplist tree that fits the features
### Basic Algorithm for Top-Down Induction of Decision Trees
ID3 Algorithm:
```
node = root of decision tree
Main loop:  
1. A <- the "best" decision attribute for the next node
2. Assign A as decision attribute for node
3. For each value of A, create a new descendant of node
4. Sort traning examples to leaf nodes
5. If training examples are perfectly classified, stop.
Else, recurse over new leaf nodes
```
How do we choose which attributes are best?
### Choosing the Best Attribute
**Key problem:** Choosing which attribute to split a given set of examples
#### Some possibilities are:
 1. **Ramdom**
 2. **Least-Values**: Attribute with the smallest number of possible values
 3. **Most-Values**: Attribute with the largest number of possible values
 4. **Max-Gain**: Attribute with the largest expected information gained(*ID3* used)

 **Idea:** a good attribute splits the examples into subsets that are ideally "all positive" or "all negative"
 ### Information Gain
 #### Impurity/Entropy(informal)
 - **Entropy:** Measures the level of impurity in a group
 ![Compute entropy](http://www.saedsayad.com/images/Entropy_3.png)  
It is the expected number of bits needed to encode a randomly drawn value of X(under most efficient code)
*From information theory(Huffman code)*
![](https://i.stack.imgur.com/1fEJE.png)  
Information Gain = entropy(parent)-[(weighted)average entropy(children)]

## Class 3: k-Nearest Neighbor & Instance-based Learning
### Stages of batch machine learning
#### Given __labeled__ data
- X & Y
#### Train the model:
- model<-classifier.train(X,Y)
#### Apply the model to new data:
- y<-model.predict(x)
## Class 4: Evaluation
### Classification Metrics
accuracy=# correct predictions/# test instance
error=1-accuracy
### Confusion Matrix
- Given a dataset of P positive instances and N negative instances

|Predicted|class|matrix
| ------ | ------ | ----|
|   | Yes | NO |
| Yes | TP | FN |
| No  | FP | TN |
- accuracy=(TP+TN)/(P+N)
- precision=TP/(TP+FP)
- recall=TP/(TP+FN)

### Training Data and Test Data
- Traning data: data used to build the model
- Test data: new data, not used in the training
- Need to avoid overfitting
### Comparing Classifiers
Idea:divide full data set into n parts
![n-fold cross validation](http://chrisjmccormick.files.wordpress.com/2013/07/10_fold_cv.png)  
### Optimizing Model Parameters
loop for t trials
1. randomize data set
2. perform k-fold CV(Compute learning curve over each training/testing split)   

Finally, compute statistics over t*k test performance
### Learning Curve
- Shows performance versus the # training examples
- Compute learning curve over each training/testing split (taking average to have the learning curve)

## Class 5: Linear Regression
from intro:
![Comparison of Learning Methods](https://image.slidesharecdn.com/hutter1-120821071909-phpapp02/95/introduction-to-statistical-machine-learning-65-728.jpg?cb=1345533592)
### Regression
Given:
- Data X
- Corresponding labels Y
- Trying to figure out a curve fitting the data
### Linear Regression
- Hypothesis
y'=a0x0+a1x1+a2x2+...+adxd=**a*****x**
Assume x0=1
- Fit model by minimizing sum of squared errors
- Cost Function (Objective function)
J(**a**)=(average of squares when the predictor is y'=**a*****x**)/2
- Fit by solving **min** J(**a**)
### Intuition Behind Cost Function
There is only one minimum.
![](https://qph.ec.quoracdn.net/main-qimg-7e46f059685ebb2d7c6b365f0fff9114)
### Basic Search Procedure
- Choose initial value for **a**
- Before we reach a minimum:
Choose a new value for **a** to reduce J(**a**)
### Gradient Descent	 

1.Initialize **a**
2.Repeat until convergence:
**a**=**a**- α *gradient(J(**a**))

α is called the learning rate (small,e.g. 0.5)
- Assume convergence when ||**a**'-**a**||(2-norm)<e
- To achieve simultaneous update:   
At the start of each GD iteration, compute **a*****x**   
Then use this stored value in the update step loop
### Choosing α
To see if gradient descent is working, print out the function value each iteration