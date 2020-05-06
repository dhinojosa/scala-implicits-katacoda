We don't have to accept the `implicit` value, we can place something manually,
if we want to override the implicit value, notice in the following example, we 
are adding our own second value of `110`.

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;

object MyApp extends App {

  implicit val rate: Int = 100

  def calcPayment(hours:Int)(implicit rate:Int) = hours * rate

  println(calcPayment(50)(110))
}
</pre>

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}
