When ordering a `List`, you would need to establish _how_ you wish to sort certain items. That is where `Ordering[A]` comes in where `[A]` is a parameterized type of whatever you would like to order.  There are some `Ordering[A]` already built into the language, like `Ordering[String]`, `Ordering[Int]`,  and `Ordering[Float]`. To prove it, you can run, for example, `implicitly[Ordering[Int]]` and that would return the object representation of what is bound.  If you create a custom type, bind your own `Ordering[A]`, where `A` is your custom type. Below, we create a custom class `Employee` and an `implicit` `Ordering[Employee]` so it knows how to sort a collection of `Employee`s.

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;

case class Team(city:String, mascot:String)

//Create two choices to sort by, city and mascot
object MyPredef3 {
  implicit val teamsSortedByCity: Ordering[Team] =
    (x: Team, y: Team) => x.city compare y.city
  implicit val teamsSortedByMascot: Ordering[Team] =
    (x: Team, y: Team) => x.mascot compare y.mascot
}

object MyApp extends App {
  //Create some sports teams
  val teams = List(Team("Cincinnati", "Bengals"),
     Team("Madrid", "Real Madrid"),
     Team("Las Vegas", "Golden Knights"),
     Team("Houston", "Astros"),
     Team("Cleveland", "Cavaliers"),
     Team("Arizona", "Diamondbacks"))

  //import the implicit rule we want, in this case city
  import MyPredef3.teamsSortedByCity

  //min finds the minimum, since we are sorting
  //by city, Arizona wins.
  println(teams.min.city)
}

</pre>

Clear the screen

`clear`{{execute}}

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

Notice above, that we encased two `implicit`s definitions in an `object` with an arbitrary name called `Predef3`, this allows us to select one recipe for our scope, `teamsSortedByCity`.
