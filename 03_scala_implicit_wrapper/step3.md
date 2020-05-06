Why use a method or a function, when we can just put an `implicit` in front of the class definition and get the same thing. Before we do here are some rules:

1. They can only be used inside of an `object`/`trait`/`class`
2. They can only take one parameter in the constructor
3. There can not be any colliding method name as that with the `implicit` outer scope

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;


object MyApp extends App {
   //Notice that we have an implicit keyword in front of class

   //Also notice I cannot violate rule number 1, I must put it
   //in a trait, object, or class

   implicit class IntWrapper(x:Int) {
      def isOdd: Boolean = x % 2 != 0
         def isEven: Boolean = !isOdd
   }

  // Tell the compiler that I intend to perform a conversion
  import scala.language.implicitConversions
 
  // No methods or function definitions required 
  
  println(10.isOdd)
  println(10.isEven)
}

</pre>

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

Notice above, we don't have a method or function, but the enhancement still works. That is because of the `implicit` in front of the `class` definition
