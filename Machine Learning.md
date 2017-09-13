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
### Stages
#### Given data
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

