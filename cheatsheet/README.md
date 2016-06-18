## Scala Cheatsheet

### Values

Scala immutable names

```scala
    val n = 21          // type automatically assigned as Int
    val d: Double = 21  // explicit type declaration
```

You cannot reassign to values, but you can redefine them:

```scala
    val two = 2  // first assignment
    two = 3      // causes error: reassignment to val
    val two = 3  // works fine
```

A value could not be reassigned, but can contain a pointer to a mutable object:

```scala
    val jhm = new java.util.HashMap[Int, String]()  // a pointer to the mutable object is assigned to jhm
    jhm.set(1, "one")                               // works fine
    
    val mhm = new scala.collection.mutable.HashMap[Int, String]()
    mhm = mhm + (2 -> "two)  // causes error: reassignment to val
    mhm += (2 -> "two")      // works fine, because  +=  is a member of mutable HashMap class
```

### Variables

Scala names that can vary, same as C++ variable

```scala
    var n = 5
    n = 6
    
    var l = List(1, 2, 3)
    l += 4         // error
    l = l.drop(2)  // fine
```

### Functions

Callable things

```scala
    // classic function
    def f(a: Int): Double = {
      var returnValue: Double = 0
      ...
      returnValue  // last line is returned
    }
    
    def square(a: Int) = { a*a }      // no explicit return type
    def triple(a: Int) = 3*a          // no braces
    def sum(a: Int*) = a.reduce(_+_)  // function with varargs
    def one() = 1                     // no arguments
    def two = 2                       // no parentheses
```

#### Anonymous Function

Functions with no name

```scala
    (x: Int) => x*x  // no name
    x => x*x         // no argument type, when there is no ambiguation
    2*_              // underscore as once-used argument, when there is no ambiguation in the type of argument
    _*_              // same as (a, b) => a*b
    
    import scala.language.postfixOps
    2*               // same as _*2 or 2*_, *2 won't work since * is a postfix operator returning a function
```

#### Type of Functions

A function `(a1: T1, ... , an: Tn): T` has the type `(T1, ... , Tn) => T`:

```scala
    def f(a: Int) = a.toString           // f has the type Int => String
    def add(a: Double, b: Double) = a+b  // has the type (Double, Double) => Double
```

#### Higher Order Functions

Are functions that return functions:

```scala
    def f(a: Int) = {
      def g(b: Int) = a*b
      g _  // return g of the type Int => Int
    }
    
    def f(a: Int) = (b: Int) => a*b       // same function
    def f(a: Int): Int => Int = b => a*b  // same function
    def f(a: Int): Int => Int = a*_       // same function
    
    import scala.language.postfixOps
    def f(a: Int): Int => Int = a*        // same function
```

#### Currying

Converting a function with multiple arguments into a function with a
single argument that returns another function:

```scala
    def f(a: Int, b: Int): Int // uncurried version (type is (Int, Int) => Int)
    def f(a: Int)(b: Int): Int // curried version (type is Int => Int => Int)
```

### Evaluation Rules

- Call by value: evaluates the function arguments before calling the function
- Call by name: evaluates the function first, and then evaluates the arguments if need be

```scala
    def example = 2      // evaluated when called
    val example = 2      // evaluated immediately
    lazy val example = 2 // evaluated once when needed
    
    def square(x: Double)    // call by value
    def square(x: => Double) // call by name
    def myFct(bindings: Int*) = { ... } // bindings is a sequence of int, containing a varying # of arguments
```
