If we have an abstract data type of currencies and a method combine that only accepts `Dollar` we can use a conversion to convert from a normal `Int` to a `Dollar`.

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

   //Only Dollars Allowed
   def combine(x:Dollar, y:Dollar):Dollar = Dollar(x.value + y.value)

   //Calling combine with Int not Dollars but it works!
   println(combine(100, 100))

}

</pre>

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

Notice the call to `combine`, we are calling the method with two `Int`. The `implicit def int2Dollar` since it is in scope will perform the conversion
