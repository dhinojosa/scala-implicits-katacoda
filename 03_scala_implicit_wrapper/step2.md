We can do everything in the last step, but instead of a method using `def` we can use a function `Int => IntWrapper`. The results are the same.

Enter the following into your editor:

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;

class IntWrapper(x:Int) {
  def isOdd: Boolean = x % 2 != 0
  def isEven: Boolean = !isOdd
}

object MyApp extends App {
  // Tell the compiler that I intend to perform a conversion
  import scala.language.implicitConversions
  
  // Define the conversion, for every Int wrap or adapt an IntWrapper
  // This is only applicable for this scope, inside the App
  // This is using a val and it is referencing a function

  implicit val int2IntWrapper: Int => IntWrapper = 
     (x:Int) => new IntWrapper(x)
  
  println(10.isOdd)
  println(10.isEven)
}

</pre>

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

Notice above, that we replaced the `def` with a function. `val` is assigned to an `Int => IntWrapper` where it wraps the argument or the original reference
