---
layout: post
title:  "Scala xml parsing"
meta: "Scala xml parsing, extracting elements and atrributes"
date:   2017-03-04 11:11:37 +0530
categories: scala xml

---

Scala xml parsing, extracting elements and atrributes.

How to create customer object from customer xml response?
=====================================

{% highlight scala %}

case class Customer(name: String, city:String, customerType:String)

val customerXml: scala.xml.Elem = <customers>
		<customer type="prime">
			<name>Ashok</name><city>Pune</city>
		</customer>
		<customer type = "regular">
			<name>Mahesh</name>
			<city>Mumbai</city>
		</customer>
		<customer type = "prime">
			<name>Prashant</name>
			<city>Mumbai</city>
		</customer>
	</customers>

val customers :scala.xml.NodeSeq = customersXml \ "customer" 
// \"yourElement" to extract elements

customers.map(customer => Customer((customer \ "name").text, 
(customer \ "city").text, (customer \ "@type").text))   
// "@yourAttribute" to extract attributes

result:List[Customer] = List(Customer(Ashok,Pune,prime), Customer(Mahesh,Mumbai,regular), 
Customer(Prashant,Mumbai,prime))

{% endhighlight %}

