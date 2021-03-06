<!DOCTYPE html>
<html>
  <head>
    <title>Title</title>
    <meta charset="utf-8">
    <style>
      @import url(https://fonts.googleapis.com/css?family=Yanone+Kaffeesatz);
      @import url(https://fonts.googleapis.com/css?family=Droid+Serif:400,700,400italic);
      @import url(https://fonts.googleapis.com/css?family=Ubuntu+Mono:400,700,400italic);

      body { font-family: 'Droid Serif'; }
      h1, h2, h3 {
        font-family: 'Yanone Kaffeesatz';
        font-weight: normal;
      }
      .remark-code, .remark-inline-code { font-family: 'Ubuntu Mono'; }

    </style>
  </head>
  <body>
    <textarea id="source">
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

Once you accept your flaws noone can use them against you. 
who wrote it:
a. Herman Riel (Nazi)
b. Malcolm X
c. George R. R. Martin.

---

# It's all about context

Once you accept your flaws noone can use them against you. 
who wrote it:
a. Herman Riel (Nazi)
b. Malcolm X
c. George R. R. Martin.

---

# Postpone implementation and reuse
Lets look at some common cases
``` scala
sealed trait Identifiable { def id: String }
case class Mink(id: String, name: String) extends Identifiable
case class Cat(id: String, name: String) extends Identifiable
```
``` scala
object Writer {
    writeIDtoDisk(ident: Identifiable) = ???
    writeIDtoS3(ident: Identifiable) = ???
}
```
--
``` scala
sealed trait Writer( 
    def write(ident: Identifiable) : Unit
    val path : String )
case class S3Writer(....) extends Writer
case class DiskWriter(....) extends Writer

```
---
# Traits all over the place
``` scala
def moveAnimals(animals: List[Identifiable], writer : Writer) = ???
def blendAnimals(animals: List[Identifiable], writer : Writer) = ???
def sellAnimals(animals: List[Identifiable], writer : Writer) = ???
```
--
How about that factory stuff.
``` scala
def moveAnimals(animals: List[Identifiable]) = { 
    WriterFactory.get("ehm s3 or disk????")
}
```
-- 
``` scala
def moveAnimals(animals: List[Identifiable])(implicit writer: Writer) = ???
```
---
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


</textarea>
    <script src="https://remarkjs.com/downloads/remark-latest.min.js">
    </script>
<script>
  var slideshow = remark.create({
        highlightStyle: 'ir-black',
        highlightSpans: true
      });
      // extract the embedded styling from ansi spans
      var highlighted = document.querySelectorAll("code.terminal span.hljs-ansi");
      Array.prototype.forEach.call(highlighted, function(next) {
        next.insertAdjacentHTML("beforebegin", next.textContent);
        next.parentNode.removeChild(next);
      });
</script>
</body>
</html>