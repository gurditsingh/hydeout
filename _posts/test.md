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
		**Lets describe how wheely works:**
		• wheely has two parameter groups.
		• The first parameter group evaluate to a Boolean value.
		• The second parameter group return nothing (Unit), because the last expression in the code block (i += 1) returns nothing.
		
		**Lets create code for wheely**
		```scala
		def wheely(expr: => Boolean)(block: => Unit): Unit = {
	      while (expr) {
	        block
	      }
	    }

	    var i = 0
	    wheely( i < 3){
	      println("i : "+ i)
	      i+=1
	    }
		```

		**Notice :** both parameter groups use by-name parameters.
		
		**Parameters Kind:**
			**by-value** parameter is like receiving a val field; its evaluated once, when the parameter is define to the function.
			by-name parameter is like receiving a def method; its body is evaluated whenever it is used inside the function.
		
		

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3Njk4NTI2OTIsLTE4NzI3NTk2NTksNj
c5MzMyMzY1LC00MDM5Nzc0NjEsLTE3MzIyMzg3OTgsMjAzNjY4
NjYxMiw0Njg5OTAyOTYsMTI3NDk2NTg1Miw4MTc4NjE4MTMsNT
IxMjc0MjkzLC0zMDcyOTI0NywxMjE1MTMyNTMyLC0xMzQzMTg2
MDQ3LDE4NjYzNzMwMTMsLTExOTI3NzQ3NTUsOTc2MTQ3NDczLC
04OTM3Njg4NCwtMTA3OTQzNDEzNywtNTY1MTEzNjM3LC0xNTY5
OTA0MTQyXX0=
-->