## Converting Java to Scala Collections

We need to call Java often, but Java's collections may not be immutable which is a Scala standard, and Java's collection don't have quite the list of methods and functions that we love, so conversions are necessary. To do so, import `scala.collection.JavaConverters._` and don't forget the underscore at the end.  This will ensure that all `implicit`s that are bound in the `JavaConverters` object is available. The following example, uses Java's `java.time` API to get all the time zones in the world, then we are calling a decorator provided by `JavaConverters` called `asScala` to convert the Java Collection into a Scala Collection. Once we have our Scala collection we are using our functional programming prowess to find all the time zones in "America"

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;

object MyApp extends App {
   import scala.collection.JavaConverters._
   import java.time._

   println(ZoneId.getAvailableZoneIds
     .asScala
     .toSet
     .filter(s => s.startsWith("America"))
     .map(s => s.split("/").last)
     .toList
     .sorted)
}

</pre>

Clear the screen

`clear`{{execute}}

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

NOTE: For newer versions of Scala, this has been replaced by [CollectionConverters](https://www.scala-lang.org/api/current/scala/jdk/CollectionConverters$.html)
