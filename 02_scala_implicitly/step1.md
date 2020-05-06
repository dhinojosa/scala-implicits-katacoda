Let's start from what we learned in the previous scenario, implicitly binding a type, in this case, an `IceCream`. We can then bring in the `IceCream` into an `implicit` method parameter.

Enter the following into your editor:

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;

case class IceCream(name: String)
case class Scoops(num:Int, flavor:IceCream)

object MyApp extends App {
  //Flavor of the month
  implicit val flavorOfTheMonth: IceCream = IceCream("Rainbow Sherbet")

  def orderIceCream(num:Int)(implicit flavorOfTheMonth:IceCream) = {
    Scoops(num, flavorOfTheMonth)
  }
  assert(orderIceCream(4) == (Scoops(4, IceCream("Rainbow Sherbet"))))
}
</pre>

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

Notice that the Ice Cream Flavor is `Rainbow Sherbet`.  But, this has the potential to be overridden.
