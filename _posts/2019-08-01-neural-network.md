---
title: " what is Neural Network in Deep Learning"
layout: post
excerpt: "Here’s something that might surprise you neural networks aren’t that complicated! The term “neural network” gets used as a buzzword a lot, but in reality they’re often much simpler than people imagine. This post is intended for complete beginners. We’ll understand how neural networks work while implementing one from scratch in Python."
last_modified_at: 2019-08-01T12:20:01-05:00
tags:
  - Neural Network
  - Deep Learning
  - Machine Learning
  - Python
  - Derivatives
  - Math
---
# Let's start with very simple introduction:
Neural networks are simple. They just perform a dot product with the input and weights and apply an activation function. When weights are adjusted via the gradient of loss function, the network adapts to the changes to produce more accurate outputs. how easy !!!

# What is a Neural Network?
A Neural Network is a collection of neurons connected by synapses. This collection is organized into three main layers: the input layer, the hidden layer, and the output layer. You can have many hidden layers, which is where the term deep learning comes into play. In an artificial neural network, there are several inputs, which are called features, and produce a single output, which is called a label.

![Neural Network](_screenshots/NN.png)

# Let's start Combining Neurons into a Neural Network
Our neural network will model a single hidden layer with three inputs and one output. In the network, we will be predicting the Sale Price of our house based on the inputs of No.Bedroom and the Quality of the house. Our test sale price is the output. Here's our sample data of what we'll be training our Neural Network on:

| No.BedRoom and Quality | SalePrice($) |
| ------------ | ------------ |
| (2,7) | 94 |
| (1,3) | 89 |
| (3,9) | 83 |
| (4,7) | ? |

As you may have noticed, the ? in this case represents what we want our neural network to predict.

# Let's start coding Neural Network from scratch using python
Open up a new python file. You'll want to import numpy as it will help us with certain calculations.
# Module 1 : Input Layer
First, let's import our data as numpy arrays using np.array. We'll also want to normalize our inputs, but our output is a sale price from 10-100. Therefore, we need to scale our data by dividing by the maximum value for each variable.
```python
import numpy as np

# X = (No.Bedroom, Quality), y = score on salePrice
X = np.array(([2, 7], [1, 3], [3, 9]), dtype=float)
y = np.array(([94], [89], [83]), dtype=float)

# scale units
X = X/np.amax(X, axis=0) # maximum of X array
y = y/100 # max salePrice is 100
```
# Module 2 :Feedforward Propagation for Hidden to Output Layer
> **Weights assigned to Edges in Network**
Neural Network is a finite graph/network with directed edges/links. Weight is assigned to each in the graph/network.

first we'll need to define two sets of random weights. One to go from the input to the hidden layer, and the other to go from the hidden to output layer. we'll generates our weights randomly using np.random.randn().
```python
#weights
W1 = np.full((2,3),0.5) # Input Layer to Hidden Layer
W2 = np.full((3,1),0.5) # Hidden Layer to Input Layer
```
> **Activation Function apply to Nodes in Network**
Neural Network is a finite graph/network with directed edges, in which each vertex/node represents a neuron. Each node calculates a weighted sum of its inputs, and transmits along its output edges the value of some function of this weighted sum

Next we need to define some function to transform the weights. we need to apply the activation function. The role of an activation function is to introduce nonlinearity. An advantage of this is that the output is mapped from a range of 0 and 1, making it easier to alter weights in the future.

There are many activation functions. we'll use one of the popular ones the sigmoid function
```python
def sigmoid(self, s):
    # activation function 
    return 1/(1+np.exp(-s))
```
**Once we have all the variables set up, we are ready to write our feedforward propagation function.**

# Step 1:
lets first calculate the dot product as 'z2' between the input as 'X' and first layer weights(input to hidden) as 'W1'.
```python
z2 = np.dot(X,W1) # dot product of X (input) and first set of weights
print(z2)
"""
[[0.83333333 0.83333333 0.83333333]
 [0.44444444 0.44444444 0.44444444]
 [0.83333333 0.83333333 0.83333333]]
 """
```
# Step 2:
Next we'll need to apply activation function using 'z2' as a input in hidden layer (Node's are activation function in the Hidden layer)
```python
a2 = sigmoid(z2) # activation function
print(a2)
"""
[[0.69705928 0.69705928 0.69705928]
 [0.60931754 0.60931754 0.60931754]
 [0.69705928 0.69705928 0.69705928]]
 """
```
# Step 3:
Next we'll calculate the dot product as 'z3' between 'a2' as a input from activation function and second layer weights (hidden to output) as 'W2'.
```python
z3 = np.dot(a2,W2) # dot product of hidden layer (a2) and second set of  weights
print(z3)
"""
[[1.04558893]
 [0.91397631]
 [1.04558893]]
"""
```
#Step 4:
In final we'll apply activation function as 'y' output variable using 'z3' as a input form in hidden layer (Node's are activation function in the Hidden layer)
```python
y = sigmoid(z3) # final activation function
print(y)
"""
[[0.73992695]
 [0.71381315]
 [0.73992695]]
"""
```
**And, There You Go! Build A Neural Network !!!**

# The "learning" of our network
Theoretically, with those weights, our neural network calculated unexpected results. Because we used random weights to build a network. Next we need to tune those random weights, so that we'll get the expected results.



