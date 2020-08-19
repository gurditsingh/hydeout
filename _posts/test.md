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
	

	 - **first parameter group** is the expression between the two parentheses. Note that this expression should return a Boolean value.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYxMTQ1MjAyOSwtNDAzOTc3NDYxLC0xNz
MyMjM4Nzk4LDIwMzY2ODY2MTIsNDY4OTkwMjk2LDEyNzQ5NjU4
NTIsODE3ODYxODEzLDUyMTI3NDI5MywtMzA3MjkyNDcsMTIxNT
EzMjUzMiwtMTM0MzE4NjA0NywxODY2MzczMDEzLC0xMTkyNzc0
NzU1LDk3NjE0NzQ3MywtODkzNzY4ODQsLTEwNzk0MzQxMzcsLT
U2NTExMzYzNywtMTU2OTkwNDE0MiwxODE0ODM0NDI3LDIwMjcw
NTY2NzNdfQ==
-->