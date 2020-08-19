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
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU5NzYyNDg3NywyMDM2Njg2NjEyLDQ2OD
k5MDI5NiwxMjc0OTY1ODUyLDgxNzg2MTgxMyw1MjEyNzQyOTMs
LTMwNzI5MjQ3LDEyMTUxMzI1MzIsLTEzNDMxODYwNDcsMTg2Nj
M3MzAxMywtMTE5Mjc3NDc1NSw5NzYxNDc0NzMsLTg5Mzc2ODg0
LC0xMDc5NDM0MTM3LC01NjUxMTM2MzcsLTE1Njk5MDQxNDIsMT
gxNDgzNDQyNywyMDI3MDU2NjczLC0xMjU5ODkwMDYxLC0xNDUz
NjgwNjldfQ==
-->