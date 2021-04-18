In this post I will try to present some of them and to give some intuition what are possible applications for them. This article is focused more on the applications rather than on mathematical foundations. Moreover, it attempts to highlight that idea of Optics goes much, much further than manipulation of nested records.

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



In this post I will try to present some of them and to give some intuition what are possible applications for them. This article is focused more on the applications rather than on mathematical foundations. Moreover, it attempts to highlight that idea of Optics goes much, much further than manipulation of nested records.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY3NDI2OTgwLDQwMTc5MjkxMSw3MTY1Mj
AwODgsLTM2NjgwNDUwMywtMTcwMDQyODMwMSwxNTEyNDg1MzA4
LDEyNzY4NTYyNiwtMjAyNzE5Nzk4NSwxNDAxNjg2NjYyLC0xMT
QwMTkyNDk3LC01MjMwMjE3ODMsLTI1NDE2MjY1LC0xMjk4Mjk2
NDk2LDQyMTkzMDU4MCwtMjE0NTcwNjE2MiwzODkwMTQxLC0xOT
k5OTU2ODkwLDIwODQ4MzU0ODcsLTE0MTQ4MDg2ODYsLTczNjQ5
MDIzM119
-->