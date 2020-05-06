Implicits are really used to bind services that require something and you don't particularly need to inject everywhere explicitly, in this case let's discuss `Future[+T]`.  `Future` in Scala cannot run without an `ExecutionContext`. The issue is that there are so many calls that require an `ExecutionContext`. In the following example, here is running a `Future[+T]` without an `implicit`, notice how verbose it is.

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">
package com.xyzcorp;

object MyApp extends App {
  import scala.concurrent._
  import java.util.concurrent.Executors

  val executor = Executors.newFixedThreadPool(4) //Java
  val executionContext: ExecutionContext =
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

Notice that the answer (`15000`) will appear 3 seconds later
