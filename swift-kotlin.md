# Swift vs Kotlin

Resources:
https://www.cubix.co/blog/kotlin-vs-swift/
https://willowtreeapps.com/ideas/swift-and-kotlin-the-subtle-differences
https://www.raywenderlich.com/6754-a-comparison-of-swift-and-kotlin-languages

Simple Syntactical Differences:

**Constructor**  
Swift - init(a: Int)  
Kotlin - constructor(a: Int)

**Immutable variable**  
Swift - let a = 3  
Kotlin - val a = 3

**Mutable variable*  
Swift - var a = 3  
Kotlin - var a = 3

**Self object referencing**  
Swift - self.a = a  
Kotlin - this.a = a

**Arrays**  
Swift - let arr = [“hello”, “world”]  
Kotlin - val arr = arrayOf(“hello”, “world”)

**Dictionaries/Maps**  
Swift - let dict = [“hello”: “world”]  
Kotlin - val dict = hashMapOf(“hello” to “world”)

**Type inference**  
Swift - let a: Float = 0.0  
Kotlin - val a: Float = 0.0

**Function declaration**  
Swift - func sampleMethod() -> Int  
Kotlin - fun sampleMethod(): Int

**Function default parameters**  
Swift - func sampleMethod(a: Int = 0) -> Int  
Kotlin - func sampleMethod(a: Int = 0): Int

**If statements**  
Swift - if a == b {}  
Kotlin - if (a == b) {}

**For loops**  
Swift - for movie in movies  
Kotlin - for (movie in movies)

**Default values**  
Swift - let a = b?.value ?? 0
Kotlin - val a = b?.value ?: 0

Safe casting
Swift - let b = a as? Int
Kotlin - val b = a as? Int

Safe call
Swift - b?.print()
Kotlin - b?.print()

Force unwrap
Swift - b!.print()
Kotlin - b!.print()

Lazy initialization
Swift - lazy - var array2: [Int] = []
Kotlin - val array2 by lazy { intArrayOf() }




Data Class
Kotlin - Kotlin has a data class to allow developers to implement things like copying and equality.
A class that when compiled, gets methods such as hashCode(), toString(), and copy(). 
Can be defined like this: 
data class SampleClass(var a: Int = 0, var b: Int = 0, var c: String = “”)

Swift - Swift does not have a counterpart for data class.

Structs
Swift Structs:
Swift Structs are value types
Swift Classes are reference types
Value types are copied when assigned to a new variable or when passed as a parameter.

Kotlin doesn’t have a Struct type. However, you can instead use a copy function to create a new reference.
let sample = SampleClass(1, 1, “Sample”)
let newSample = sample.copy()

Kotlin Data Class is a reference type.
Swift Structs are value types.
Both can be used to hold data.


Function Implementation
Kotlin - Kotlin features $ prefix to return to the argument and no prefix for the variable.
Swift - Swift has the variable in braces and forward slash (\) to return to the argument and underscore (_) for the variable.

Default Class
Kotlin - Kotlin does not allow alterations or extensions
Swift - Swift allows extensions

Error Handling
Kotlin - Kotlin indicates with ‘null’
Swift - Swift shows error handling with ‘nil’

Enums
Enums/Sealed Classes and Switch/When
Kotlin - Kotlin does not have Enums; Kotlin’s enums are a predetermined set of constants for a type.
Swift - Swift offers an enums list for computation properties, Struct features, and other values.
Swift’s enums are data types defined by two constructions: products and sums. Swift’s enums can use associated values.

Swift Enum example:
enum Game {
	case baseball(Int, String)
	case football(Int, Int, Time)
	case basketball(Int, Time)
}

let game = Game.baseball(4, "2-2")
switch game {
case .regular:
case .baseball(let inning, let count):
case .football(let down, let yardsToGo, let timeLeft):
case .basketball(let quarter, let timeLeft):
}

Kotlin enum example:
The difference between Kotlin’s Sealed Class and Swift’s Enums is that sealed class is a reference type, while Swift’s Enums are value types.
sealed class Game {
      object RegularGame: Game()
	class BaseballGame(let inning, let count): Game()
	class FootballGame(let down, let yardsToGo, let timeLeft): Game()
	class BasketballGame(let quarter, let timeLeft): Game
}

let game = BaseballGame(4, "2-2")

when(game) {
     is Game.RegularGame -> // do stuff
     is Game.BaseballGame -> // do stuff
     is Game.FootballGame -> // do stuff
     is Game.BasketballGame -> // do stuff
}



Memory Management
Kotlin - Kotlin uses Garbage Collection for memory management.
Swift - Swift uses ARC or Automatic References Counting.

Annotations
Kotlin - Kotlin supports numerous annotations, including @Target, @Repeatable, @Retention, and @MustBeDocumented
Swift - Swift does not support annotations

Tuples
Kotlin - Kotlin has a Pair and a Triple utility class for tuples of 2 and 3 components and it has the data class that can be used to emulate a custom tuple.
data class SampleTuple(var var1: String, val var2: String, val var3: String)
//Definition of Pair data class Pair<out A, out B> 
//Definition of Triple data class Triple<out A, out B, out C>


Swift - Swift has tuples and uses it to outline the interfaces among components.
typealias SampleTuple = (var1: String, var2: String, var3: String)


Guard Statements
Kotlin - Kotlin does not feature guard statements. Developers need to adhere to the ‘if’ sentence then reverse the condition.
Swift - Swift has guard statements to check conditions.

