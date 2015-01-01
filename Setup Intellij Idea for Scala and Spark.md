# Setup IntelliJ Idea for Scala

- based on Idea community edition 14
- SBT
- Scala 

[install Idea for coursera class]: https://www.youtube.com/watch?v=xtMfNcBL8g8
[very good step by step for setting up Spark]: http://apache-spark-user-list.1001560.n3.nabble.com/Is-there-a-step-by-step-instruction-on-how-to-build-Spark-App-with-IntelliJ-IDEA-td18473.html

I used this two links for my setup:

- [install Idea for coursera class]
- [very good step by step for setting up Spark]

## Setup Scala

- use manual installation, down load SBT, Scala, unzip them and
- add bin directories to PATH (zshrc file)

Because the video and tutorial is a little old, the SBT and Scala versions are out of date, they need to update. SBT code,

```
name := "Hello"

version := "1.0"

scalaVersion := "2.11.4"

libraryDependencies += "org.scalatest" % "scalatest_2.11" % "2.2.1" % "test"
```

Testing code for hollo,

```
package demo

/**
 * Created by rkuo on 1/1/15.
 */
class HelloTest extends org.scalatest.FunSuite {
  test("sayHello method works correctly") {
    val hello = new Hello
    assert(hello.sayHello("Scala") == "Hello, Scala!")
  }
}
```
Main program,

```
package demo

/**
 * Created by rkuo on 1/1/15.
 */
class Hello {
  def sayHello(name: String) = s"Hello, $name!"
}
```

code for worksheet,

```
import demo.Hello

val hello = new Hello
println(hello.sayHello("Scala"))
```

This is very good workflow example; 

- write test code first,
- implement method to pass test,
- use worksheet for real value test.

I did not do project importing portion of tutorial. 
