The following is the same as the previous step, the only difference is we are defining our `implicit` as a function.

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;

import scala.language.implicitConversions

//Abstract Data Type of Various Currencies
sealed abstract class Currency
case class Dollar(value:Int) extends Currency
case class Yuan(value:Int) extends Currency
case class Euro(value:Int) extends Currency

object MyApp extends App {

   implicit def int2Dollar(i:Int):Dollar = Dollar(i)

   //Only Dollars Allowed, this time with a function
   implicit val int2Dollar: Int => Dollar = (i:Int) => Dollar(i)

   //Calling combine with Int not Dollars but it works!
   println(combine(100, 100))
}

</pre>

Clear the screen

`clear`{{execute}}

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

Notice the call to `combine`, we are calling the method with two `Int`. The difference is that we are using `implicit val int2Dollar`, a function, instead of a method.
