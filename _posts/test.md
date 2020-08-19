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

	**Lets create are own while loop name wheel:**  By using multiple parameter groups you can build are own control structures.  whilst must be defined to have two parameter groups. The first parameter group is i


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MzIyMzg3OTgsLTQ3MTY4Mjg5MSwyMD
M2Njg2NjEyLDQ2ODk5MDI5NiwxMjc0OTY1ODUyLDgxNzg2MTgx
Myw1MjEyNzQyOTMsLTMwNzI5MjQ3LDEyMTUxMzI1MzIsLTEzND
MxODYwNDcsMTg2NjM3MzAxMywtMTE5Mjc3NDc1NSw5NzYxNDc0
NzMsLTg5Mzc2ODg0LC0xMDc5NDM0MTM3LC01NjUxMTM2MzcsLT
E1Njk5MDQxNDIsMTgxNDgzNDQyNywyMDI3MDU2NjczLC0xMjU5
ODkwMDYxXX0=
-->