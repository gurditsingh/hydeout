## Functions with Multiple Parameter Groups called Currying
Currying splits method with multiple parameters into a chain of functions each with one parameter.

lets create simple function that have multiple input parameter groups.  The function’s input parameters in different groups surrounded by parentheses:
```scala
scala> def sum(a: Int)(b: Int) = a + b
sum: (a: Int)(b: Int)Int

scala> sum(1)(2)
res1: Int = 3

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM0NTk3NzAyOSw0Njg5OTAyOTYsMTI3ND
k2NTg1Miw4MTc4NjE4MTMsNTIxMjc0MjkzLC0zMDcyOTI0Nywx
MjE1MTMyNTMyLC0xMzQzMTg2MDQ3LDE4NjYzNzMwMTMsLTExOT
I3NzQ3NTUsOTc2MTQ3NDczLC04OTM3Njg4NCwtMTA3OTQzNDEz
NywtNTY1MTEzNjM3LC0xNTY5OTA0MTQyLDE4MTQ4MzQ0MjcsMj
AyNzA1NjY3MywtMTI1OTg5MDA2MSwtMTQ1MzY4MDY5LDEzNDIy
NzI1ODFdfQ==
-->