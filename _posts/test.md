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


**Add Functionality :**  A great thing about Scala traits is that you can mix multiple traits that have behaviour into classes and add real working methods to them. A very interesting thing you can do with traits that have concrete methods is mix them into classes on the fly.

[Check Source Code for Add Functionality ](https://github.com/gurditsingh/Scala-FP/blob/master/src/main/scala/scala/trait_lesson/AddFunctionality.scala)

**Modify Functionality (Stackable Modification﻿):** This is where traits play an important role. The stackable modifications state that “super” is accessed dynamically based on how the trait is mixed in, whereas in general super is statically determined.

Stackable modifications can be combined with each other in any way you desire. Given a set of stackable traits that each modify a class in some way, you can pick and choose any of those traits you would like to use when defining new classes.

Scala allows stackable modifications to any methods using classes and/or traits, which means you can choose very specific behavior by stacking classes and traits by mixing them together. When you stack new trait by overriding the same method over and over, you will get different or add-on behavior to your method.

[Check Source Code for Modify Functionality](https://github.com/gurditsingh/Scala-FP/blob/master/src/main/scala/scala/trait_lesson/ModifyFunctionality.scala)

**Intercept functionality :** Intercept functionality which is very similar to modifying the functionality. In Intercept we will you existing base and intercept the functinality. 


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ3OTM1MDc4NSwtNTY1MTEzNjM3LC0xNT
Y5OTA0MTQyLDE4MTQ4MzQ0MjcsMjAyNzA1NjY3MywtMTI1OTg5
MDA2MSwtMTQ1MzY4MDY5LDEzNDIyNzI1ODEsMTQ0NjQzMjY1NS
wxMjk2NTIwMDg2LC0yMDg4NzQ2NjEyLC0xODc2MDc0NjYwLC0x
NTU5NTg3NjA3LDczODA5MDYzMCwtMTE1MDQxMjExNiw5MDcxMj
c2NzMsLTIwODg3NDY2MTIsMjAzOTYzNTYyLC03MTA1Mjg3MCwt
MTc0NjI1ODMxM119
-->