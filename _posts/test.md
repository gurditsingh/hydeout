Functional programming languages, like Scala, we make it possible to ensure immutability, referential transparency and DRY.
 
In functional programming, **Immutability** is a must. Whenever it is needed to modify the content of a data structure, a new instance with updated values is created. Immutable objects and data structures are first-class citizens in Scala. This is because they prevent mistakes in distributed systems and provide thread-safe data.

In functional programming, **Referential Transparency** is a must. It means An expression is referentially transparent if it can be replaced with its value without changing the program’s behavior. Every small composable functions yielding the same output for the same input. It gives the ability to better understand and reason about the code, know exactly what function does just by looking at its signature.

In functional programming, we follow **DRY(don't repeat yourself)** principle. DRY is a principle of software development aimed at reducing repetition of software patterns, replacing it with abstractions or using data normalization to avoid redundancy. 

Problem Statement: 

In this post I will try to present some of them and to give some intuition what are possible applications for them. This article is focused more on the applications rather than on mathematical foundations. Moreover, it attempts to highlight that idea of Optics goes much, much further than manipulation of nested records.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE0MDIyODQzLC0zNjY4MDQ1MDMsLTE3MD
A0MjgzMDEsMTUxMjQ4NTMwOCwxMjc2ODU2MjYsLTIwMjcxOTc5
ODUsMTQwMTY4NjY2MiwtMTE0MDE5MjQ5NywtNTIzMDIxNzgzLC
0yNTQxNjI2NSwtMTI5ODI5NjQ5Niw0MjE5MzA1ODAsLTIxNDU3
MDYxNjIsMzg5MDE0MSwtMTk5OTk1Njg5MCwyMDg0ODM1NDg3LC
0xNDE0ODA4Njg2LC03MzY0OTAyMzMsLTE3ODY2MzcyMjksMzI5
NTg4MzU2XX0=
-->