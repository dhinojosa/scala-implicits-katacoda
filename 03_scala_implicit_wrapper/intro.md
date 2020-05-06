A wrapper enhances a class with your extra methods. Let's say that an integer in Scala needs to have an `isOdd` and `isEven` method. That would be nice but it doesn't.  We can create a wrapper to aid in this. We will go through various way of doing this.

1. Using an implicit method to enhance a class
2. Using an implicit function to enhance a class
3. Using an implicit class to enhance a class
4. Using a generic type with an implicit wrapper

The advantage for this is to cut the cruft and allow your API callers to express themselves in the shortest amount of keystrokes possible without the need for multiple adapters.