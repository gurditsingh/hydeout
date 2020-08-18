Higher order functions take other functions as parameters or return a function as a result. This is possible because functions are first-class values in Scala.

> The primary goal of this blog is to show how to write functions that
> take other functions as input parameters.

## Functions as a Data Type

The functions in Scala are treated equally to typical data types like integers or strings. Moreover, a function can be assigned to a variable or value, and then passed around like a typical parameter. 
```scala
    // Bring a value to the power of two using lambdas function
    val powOfTwoFun1 = (x:Int) => x * x
    // Bring a value to the power of two using Scala Function1
    val powOfTwoFun2 = new Function[Int,Int] {
      override def apply(x: Int): Int = x * x
    }

    assert(powOfTwoFun1(2) == powOfTwoFun2(2))
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQyMzA4MDYxOCwtMTE5Mjc3NDc1NSw5Nz
YxNDc0NzMsLTg5Mzc2ODg0LC0xMDc5NDM0MTM3LC01NjUxMTM2
MzcsLTE1Njk5MDQxNDIsMTgxNDgzNDQyNywyMDI3MDU2NjczLC
0xMjU5ODkwMDYxLC0xNDUzNjgwNjksMTM0MjI3MjU4MSwxNDQ2
NDMyNjU1LDEyOTY1MjAwODYsLTIwODg3NDY2MTIsLTE4NzYwNz
Q2NjAsLTE1NTk1ODc2MDcsNzM4MDkwNjMwLC0xMTUwNDEyMTE2
LDkwNzEyNzY3M119
-->