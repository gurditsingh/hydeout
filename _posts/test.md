## Functions with Multiple Parameter Groups called Currying
Currying splits method with multiple parameters into a chain of functions each with one parameter.

lets create simple function that have multiple input parameter groups.
```scala
scala> def sum(a: Int)(b: Int) = a + b
sum: (a: Int)(b: Int)Int

scala> sum(1)(2)
res1: Int = 3

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjI4NjcwNDg2LDQ2ODk5MDI5NiwxMjc0OT
Y1ODUyLDgxNzg2MTgxMyw1MjEyNzQyOTMsLTMwNzI5MjQ3LDEy
MTUxMzI1MzIsLTEzNDMxODYwNDcsMTg2NjM3MzAxMywtMTE5Mj
c3NDc1NSw5NzYxNDc0NzMsLTg5Mzc2ODg0LC0xMDc5NDM0MTM3
LC01NjUxMTM2MzcsLTE1Njk5MDQxNDIsMTgxNDgzNDQyNywyMD
I3MDU2NjczLC0xMjU5ODkwMDYxLC0xNDUzNjgwNjksMTM0MjI3
MjU4MV19
-->