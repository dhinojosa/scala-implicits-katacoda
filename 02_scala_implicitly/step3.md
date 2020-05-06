`implicitly` summons a type that has bound implicitly within the context or any parent context.

In the following example, we bind an `IceCream` flavor as the flavor of the month. This time, we are not giving the caller of our method `orderIceCream` an opportunity the set the Flavor of the Month, not in this Ice Cream shop. The `implicitly` is hidden behind the signature.

Enter the following into your editor:

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;

case class IceCream(name: String)
case class Scoops(num:Int, flavor:IceCream)

object MyApp extends App {
  //Flavor of the month
  implicit val flavorOfTheMonth: IceCream = IceCream("Rainbow Sherbet")

  def orderIceCream(num:Int) = {
    Scoops(num, implicitly[IceCream])
  }
  println(orderIceCream(4))
}
</pre>

Clear the screen

`clear`{{execute}}

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

Now we give our customers what they should be enjoying, Rainbow Sherbet.
