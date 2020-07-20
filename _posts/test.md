## In programming we can distinguish two main paradigms.

 1. Imperative programming
 - Keeps track of state and manages change of state
 - Defines exactly how to step through the code. Order of execution matters

 2. Functional programming
-   Avoids keeping track of and changing state and mutable data.
-   Divides the problem into functions


## What is Imperative Programming ?

With an imperative approach, a developer writes code that describes in exacting detail the steps that the computer must take to accomplish the goal.

**For example:** if you wanted to multiply all elements in a list by some factor, in Java the solution would be a `for` loop that increments a counter variable until it is less than the list length - so you are telling the computer how to transform a list explicitly.

•	Modifying Mutable Variables
•	Using Assignments 
•	Control Structure Loops, continue, break etc

## What is Functional Programming ?
Functional programming language is one which does not have an immutable variables assignments or imperative control structure and in the wider sense the functional programming language is one with that enables the construction of elegant programs that focus on the functions.

In particular functions in a functional programming language or first class citizens. 
It means that essentially you can do with a function that you could do with any other piece of data. You can define a string anywhere you should be able to define a function anywhere including inside other functions. Like any other value, you should be able to pass a function as a parameter to another function and return it as a result from a function.

## FP Rules:
1. There will be no null values.
2. Only pure functions will be used and we will’ define pure functions more
thoroughly soon, but simply stated, (a) a pure function must always return the
same output given the same input, and (b) calling the function must not have
any side effects, including reading input, writing output, or modifying any sort
of hidden state.
3. This book will only use immutable values (val) for all fields. There are no var
fields in pure FP code, so I won’t use any variables (var) in this book, unless
I’m trying to explain a point.
4. Whenever you use an if, you must always also use an else. Functional programming uses only expressions, not statements.
5. We won’t create “classes” that encapsulate data and behavior. Instead we’ll
create data structures and write pure functions that operate on those data structures.

<!--stackedit_data:
eyJoaXN0b3J5IjpbNjE0MjExNDA2LDczODA5MDYzMCwtMTE1MD
QxMjExNiw5MDcxMjc2NzMsLTIwODg3NDY2MTIsMjAzOTYzNTYy
LDEzNjY2MTczMiw3MTU1ODk5MTksLTIwOTM5MDQzNjQsMTUyOD
c0MTQ3OCwtNTY1MDE0OTk5LC00NTk5NDY3MzgsMTMxNjM1NDE1
NiwyMDkyNjYxNTU5LC03MTA1Mjg3MCwtNzEwNTI4NzAsLTE3ND
YyNTgzMTMsLTEwMzQzNTY1MTcsMTQyODk5NzcyOCwtNjU0MjEx
NjEwXX0=
-->