---
title: "Basic Linear Algebra for Machine Learning: (Learn Day:1)"
layout: post
excerpt: "A good understanding of linear algebra is essential for understanding and working with many machine learning and deep learning algorithms."
last_modified_at: 2019-08-23T11:06:01-05:00
tags:
  - Linear Algebra
  - Python
  - Math
---
## Why Linear Algebra?
The concepts of Linear Algebra are crucial for understanding the theory behind Machine Learning and Deep Learning. They give you better intuition for how algorithms really work under the hood, which enables you to make better decisions. This post will give you an introduction to the most important concepts of Linear Algebra that are used in Machine Learning.

## Topics covered?
The core data structures behind Machine Learning and Deep Learning are Scalars, Vectors, Matrices and Tensors. Programmatically, let’s solve all the basic linear algebra problems using these.

Scalars, Vectors, Matrices and Tensors
- A scalar is a single number
- A vector is an array of numbers.
- A matrix is a 2-D array
- A tensor is a n-dimensional array with n>2

## Scalars
Scalars are single numbers and are an example of a 0th-order tensor.Few built-in scalar types are int, float, complex, bytes, Unicode in Python.

```python
a = 7
b = 9.6
print(type(a))
print(type(b))
print(a + b)
print(a - b)
print(a * b)
print(a / b)
"""
<class 'int'>
<class 'float'>
16.6
-2.5999999999999996
67.2
0.7291666666666667
"""
```
## Vector
A Vector is an ordered array of numbers and an example of 1st-order tensor. A Vector has just a single index, which can point to a specific value within the Vector.

```python
import numpy as np
x = [1, 2, 3]
y = np.array([1,2,3,4])

print(x)
print(y)
print(type(x))
print(type(y))

"""
[1, 2, 3]
[1 2 3 4]
<class 'list'>
<class 'numpy.ndarray'>
"""
```
## Matrices
A Matrix is an ordered 2D array of numbers and it has two indices and are an example of 2nd-order tensors. A Matrix can have multiple numbers of rows and columns. Note that a Vector is also a Matrix, but with only one row or one column.
```python
import numpy as np
x = [[1,2],[3,4]]
y = np.matrix([[1,2],[2,3]])

print(x)
print(y)
print(type(x))
print(type(y))

"""
[[1, 2], [3, 4]]
[[1 2]
 [2 3]]
<class 'list'>
<class 'numpy.matrix'>
"""
```

# Few Matrices Operations:

## Matrix Addition
> C = A + B (Shape of A and B should be equal)

Matrix-Matrix Addition is fairly easy and straightforward. You just add each value of the first Matrix with its corresponding value in the second Matrix.
```python
import numpy as np

x = np.matrix([[1, 2], [3, 4]])
y = np.matrix([[5, 6], [7, 8]])

matrix_sum = np.add(x, y)
print(matrix_sum)
print(matrix_sum.shape)

"""
[[ 6  8]
 [10 12]]
(2, 2)
"""
```

## Matrix Multiplication
> A of shape (m x n) and B of shape (n x z) multiplied gives C of shape (m x z)

Multiplying a Matrix is calculate the sum of the products between rows and columns. The matrix Multiplication, also called dot product.

[![mm](https://hadrienj.github.io/assets/images/2.2/dot-product.png "mm")](http://https://hadrienj.github.io/assets/images/2.2/dot-product.png "mm")

```python
import numpy as np

x = np.matrix([[1, 2, 3], [4, 5, 6]])
y = np.matrix([[5, 6], [7, 8],[9, 0]])

matrix_mul = np.matmul(x, y)
print(matrix_mul)
print(matrix_mul.shape)

"""
[[ 46  22]
 [109  64]]
(2, 2
"""
```

## Matrix Transpose
With transposition you can convert a row vector to a column vector and vice versa.

```python
import numpy as np

a = np.array([[1, 2], [3, 4]])
b = a.transpose()
print(b)

""""
[[1 3]
 [2 4]]
"""
```

