`BigInt` too has a wrapper that adds [functionality](https://www.scala-lang.org/api/current/scala/math/BigInt.html).  We saw in the previous step that there is a method `+`, which adds two `BigInts`. If you look at the API, `BigInt` is merely a wrapper around `java.lang.BigInteger` that has `addition`, `subtraction`, `power`, `max`, `min`, `to`, and `until` for large ranges.

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;

object MyApp extends App {
  println(BigInt("2023949239324") + 10)
  println(BigInt("2023949239324") - 10)
  println(BigInt("2023949239324").pow(3))

  //Using a BigInt range
  BigInt("3023020233") to BigInt("3023020239") foreach (println)
}

</pre>

Clear the screen

`clear`{{execute}}

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

