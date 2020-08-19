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

	**Lets create are own while loop name wheely:**  By using multiple parameter groups you can build are own control structures. wheely must be defined to have two parameter groups.
	

	 - **The first parameter group** is the expression between the two parentheses. Note that this expression should return a Boolean value.
	 - **The second parameter group** is the block of code enclosed in curly braces after first parameter.

		**Scala while loop example:**
		```scala
		var i = 0
	    while (i < 3){
	      println("i : "+ i)
	      i += 1
	    }
		```
		

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAyNTcxMDI3Myw2NzkzMzIzNjUsLTQwMz
k3NzQ2MSwtMTczMjIzODc5OCwyMDM2Njg2NjEyLDQ2ODk5MDI5
NiwxMjc0OTY1ODUyLDgxNzg2MTgxMyw1MjEyNzQyOTMsLTMwNz
I5MjQ3LDEyMTUxMzI1MzIsLTEzNDMxODYwNDcsMTg2NjM3MzAx
MywtMTE5Mjc3NDc1NSw5NzYxNDc0NzMsLTg5Mzc2ODg0LC0xMD
c5NDM0MTM3LC01NjUxMTM2MzcsLTE1Njk5MDQxNDIsMTgxNDgz
NDQyN119
-->