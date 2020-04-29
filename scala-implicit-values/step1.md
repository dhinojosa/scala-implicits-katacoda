## `implicitly` Basics

`implicitly` summons a type that has bound implicitly within the context or any parent context.

In the following we bind an `IceCream` flavor as the flavor of the month, but we are not giving the caller of our method `orderIceCream` an opportunity the set the Flavor of the Month. It is hidden behind the signature.

Enter the following into your editor:

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;

case class IceCream(name: String)
case class Scoops(num:Int, flavor:IceCream)

//Flavor of the month
implicit val flavorOfTheMonth: IceCream = IceCream("Rainbow Sherbet")

object MyApp extends App {
      def orderIceCream(num:Int) = {
        Scoops(num, implicitly[IceCream])
      }
      assert(orderIceCream(4) == (Scoops(4, IceCream("Rainbow Sherbet"))))
}
</pre>

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}


