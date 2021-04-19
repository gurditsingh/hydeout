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
But let’s suppose that we have to change a deeply nested object. Scala offers a function called `copy` to modify the parameters value inside a `case class`. This function doesn’t mutate the referred value, instead it creates a new object :

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

The greater the level of nesting of the objects, the less readable the syntax becomes.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjI3OTM3NDcxLDE1MzgyMzMzMjQsLTIwNz
AyMzM4NjYsNDAxNzkyOTExLDcxNjUyMDA4OCwtMzY2ODA0NTAz
LC0xNzAwNDI4MzAxLDE1MTI0ODUzMDgsMTI3Njg1NjI2LC0yMD
I3MTk3OTg1LDE0MDE2ODY2NjIsLTExNDAxOTI0OTcsLTUyMzAy
MTc4MywtMjU0MTYyNjUsLTEyOTgyOTY0OTYsNDIxOTMwNTgwLC
0yMTQ1NzA2MTYyLDM4OTAxNDEsLTE5OTk5NTY4OTAsMjA4NDgz
NTQ4N119
-->