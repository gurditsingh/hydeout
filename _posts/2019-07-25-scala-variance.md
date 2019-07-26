---
title: "What is variance in Scala?"
layout: post
excerpt: "In the generic types, the variance is the correlation between the inheritance relation of the abstract types and how it is “transmitted” to the inheritance in the generic classes. Scala supports variance annotations of type parameters of generic classes, to allow them to be covariant, contravariant, or invariant."
last_modified_at: 2019-07-25T10:27:01-05:00
tags:
  - variance
  - Scala
  - Generic
  - TypeSystem
  - Invariance
  - Covariance
  - Contravariance
---
# Let's start with Liskov substitution principle
Let Φ(x) be a property provable about objects x of type T. Then Φ(y) should be true for objects y of type S where S is a subtype of T.

# What is Variance?
In the generic types, the variance is the correlation between the inheritance relation of the abstract types and how it is “transmitted” to the inheritance in the generic classes. Scala supports variance annotations of type parameters of generic classes, to allow them to be covariant, contravariant, or invariant.

# Variance in functioning:

# Invariance [T]: 
A generic class invariant over its abstract type can only receive a parameter type of exactly that type.
```scala
trait Bank

trait Online extends Bank
trait Offline extends Bank

class Payment[T]

object Invariance{

  def doPayment(method:Payment[Online]){
    print(method)
  }

  doPayment(new Payment[Online]) // pass the same type
}
```
------------
# Covariance [+T]:
 A generic class covariant over its abstract type can receive a parameter type of that type or subtypes of that type.
 ```scala
trait Bank

trait Online extends Bank
trait Offline extends Bank

class NetBanking extends Online
class Wallet extends Online

class Cash extends Offline
class Cheque extends Offline

class Payment[+T]

object Covariance {

  def doPayment(method:Payment[Online]){
    print(method)
  }

  doPayment(new Payment[NetBanking]) // pass subtype to supertype
}
```
------------
# Contravariance [-T]: 
A generic class contravariant over its abstract type can receive a parameter type of that type or supertypes of that type.
```scala
trait Passenger

class Business extends Passenger

class Corprate extends Business

class AirLine[-T]

object Contravariance {

  def doPayment(method:AirLine[Corprate]){
    print(method)
  }

  doPayment(new AirLine[Business])// pass supertype to subtype
}
```

------------
