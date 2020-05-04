## The arrow wrapper

There is a term that is used a lot and that is "syntactic sugar". When someone says "syntactic sugar", it usually means that language designers made a special consideration in the structure of language or bent their rules to allow someone to do something.  The `->` is not syntactic sugar, it is the adapter pattern - simplified by the compiler.

One of the well known `implicit` wrappers that is already in use currently in `Scala` is the `->` wrapper.  `->` will take the left hand, and the right hand of the arrow, whatever type it may be and turn it into a `Tuple2`.  These definitions reside in an `object` called [`Predef`](https://github.com/scala/scala/blob/v2.13.2/src/library/scala/Predef.scala) which is automatically imported into any Scala file.

It is used most commonly in creating a `Map[K,V]`, since the `apply` factory method requires a `Tuple2[A,B]*` repeated parameter

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;

object MyApp extends App {

  // -> creates a Tuple2
  val m = 1 -> "One"
  println(m)

  // Calling Map.apply with repeated parameters of Tuple2
  val map = Map(1 -> "One", 2 -> "Two", 3 -> "Three")
  println(map)
}

</pre>

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}
