## Primitive Conversions

Every "Primitive" or any type that extends from `AnyVal` has an `implicit` wrapper associated with it. The wrapper names are usually predicated with the word `Rich`.  For example, `RichInt`, `RichFloat`, etc. These conversions happened automatically without you even really considering it.

Here is an example of the conversion from [the Predef source](https://github.com/scala/scala/blob/v2.13.2/src/library/scala/Predef.scala#L529)

```scala
implicit def intWrapper(x: Int): runtime.RichInt = new runtime.RichInt(x)
```

What is contained in these values? let's take an example of [RichInt](https://github.com/scala/scala/blob/v2.13.2/src/library/scala/runtime/RichInt.scala)


Enter the following into your editor:

<pre class="file" data-filename="src/MyApp.scala" data-target="replace">

package com.xyzcorp;

object MyApp extends App {

  //max comes from RichInt
  println(10.max(3))

  //to is a method in RichInt, this is how a range is created
  (1 to 10).foreach(println)

  //toHexString is a method in RichInt
  println(30.toHexString)
}

</pre>

We will then compile

`scalac -d target src/MyApp.scala`{{execute}}

Then we will run

`scala -cp target com.xyzcorp.MyApp`{{execute}}
