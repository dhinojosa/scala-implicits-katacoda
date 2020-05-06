What if we want to apply a particular wrapper to every object that is in Scala within a particular scope?  An _implicit wrapper_ is where a parameterized type shines.  In the following example, we use `[A]` to represent any type.

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

Clear the screen

`clear`{{execute}}

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

Notice above that we are not wrapping anything in particular, just the generic type `A`. But what it does give us is the ability to call the `exclaim` method on just about any value.
