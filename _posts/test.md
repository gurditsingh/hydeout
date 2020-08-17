## Traits
Traits are a fundamental unit of code reuse in Scala. Trait encapsulates method and field definitions, which can be reused by mixing into classes.


> what the **trait** word means. The traits means characteristic, so if
> you have a trait with a few attributes that you can mix into your
> object and this object will does have access to those attributes.

## Kind of Traits:

 1. Thin Trait
 2. Rich Trait
 
 **Thin Trait :** The thin trait is very similar to Java interfaces like the most of the methods abstract not all.
 **Rich Trait:** Rich Trait are sort of the opposite most methods in a Rich Trait are implemented usually in terms of the abstract methods.

## Divide Trait into three separate categories

 - Add Functionality
 - Modify Functionality
 - Intercept functionality


**Add Functionality : ** A great thing about Scala traits is that you can mix multiple traits that have behaviour into classes and add real working methods to them. A very interesting thing you can do with traits that have concrete methods is mix them into classes on the fly.

[Check Source Code for Add Functionality ](https://github.com/gurditsingh/Scala-FP/blob/master/src/main/scala/scala/trait_lesson/AddFunctionality.scala)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM1MjU2NTExMiwyMDI3MDU2NjczLC0xMj
U5ODkwMDYxLC0xNDUzNjgwNjksMTM0MjI3MjU4MSwxNDQ2NDMy
NjU1LDEyOTY1MjAwODYsLTIwODg3NDY2MTIsLTE4NzYwNzQ2Nj
AsLTE1NTk1ODc2MDcsNzM4MDkwNjMwLC0xMTUwNDEyMTE2LDkw
NzEyNzY3MywtMjA4ODc0NjYxMiwyMDM5NjM1NjIsMTM2NjYxNz
MyLDcxNTU4OTkxOSwtMjA5MzkwNDM2NCwxNTI4NzQxNDc4LC01
NjUwMTQ5OTldfQ==
-->