## `implicit` wrappers

A wrapper enhances a class with your extra methods. Let's say that an integer in Scala needs to have an `isOdd` and `isEven` method. That would be nice but it doesn't.  We can create a wrapper 

```scala
class IntWrapper(x:Int) {
   def isOdd = x % 2 != 0
   def isEven = !isOdd
}
```

To do this generally we would need create the wrapper following.

```scala
val wrap = new IntWrapper(3)
println(wrap.isOdd)
```

But can we get rid of this extra step? That is what this section is about.
