`implicitly` can also differentiate parameterized types

In the following we can create a `List[String]`, where the square brackets will contain the parameterized type.  We can also create a `List[Int]`.  In the JVM, both `String` and `Int` will be erased and not known during _runtime_. When it comes to implicit resolution that is done at _compile-time_ so the `String` and the `Int` are still known and are distinct.


Enter the following into your editor:

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

implicit val listOfString: List[String] = List("Foo", "Bar", "Baz")
implicit val listOfDouble: List[Double] = List(1.0, 2.0, 3.0)

val result = implicitly[List[Double]]
result(1) should be (2.0)
</pre>

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}
