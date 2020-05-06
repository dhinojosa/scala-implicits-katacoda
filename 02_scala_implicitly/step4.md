`implicitly` can also differentiate parameterized types.

In the following example, we can create a `List[String]`, where the square brackets contain the parameterized type.  We can also create a `List[Int]`.  In the JVM, both `String` and `Int` are erased and not known during _runtime_. The implicit resolution takes place at _compile-time_, so the `String` and the `Int` are still known and are distinct.

Enter the following into your editor:

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">
package com.xyzcorp

object MyApp extends App {
  implicit val listOfString: List[String] = List("Foo", "Bar", "Baz")
  implicit val listOfDouble: List[Double] = List(1.0, 2.0, 3.0)

  val result = implicitly[List[Double]]
  println(result(1))
}
</pre>

Clear the screen

`clear`{{execute}}

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

Notice `implicitly[List[Double]]` retrieves the right `List` when we ask for the first item from a zero-based `List`.
