---
layout: post
title:  "Play ws call test"
meta: "WsTestClient - How to test wsClient of play with spec2?"
date:   2017-02-20 11:11:37 +0530
categories: Play ws spec2

---

How to test wsClient of play with spec2? 
=======================================

Relatively better way to test ws clients.

Either use wireMock or Play's web service mock. 

With wireMock, we need to manage of server's lifecycle and some extra code as well.

Better way use Play's mock service with WsTestClient.

Example:

Problem: How to test ws.url().get method of play framework?

{% highlight scala %}

//Class to test

class HttpClient @Inject()(ws: WSClient, hostUrl: String){

  def get() :Future[String]= {

    ws.url(hostUrl + "/customer").get().map(
      resp => resp.body
    )
  }

}

//Solution with WsTestClient

"Http Client" should {

	"call get with correct url" in {
		implicit ee: ExecutionEnv =>
	  Server.withRouter() {
	    case GET(p"/customer") => Action {
	      Results.Ok("result")
	    }
	  } { implicit port =>
	    WsTestClient.withClient { client =>
	      new HttpClient(client, mockApplicationConfig).get() must be_==("result").await
	    }
	  }
	}
}

{% endhighlight %}

For more info, refer play framework documentation


