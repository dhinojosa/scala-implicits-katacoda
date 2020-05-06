There is nothing wrong with the previous **step** _unless_ you don't want anyone overriding the flavor of the month and making their own choice.  If you are a "My Way or the Highway" kind of ice cream vendor, then the previous scenario is not for you, the following demonstrates how easy it is to plugin your favorite ice cream.

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
  assert(orderIceCream(4)(IceCream("Rocky Road")) == (Scoops(4, IceCream("Rocky Road"))))
}
</pre>

Clear the screen

`clear`{{execute}}

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

Notice that the Ice Cream Flavor is `Rocky Road`. How dare my customers make free-will choices when it comes to ice cream? We need to put an end to this contempt in the next step.
