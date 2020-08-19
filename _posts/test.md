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
		**Notice : ** 
		
		

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjU3Njc0MTgwLC0xODcyNzU5NjU5LDY3OT
MzMjM2NSwtNDAzOTc3NDYxLC0xNzMyMjM4Nzk4LDIwMzY2ODY2
MTIsNDY4OTkwMjk2LDEyNzQ5NjU4NTIsODE3ODYxODEzLDUyMT
I3NDI5MywtMzA3MjkyNDcsMTIxNTEzMjUzMiwtMTM0MzE4NjA0
NywxODY2MzczMDEzLC0xMTkyNzc0NzU1LDk3NjE0NzQ3MywtOD
kzNzY4ODQsLTEwNzk0MzQxMzcsLTU2NTExMzYzNywtMTU2OTkw
NDE0Ml19
-->