
# Scala basics (case class, companion object)



``` scala
case class Building(location: String, private var secrets: String)
object Building {
   def hearsay(d: Building) = s"I heard that ${d.secrets}"
}
```
---
# Scala basics (traits)
``` scala
trait Farm { def acres : Int}
trait MinkCages { def skinFur() = "silver colered fur" }
case class McDonaldHouse(acres: Int = 54) extends Farm
```
---
# Guess valid code(traits)
``` scala
trait Animal { def sound : String }
trait TailShaker { def happy = "shake tail" }
case class Cow(name: String) extends Animal
class Bull extends Animal { def sound = "Big muuh"}
new Bull() with TailShaker
```
---
# Scala basics (generics and inference)
``` scala
object PoorInference{
   def convert[T, U](value: T, func: T => U) = func(value)
}
val f : Int => Int = x => x +2
PoorOnference.convert(2, f)
case class Box[T](value: T){ 
   def convert[U](func: T => U) = func(value) 
}
Box(2)
Box.convert(x => + 2)
```