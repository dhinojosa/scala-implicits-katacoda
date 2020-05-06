The compiler will gripe at compile time if there are two implicit bindings of the same type.  It's worth noting that what Scala doing are compile time tricks for implicit. One strategy is to wrap a value in a type to avoid conflict. The following is the result of what happens when bind two values of the same type. Notice that both `rate` and `age` are both type of `Int`

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;

object MyApp extends App {
  implicit val rate = 100
  implicit val age = 40

  def calcPayment(hours:Int)(implicit rate:Int) =
      hours * rate

  calcPayment(50)
}
</pre>

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

We won't bother running because it will not compile
