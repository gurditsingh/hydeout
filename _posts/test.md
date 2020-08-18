Higher order functions take other functions as parameters or return a function as a result. This is possible because functions are first-class values in Scala.

> The primary goal of this blog is to show how to write functions that
> take other functions as input parameters.

## Functions as a Data Type

The functions in Scala are treated equally to typical data types like integers or strings. Moreover, a function can be assigned to a variable or value, and then passed around like a typical parameter.

Let’s assume that we want a functions that calculates the power of an arbitrary number.
```scala
    // Bring a value to the power of two using lambdas function
    val powOfTwoFun1 = (x:Int) => x * x
    // Bring a value to the power of two using Scala Function1
    val powOfTwoFun2 = new Function[Int,Int] {
      override def apply(x: Int): Int = x * x
    }

    assert(powOfTwoFun1(2) == powOfTwoFun2(2))
```

The two approaches shown above construct the same type of a function. Our desired function should take one parameter of int and return a result of an int.

The first implementation uses widely known as lambda or single abstract method. The second implementation uses the trait  **Function1**, on which an  **apply**  method is overridden. Scala provides more variants of this Function trait, like  **Function2**, or  **Function3**, taking 2 or 3 parameters respectively.

Now, with those functions you can primarily do two things: call them or give as a parameter to another function.

## Using Higher Order Functions (HOF)

```scala
def isEven(i: Int) = i % 2 == 0
def sum(a: Int, b: Int) = a + b
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNDMxODYwNDcsMTg2NjM3MzAxMywtMT
E5Mjc3NDc1NSw5NzYxNDc0NzMsLTg5Mzc2ODg0LC0xMDc5NDM0
MTM3LC01NjUxMTM2MzcsLTE1Njk5MDQxNDIsMTgxNDgzNDQyNy
wyMDI3MDU2NjczLC0xMjU5ODkwMDYxLC0xNDUzNjgwNjksMTM0
MjI3MjU4MSwxNDQ2NDMyNjU1LDEyOTY1MjAwODYsLTIwODg3ND
Y2MTIsLTE4NzYwNzQ2NjAsLTE1NTk1ODc2MDcsNzM4MDkwNjMw
LC0xMTUwNDEyMTE2XX0=
-->