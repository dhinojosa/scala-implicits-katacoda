## `implicit` Basics

`implicit`s are like a `Map[Class[A], A]` where `A` is any object and it is tied into the scope, and it is there when you need it, hence it is implicit. This provide a lot of great techniques that we can use in Scala.

`implicit`s are done per scope so in the following example, we will begin with an `implicit` value and call it from inside a method which uses a multiple parameter list where one one group would accept the value as a parameter, and the other would receive the implicit value.

Enter the following into your editor

<pre class="file" data-filename="Step1.scala" data-target="replace">

package com.xyzcorp;

object Step1 extends App {

   implicit val rate: Int = 100

   def calcPayment(hours:Int)(implicit n:Int) = hours * n

   println(calcPayment(30))

}
</pre>

We will then compile

`scalac Step1.scala`{{execute}}

Then we will run

`scala com.xyzcorp.Step1`{{execute}}
