**In this post I will try to present some of them and to give some intuition what are possible applications for them. This article is focused more on the applications rather than on mathematical foundations. Moreover, it attempts to highlight that idea of Optics goes much, much further than manipulation of nested records.**

Functional programming languages, like Scala, we make it possible to ensure immutability, referential transparency and DRY.
 
In functional programming, **Immutability** is a must. Whenever it is needed to modify the content of a data structure, a new instance with updated values is created. Immutable objects and data structures are first-class citizens in Scala. This is because they prevent mistakes in distributed systems and provide thread-safe data.

In functional programming, **Referential Transparency** is a must. It means An expression is referentially transparent if it can be replaced with its value without changing the program’s behavior. Every small composable functions yielding the same output for the same input. It gives the ability to better understand and reason about the code, know exactly what function does just by looking at its signature.

In functional programming, we follow **DRY(don't repeat yourself)** principle. DRY is a principle of software development aimed at reducing repetition of software patterns, replacing it with abstractions or using data normalization to avoid redundancy. 

## Problem Statement
Let’s suppose we have a below nested data structure:
```scala
case class Street(name: String, code: String)
case class Address(country: String, city: String, street: Street)
case class Name(firstName:String,middelName:String,lastName:String)

case class BillInfo(addresses:Seq[Address],name: Name)

case class SiteInfo(url:String,alias:String,rating:Int)
case class GeneralInfo(email:String,password:String,siteInfo:SiteInfo)

case class User(id:String,generalInfo: GeneralInfo,billInfo: BillInfo)

```
let’s suppose that we have to change a deeply nested object. Scala offers a function called `copy` to modify the parameters value inside a `case class`. This function doesn’t mutate the referred value, instead it creates a new object :

 - **Increase the User Rating**

	```scala
	  def increaseUserSiteRating(user: User): User = {
	  
	    user.copy(
	      generalInfo = user.generalInfo.copy(
	        siteInfo = user.generalInfo.siteInfo.copy(
	          rating = user.generalInfo.siteInfo.rating + 1)))
	  }
	```

 - **Confirm All Billing Address**
	 ```scala
	  def confirmAddresses(user: User): User ={

	    val updatedAddresses = user.billInfo.addresses.map(_.copy(isConfirmed = true))
	    user.copy(billInfo = user.billInfo.copy(addresses = updatedAddresses))
	  }
	```

The greater the level of nesting of the objects, the less readable the syntax becomes. If we increase a level of nesting in our structures then we will considerably increase amount of a code. In such cases lens give a cleaner way to make changes in nested structures.

In this post I will use code and terminology taken from [Monocle](https://julien-truffaut.github.io/Monocle/) – Scala library for Optics.

## Introducing Lenses
A Lens is an abstraction from functional programming which helps to deal with a problem of updating complex immutable nested objects.

Lens in essence is a pair of functions:

-   `get(s: S): A`
-   `set(a: A): S => S`

	What are `S` and `A`? `S` represents the `Product` (or in other words “the whole part”, or container) and `A` some element inside of `S` (or in other words “the specific part”).

	In a nutshell – by having `get` Lens allows to “zoom in” into a specific part of `Product` and by having `set` lets you construct new “whole part” with updated “specific part”. After zooming in we lose some information and that’s why `set`needs `S` as an argument – to be able to reconstruct whole Product.

Let’s suppose we have the same below nested data structure:
```scala
case class Street(name: String, code: String)
case class Address(country: String, city: String, street: Street)

```

let’s suppose that we have to change a deeply nested object. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUzOTc5MjgwLDExMjk3OTA4MjYsMTUzOD
IzMzMyNCwtMjA3MDIzMzg2Niw0MDE3OTI5MTEsNzE2NTIwMDg4
LC0zNjY4MDQ1MDMsLTE3MDA0MjgzMDEsMTUxMjQ4NTMwOCwxMj
c2ODU2MjYsLTIwMjcxOTc5ODUsMTQwMTY4NjY2MiwtMTE0MDE5
MjQ5NywtNTIzMDIxNzgzLC0yNTQxNjI2NSwtMTI5ODI5NjQ5Ni
w0MjE5MzA1ODAsLTIxNDU3MDYxNjIsMzg5MDE0MSwtMTk5OTk1
Njg5MF19
-->