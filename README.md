# Angellandros GitHub Blog
Muhammad-Ali A'rabi Homepage

ΑΓΕΩΜΕΤΡΗΤΟΣ ΜΗΔΕΙΣ ΕΙΣΙΤΩ

## Scala Wars
This side of the page is dedicated to Scala programming language.

### H2H Scala Course, CafeBazaar

__Exercise 1.__
What is the problem with this anonymous function?
```scala
val l = (1 to 5).toList
l foreach { println(_*2) }
```

__Exercise 2.__
Write a code in Scala which estimates `Pi = 3.14`. The code should scan an integer from `stdin`, which is the number of iterations. Do it with `val n = readLine.toInt`.
Use <ideone.com> to compile and test the code, and share the link after you have succeeded.
You can use `scala.util.Random` class in your code if you want:
```scala
import scala.util.Random

object Main extends App {
    val r = Random()
    val n = readLine().toInt
    ...
    val someRandomDouble = r.nextDouble()  // generates a double between 0.0 and 1.0
    ...
    println(pi)
}
```

