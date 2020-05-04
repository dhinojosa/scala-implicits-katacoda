## Using a generic type with an `implicit` wrapper

What if we want to apply a certain wrapper to every object that is in Scala within a particular scope?  This is where a parameterized type really shines.  In the following example we will use `[A]` to represent any type.

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;


object MyApp extends App {
   implicit final class ExclaimClass[A](private val v:A) {
      def exclaim:String = v.toString + "!"
   }

   println(10.exclaim)
   println("Hello".exclaim)
   println(List(1,2,3).exclaim)
}

</pre>

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

Notice above, that we are not wrapping anything in particular just the generic type `A`. But what it does give us is the ability to call the `exclaim` method on just about any value.
