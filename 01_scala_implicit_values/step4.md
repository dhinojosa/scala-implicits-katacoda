The compiler already griped at compile time that there were two implicit bindings of the same type in the previous step. The following is the result of what happens when binding two values of the _different_ types. Notice now that both `rate` and `age` are no longer `String`, but their types, `Rate` and `Age` respectively. In the `calcPayment` method, we require a `Rate` type, and since `Age` has its type, there is no ambiguity.

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">
package com.xyzcorp;

object MyApp extends App {
  case class Rate(value:Int)
  case class Age(value:Int)

  implicit val rate: Rate = Rate(100)
  implicit val age: Age = Age(40)

  def calcPayment(hours:Int)(implicit rate:Rate) =
    hours * rate.value

  println(calcPayment(50))
}
</pre>

Clear the screen

`clear`{{execute}}

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}
