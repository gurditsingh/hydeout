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

 - **Benefit: write your own control structures.**

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
		
		 - **by-value** parameter is like receiving a val field; its evaluated once, when the parameter is define to the function.
		 - **by-name** parameter is like receiving a def method; its is evaluated whenever it is used in the function.
		 
		In wheely both parameter groups use by-name parameters because we need to evaluate both the parameters when they required. If wheely function not receive by-name parameters its evaluate the expr (true) for the first time and the loop will run forever same is the case with second parameter(code) as well.
		
		**Lets write complex control structure where the database/file connection is automatically close after call:**
		[source code](https://github.com/gurditsingh/Scala-FP/blob/master/src/main/scala/scala/Curring_lesson/AutoCloseCurring.scala)
		

------------

 - **Benefit: Using implicit values**
	 A benefit of multiple input parameter groups comes when you use them with implicit parameters. This can help to simplify code to pass implicit parameters when needed.
	 
	 **Lets create simple example:**
	```scala
		scala> def showIfTrue(x: Int)(implicit y: Boolean) = if (y) println(x)
		showIfTrue: (x: Int)(implicit y: Boolean)Unit

		scala> implicit val b:Boolean = true
		b: Boolean = true

		scala> showIfTrue(10)
		10
	```
	**How this works:**

	 - **showIfTrue()** function have two parameter groups and the second parameter group declares an implicit.
	 - **showIfTrue(10)** is called with one parameter group.
	 - Scala knows that one of the implicit Boolean value present in the current scope (like we defined **implicit val b:Boolean = true**) otherwise throw error.

------------

 - **Benefit: Using default values**
	you can use default values for input parameters when using multiple parameter groups.
	```scala
	scala> def fun(x: Int = 1)(y: Int = x) = { x + y }
	fun: (x: Int)(y: Int)Int

	scala> fun()()
	res0: Int = 2
	```
	

> In fun function parameter in the second parameter group can use a
> parameter from the first parameter group as a default value.

	 
   

	


		

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ4ODM0NTgyMCwtNDkzMzIzNjI1LC0xMj
c4NDY2NzcsLTk5OTAzMDMyMiwtMTcwNjczMTk5Miw5MDc4OTc3
MjIsLTEzNDM1ODAwNzYsLTE4NzI3NTk2NTksNjc5MzMyMzY1LC
00MDM5Nzc0NjEsLTE3MzIyMzg3OTgsLTQ3MTY4Mjg5MSwyMDM2
Njg2NjEyLDQ2ODk5MDI5NiwxMjc0OTY1ODUyLDgxNzg2MTgxMy
w1MjEyNzQyOTMsLTMwNzI5MjQ3LDEyMTUxMzI1MzIsLTEzNDMx
ODYwNDddfQ==
-->