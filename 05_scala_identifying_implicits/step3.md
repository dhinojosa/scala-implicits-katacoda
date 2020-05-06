## `BigInt` Conversions

`BigInt` is a Scala implementation of what `java.lang.BigInteger` is in Java with some special features.  We can create `BigInt` in much of the same way as the Java equivalent, but where the comparisons end is how we can interact with it.  In regards to `implicit`s, `BigInt` will convert any integer that you interact with it. In the following code, we don't need to convert `10` to a `BigInt(10)` before interacting with `BigInt("2023949239324")`, that is automatic.  Thanks to implicit conversions it takes care of the hard work.

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;

object MyApp extends App {
  println(BigInt("2023949239324") + 10)
}

</pre>

Clear the screen

`clear`{{execute}}

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

