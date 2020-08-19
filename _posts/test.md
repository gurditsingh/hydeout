## Functions with Multiple Parameter Groups called Currying
Currying splits method with multiple parameters into a chain of functions each with one parameter.

## Let's create simple example:

Create simple function that have multiple input parameter groups.  The function’s input parameters in different groups surrounded by parentheses:
```scala
scala> def sum(a: Int)(b: Int) = a + b
sum: (a: Int)(b: Int)Int

scala> sum(1)(2)
res1: Int = 3
```
That’s all this is a basic technique.

**If you trying to call it with two parameters in one group won’t work:**
```scala
scala> sum(1,2)
<console>:13: error: too many arguments for method sum: (a: Int)(b: Int)Int
       sum(1,2)
```
You must apply the input parameters in the separate input groups.

## Declare multiple parameter groups gives you these additional benefits:

 - **write your own control structures:**

**Lets create are own while loop:**  By using multiple parameter groups you can build are own control structures.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MjcxNDYwMzAsMjAzNjY4NjYxMiw0Nj
g5OTAyOTYsMTI3NDk2NTg1Miw4MTc4NjE4MTMsNTIxMjc0Mjkz
LC0zMDcyOTI0NywxMjE1MTMyNTMyLC0xMzQzMTg2MDQ3LDE4Nj
YzNzMwMTMsLTExOTI3NzQ3NTUsOTc2MTQ3NDczLC04OTM3Njg4
NCwtMTA3OTQzNDEzNywtNTY1MTEzNjM3LC0xNTY5OTA0MTQyLD
E4MTQ4MzQ0MjcsMjAyNzA1NjY3MywtMTI1OTg5MDA2MSwtMTQ1
MzY4MDY5XX0=
-->