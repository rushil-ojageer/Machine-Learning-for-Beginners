# Machine Learning
## Intro
Traditional Artificial Intelligence (AI) algorithms are designed to solve specific problems. Deep blue was purpose built for playing chess. Game enemy AI are built to attack the player. Most traditional methods of AI approximate a solution for a specific problem.

Machine learning tries to learn more general concepts and work in changing dynamic contexts.

## Types of Learning
There are various ways for learning to happen.

* **Supervised Learning:** The algorithm is given inputs as well as the expected output in a training set. The goal is to learn general rules that map inputs to the correct outputs for future inputs.

* **Unsupervised Learning:** The algorithm is given inputs without expected outputs. The goal is to discover hidden patterns that can be used for future learning.

* **Reinforcement Learning:** The algorithm works with a given input without the expected outputs, and a specific goal that it should aim to achieve. The algorithm should determine if it is closer to it's goal or not.

## Categories Based on Outputs

* **Classification:** Inputs are categorised into two or more groups. Classification generally uses supervised learning.

* **Regression:** Similar to classification, where the outputs are not discrete. There may be categories that were previously unknown.

* **Clustering:** Inputs are categorised into groups, however, the groups are not known. Clustering generally uses unsupervised learning.

## Data
Collecting and preparing data is one of the most important part of machine learning.
The attributes that describe an object are called FEATURES.
The classification of that object is called a LABEL.

* Remove redundant features. E.g. temperature in Fahrenheit, and temperature in Celsius is redundant.

* Remove features that don't add value to classifying the object.

* Ensure no single feature automatically determine the label.

# Getting your hands dirty

## Getting Setup with Python
Ensure that you have the below software installed.

Software you require
* [Python 2.7](https://www.python.org)
* [Anaconda (Recommended)](https://www.continuum.io)

### Hello World

```
from sklearn import tree

#A set of features of fruit
#Weight as an integer, 1 = rough 2 = smooth
features = [[140, 1],[130, 1],[150, 0],[170, 0]]
#Classification of the fruit. 0 = orange 1 = apple
labels = [0, 0, 1, 1]

clf = tree.DecisionTreeClassifier()
clf = clf.fit(features, labels)

print clf.predict([[160, 0]])
```

### Iris Flower Classification
```
from sklearn.datasets import load_iris
from sklearn import tree
import numpy as np

iris = load_iris()
test_idx = [0, 50, 100]

#training data
training_target = np.delete(iris.target, test_idx)
training_data = np.delete(iris.data, test_idx, axis = 0)

#testing data
testing_target = iris.target[test_idx]
testing_data = iris.data[test_idx]

clf = tree.DecisionTreeClassifier()
clf.fit(training_data, training_target)

print testing_target
print clf.predict(testing_data)

#vis code
from sklearn.externals.six import StringIO
import pydot
dot_data = StringIO()  
tree.export_graphviz(clf, out_file=dot_data,  
                         feature_names=iris.feature_names,  
                         class_names=iris.target_names,  
                         filled=True, rounded=True,  
                         special_characters=True)  
graph = pydot.graph_from_dot_data(dot_data.getvalue())  
graph.write_svg("iris.svg")

print testing_data[1], testing_target[1]
print iris.feature_names, iris.target_names

```

# References
* [Google Developers YouTube](https://www.youtube.com/playlist?list=PLOU2XLYxmsIIuiBfYad6rFYQU_jL2ryal)