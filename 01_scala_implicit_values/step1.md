`implicit`s are like a `Map[Class[A], A]` where `A` is an object, and tied into a scope, and it is there when you need it; hence it is implicit. `implicit`s provide a lot of great techniques that we can use in Scala.

`implicit`s applied per scope is on display in the following example, we begin with an `implicit` value and call it from inside a method which uses a multiple parameter list where one group would accept the value as a parameter, and the other would receive the implicit value.

Enter the following into your editor

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;

object MyApp extends App {

   implicit val rate: Int = 100

   def calcPayment(hours:Int)(implicit n:Int) = hours * n

   println(calcPayment(30))

}
</pre>

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}
