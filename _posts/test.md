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

First 1 : Increase the User Rating
```scala
  def updateUserSiteRating(user: User): User = {
  
    user.copy(
      generalInfo = user.generalInfo.copy(
        siteInfo = user.generalInfo.siteInfo.copy(
          rating = user.generalInfo.siteInfo.rating + 1)))
  }
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyNTQ4MTAxNiw0MDE3OTI5MTEsNzE2NT
IwMDg4LC0zNjY4MDQ1MDMsLTE3MDA0MjgzMDEsMTUxMjQ4NTMw
OCwxMjc2ODU2MjYsLTIwMjcxOTc5ODUsMTQwMTY4NjY2MiwtMT
E0MDE5MjQ5NywtNTIzMDIxNzgzLC0yNTQxNjI2NSwtMTI5ODI5
NjQ5Niw0MjE5MzA1ODAsLTIxNDU3MDYxNjIsMzg5MDE0MSwtMT
k5OTk1Njg5MCwyMDg0ODM1NDg3LC0xNDE0ODA4Njg2LC03MzY0
OTAyMzNdfQ==
-->