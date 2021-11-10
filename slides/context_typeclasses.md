# Recap
case class, trait, Describe data

--
``` scala
Box[T](value: T)
```
When we put a type in a "box", type inference improves on calls later.

--
terminal examples (lets look at things in boxes)


# It's all about .......

Story ....
is it about:
a.
b.
c.


# Postpone implementation and reuse
Lets look at some common cases
``` scala
trait Identifiable { def id: String }
case class Mink(id: String, name: String) extends Identifiable
case class Cat(id: String, name: String) extends Identifiable
```
``` scala
object Writer {
    writeIDtoDisk(ident: Identifiable) = ???
    writeIDtoS3(ident: Identifiable) = ???
}
```
``` scala
sealed trait WriterType()
case class S3Writer
case class DiskWriter
Writer[T](conf: Configuration) { def write ..... }
```

# Where do we use context
- Configuration
- Behavior
- Extension types

# How do we set them
Java ,  Spring, Guice dependency injection
Scala, implicits
loads of examples here



# Exercise 1 (Wire it up)
munit + sbt_console

wire up some code such that tests pass

# Creating a console serializer 
(hands on scala chap 5)

# Pros & Cons about implicits
compile time
performance
warts, changes in scala 3
type conversions

# Exercise 2 (lets extends some things)