Type Alias
Kotlin - Kotlin does not have type alias
Swift - Swift has a type alias

Delegated Properties
Kotlin - Kotlin has delegated properties for developers to add method citations to other classes
Swift - Swift does not have delegated properties.

Optionals:
Swift and Kotlin both allow for optional types.
Swift’s Optional is an enum that has two values: some(value) and none. This allows for the optional type to always have a value to its pointer.
Kotlin uses null values. For Kotlin nullables, null pointers are still used, but with its type system, you can determine if a variable should be allowed to contain a null pointer. The goal of Kotlin nullables is to help with the issue of NullPointerException and add more tools for type checking.

Swift Optional Example:
struct SampleStruct {
    var id: Int?
    var thing1: String
    var thing2: String
    var thing3: String?
}

func printOut(sampleStruct: SampleStruct) {
    guard let id = sampleStruct.id else {
        print("Invalid id, cannot print things")
        return
    }
    print(sampleStruct.thing1)
    print(sampleStruct.thing2)
    if let thing3 = sampleStruct.thing3 {
        print(thing3)
    }
}

Kotlin Optional Example:
data class SampleClass(var id: Int?, var thing1: String, var thing2: String, var thing3: String?)

fun printOut(sampleClass: SampleClass) {
   val id = sampleClass.id ?: run {
       print("Invalid id, cannot print things")
       return
   }
   print(id)
   print(sampleClass.thing1)
   print(sampleClass.thing2)
   val thing3 = sampleClass.thing3
   if (thing3 != null) {
       // smart cast on a null check
       print(thing3)
   }
   // OR
   sampleClass.thing3?.let {
       print(it)
   }
}


Implicit Unwrapping vs lateinit
Swift has implicit unwrapping, which defines an optional but tells the compiler that it can unwrap it because it will have a value when ready.
Kotlin has something similar using the lateinit keyword. 
Useful for dependency injection - setting values in a type after initizializtion

Swift:
var string: String!
func doBadStuff() {
   string.doSomething() // Will crash because string doesn’t have a value
}
---------------------
string = “String”
func doGoodStuff() {
   string.doSomething() // This is good because string was set.
}


Kotlin
lateinit var string: String
fun doBadStuff() {
   string.doSomething() // Will crash because string doesn’t have a value
}
---------------
string = “String”
fun doGoodStuff() {
    string.doSomething() // This is good because string was set.
}




Extensions
Swift and Kotlin have extension capabilities. Extensions add functionality to an already existing type. You can extend say the Int type, for example, but the syntax for both is totally different.

Swift:
extension Int { var doubled: Int { return self * 2 } } 
let a = 1.doubled

Kotlin:
var Int.doubled: Int get() = this * 2 
val a = 1.doubled


Protocols + Interfaces
Protocols and Interfaces are almost the same thing. 
A couple of differences:
Kotlin allows you to provide default functionality for a method
Swift requires an extension of the protocol in order to give an implementation.
Regarding generics:
Kotlin allows for generics to go in the definition of the interface
Swift allows you to define an associatedType to go along with conformance

Swift sample:
protocol SampleProtocol {
	associatedType T
	func get(value: T) -> T
}

extension SampleProtocol where Self.T == Self  {
	func get(value: Self) -> Self {
		// do stuff
	}
}

struct SomeClass: SampleProtocol {
     func get(value: SomeClass) -> SomeClass {
           // do stuff
     }
}

Kotlin
interface SampleInterface<T> {
   fun get(value: T): T {
       // do stuff
   }
}

class SomeClass: SampleInterface<Int> {
   override fun get(value: Int): Int {
       // do stuff
   }
}


Higher Order Functions
Higher Order Functions are essentially functions that accept closures or functions as parameters and return either a new value or another function. With higher order functions, we are able to transform, filter, and iterate through values such as arrays.

Swift Higher Order Function sample
func higherOrderFunctions() {
    let array = [1,2,3,4,5,6,7,8,9,10]
    // $0 is implicitly defined as the current value of the spot you are at     in an array
    let mappedArray = array.map {
        $0 * 2
    }
    let filteredArray = array.filter {
        $0 % 2 == 0
    }
    // $0 is not an option because the current value in the closure is now defined as (acc, element)
    let reducedArray = array.reduce(0) { (acc, element) in
        return acc + element
    }
}

Kotlin Higher Order Function sample
fun higherOrderFunctions() {
   val array = arrayOf(1,2,3,4,5,6,7,8,9,10)


   // it is implicitly defined as the value of the spot you are at     in an array
   val mappedArray = array.map {
       it * 2
   }
   // result: [2,4,6,8,10,12,14,16,18,20]

   val filteredArray = array.filter {
       it % 2 == 0
   }
   // result: [2,4,6,8,10]
   // it is not an option because the current value in the closure is now defined as acc, element
   val reducedArray = array.reduce { acc, element ->
       acc + element
   }
   // result: 55
}


Lambdas vs Closures
Unnamed functions that can be assigned to variables and passed around like any other value. 

Kotlin - Lambda
val square = { a:Int -> 
  a * a
}
println(square(4) //16

Kotlin scope functions 
Run
Apply
Also
Let
With

Labels
Return@
Objects as singleton 
Companion objects
Coroutines




SwiftUI and Compose are the declarative frameworks for each.

