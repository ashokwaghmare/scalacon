---
layout: post
title:  "Scala js setup"
meta: "Scala js set up with activator"
date:   2017-03-21 11:11:37 +0530
categories: scala fold

---

Scala js set up with activator.
===============================

Steps:

Download and install [lightbend activator](https://www.lightbend.com/activator/download)

Set up the path for activator. once done with activator installation.

Create a minimal-scala project using {% highlight scala %} activator new {% endhighlight %} command.

Now add {% highlight scala %} addSbtPlugin("org.scala-js" % "sbt-scalajs" % "0.6.14") {% endhighlight %} in project/plugins.sbt

add {% highlight scala %} enablePlugins(ScalaJSPlugin) {% endhighlight %} in build.sbt

add following file in src/main directory

{% highlight scala %}

import scala.scalajs.js.JSApp

object Hello extends JSApp{
  def main(): Unit = {
    println("Hello in scala JS") // equivalent to console.log("Hello in scala JS")
  }
}

{% endhighlight %}


Now say {% highlight scala %} activator run {% endhighlight %}

You can see output on console:  "Hello in scala JS"

Now you can see generated javascript file in target directory. for me path is : target/scala-2.11/js-demo-fastopt.js







