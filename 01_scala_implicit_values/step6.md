## `implicit` to Bind Services

Now we can rewrite the previous step with an `implicit` notice by doing so, we do not have to explicitly set the `ExecutionContext` for every little thing it is assumed that we are using the `executionContext` that is defined in the value `executionContext`.  Compare and contrast the differences between this step and the previous step for understanding.

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">
package com.xyzcorp;

object MyApp extends App {
  import scala.concurrent._
  import java.util.concurrent.Executors

  val executor = Executors.newFixedThreadPool(4) //Java
  implicit val executionContext: ExecutionContext =
    ExecutionContext.fromExecutor(executor)

  val future = Future.apply {
    println(s"Thread-name: ${Thread.currentThread().getName}")
    Thread.sleep(3000)
    50 + 100
  }(executionContext)

  future
    .map(x => x * 100)(executionContext)
    .foreach(a => println(a))(executionContext)
}
</pre>

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}

