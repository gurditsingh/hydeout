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

I also showed that isEven works great when you pass it into the List class filter method:
```scala
scala> val list = List(1,2,3,4,5,6)
list: List[Int] = List(1, 2, 3, 4, 5, 6)

scala> list.filter(isEven)
res0: List[Int] = List(2, 4, 6)
```
**The key points :**

 - The filter method accepts a function as an input parameter.
 - The functions you pass into filter must match the type signature (takes an Int returns a Boolean).

## Defining HOF
To define a function that takes another function as an input parameter, all you have to do is define the signature of the function you want to accept. The function greet takes function as input parameter callback have no input parameters and must return nothing.

```scala
def greet(callme: () => Unit) {
callme()
}
```

**Let see how this function works**
callme is the input parameter. In this case callme is a function to accept.
The callme signature specifies the type of function to accept.
The () portion of callme signature takes no input parameters.
The Unit portion of the signature callme function should return nothing.
When greet is called, its function body is executed, and the callme() line inside the body invokes the function that is passed in.


 

<!--stackedit_data:
eyJoaXN0b3J5IjpbNTIxMjc0MjkzLC0zMDcyOTI0NywxMjE1MT
MyNTMyLC0xMzQzMTg2MDQ3LDE4NjYzNzMwMTMsLTExOTI3NzQ3
NTUsOTc2MTQ3NDczLC04OTM3Njg4NCwtMTA3OTQzNDEzNywtNT
Y1MTEzNjM3LC0xNTY5OTA0MTQyLDE4MTQ4MzQ0MjcsMjAyNzA1
NjY3MywtMTI1OTg5MDA2MSwtMTQ1MzY4MDY5LDEzNDIyNzI1OD
EsMTQ0NjQzMjY1NSwxMjk2NTIwMDg2LC0yMDg4NzQ2NjEyLC0x
ODc2MDc0NjYwXX0=
-->