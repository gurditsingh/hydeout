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
if trying to call it with three parameters in one group won’t work:
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzOTU0ODIwMTMsNDY4OTkwMjk2LDEyNz
Q5NjU4NTIsODE3ODYxODEzLDUyMTI3NDI5MywtMzA3MjkyNDcs
MTIxNTEzMjUzMiwtMTM0MzE4NjA0NywxODY2MzczMDEzLC0xMT
kyNzc0NzU1LDk3NjE0NzQ3MywtODkzNzY4ODQsLTEwNzk0MzQx
MzcsLTU2NTExMzYzNywtMTU2OTkwNDE0MiwxODE0ODM0NDI3LD
IwMjcwNTY2NzMsLTEyNTk4OTAwNjEsLTE0NTM2ODA2OSwxMzQy
MjcyNTgxXX0=
-->