---
layout: post
title:  "Scala filter"
meta: "scala filter with example, predicate and function as parameter"
date:   2017-02-24 11:11:37 +0530
categories: scala filter

---

Scala filter use to extract elements from collection based on predicate. It iterates through each element of collection and check for predicate.  

Scala filter example:
==========================

Extract only even numbers, 

{% highlight scala %}

val list = List(1, 2, 3, 4)

list.filter(element => element%2 == 0)

result :  List(2, 4)
{% endhighlight %}

User wants only list of prime customers from all customers:
===========================================================

Problem: How to extract only prime customers?  Given: list of customer.
{% highlight scala %}

case class Customer(id: String, name: String, email: String, 
			city:String, customerType:String)

val customers = List(Customer("1", "John", "john@mail.com", "London", "Prime"), 
Customer("2", "Andy", "andy@mail.com", "Paris", "General"))

customers.filter(customer => customer.customerType == "Prime")

result: List(Customer("1", "John", "john@mail.com", "London", "Prime"))

{% endhighlight %}



Short-hand for Scala filter:
============================

Use _ as shorthand for each customer.

Example,

{% highlight scala %}

case class Customer(id: String, name: String, email: String, 
			city:String, customerType:String)

val customers = List(Customer("1", "John", "john@mail.com", "London", "Prime"), 
Customer("2", "Andy", "andy@mail.com", "Paris", "General"))

customers.filter(_.customerType == "Prime")

result: List(Customer("1", "John", "john@mail.com", "London", "Prime"))

{% endhighlight %}


We can pass Boolean function as parameter:
=========================================


We can further extract predicate in seperate function.

Example:

{% highlight scala %}

case class Customer(id: String, name: String, email: String, 
			city:String, customerType:String)

def isPrime(customer:Customer) : Boolean = customer.customerType == "Prime" // predicate, Boolean function	

val customers = List(Customer("1", "John", "john@mail.com", "London", "Prime"), 
Customer("2", "Andy", "andy@mail.com", "Paris", "General"))

customers.filter(isPrime(_))

result: List(Customer("1", "John", "john@mail.com", "London", "Prime"))

{% endhighlight %}










