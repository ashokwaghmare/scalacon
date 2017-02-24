---
layout: post
title:  "Integration test with play framework"
meta: "Integration tests using GuiceApplicationBuilder play framework 2.5 with spec2, WsTestClient to hit actual enpoint, WithServer is used to specify running port"
date:   2017-02-24 11:11:37 +0530
categories: Play ws spec2

---

How to write integration specs using GuiceApplicationBuilder in play framework? 
===============================================================================

Since FakeApplication is depricated from Play 2.5.0, it's recommended to use GuiceApplicationBuilder to create an application instance.
WsTestClient is used to hit actual endpoint and WithServer is used to specify running port.


Example:

{% highlight scala %}
class CustomerControllerIntegrationSpec extends Specification{

    val expectedJson = """{"customers":[{"names":["Akshara", "Akash"]}]}"""

    "Customer end point" should {
      val application = GuiceApplicationBuilder().build()
      "return customer json" in new WithServer(app = application, port = 3333) {
        WsTestClient.withClient{client =>
          val response = await(
          	client.url("http://localhost:3333/customers").get() //end point from route file
          	)  
          response.body must equalTo(expectedJson) 
          response.status must equalTo(OK)

        }
      }
    }

  }

{% endhighlight %}

default host is http://localhost, port as specified 3333, you can specify any other port as well.



