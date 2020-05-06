Now we can rewrite the previous step with an `implicit` notice by doing so; we do not have to set the `ExecutionContext` explicitly.  Every time we have a method that requires an `ExecutionContext`, we use the `executionContext` that is bound implicitly  Compare and contrast the differences between this step and the previous step for deeper understanding.

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">
package com.xyzcorp;

object MyApp extends App {
  import scala.concurrent._
  import java.util.concurrent.Executors

  val executor = Executors.newFixedThreadPool(4) //Java
  implicit val executionContext: ExecutionContext =
    ExecutionContext.fromExecutor

  val future = Future.apply {
    println(s"Thread-name: ${Thread.currentThread().getName}")
    Thread.sleep(3000)
    50 + 100
  }

  future
    .map(x => x * 100)
    .foreach(a => println(a))
}
</pre>

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

