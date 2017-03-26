---
layout: post
title:  "Scala fold operations"
meta: "Scala fold uses accumulator to perform operations, Difference between fold, foldLeft and foldRight"
date:   2017-03-09 11:11:37 +0530
categories: scala fold

---

Scala fold uses accumulator to perform operations.

Company needs cost of all employees?
=====================================
How to calculate cost of all employees? given list of employee with ctc.

{% highlight scala %}

case class Employee(id: Int, ctc:Int)

val employees = List(Employee(332, 18), Employee(124, 21), Employee(112, 12))

val costOfAllEmployee = employees.foldLeft(0){(accumulator, employee) => 
	accumulator + employee.ctc
}

// 0 is initial value of accumulator.

costOfAllEmployee: Int = 51

{% endhighlight %}


Difference between fold, foldLeft and foldRight
==============================================

foldLeft - traverse from left to right.

foldRight - traverse from right to left.

fold - no direction. 

Short-hand for Scala leftFold
=========================

{% highlight scala %}

val costOfAllEmployee = employees.foldLeft(0)(_ + _.ctc)

{% endhighlight %}




