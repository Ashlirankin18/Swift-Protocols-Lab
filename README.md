
## Protocols Lab

## Instructions for lab submission 

1. Fork the assignment repo
1. Clone your Fork to your machine
1. Complete the lab
1. Push your changes to your Fork
1. Submit a Pull Request back to the assignment repo
1. Paste a link of the pull request on Canvas and submit

<pre> 
Question 1.
Create a Human class with two properties: name of type String, and age of type Int. You'll need to 
create a memberwise initializer for the class. Initialize two Human instances.

Make the Human class adopt the CustomStringConvertible. Print both of your previously initialized
Human objects.

Make the Human class adopt the Equatable protocol. Two instances of Human should be considered equal
if their names and ages are identical to one another. Print the result of a boolean expression 
evaluating whether or not your two previously initialized Human objects are equal to eachother
(using ==). Then print the result of a boolean expression evaluating whether or not your two
previously initialized Human objects are not equal to eachother (using !=).

Make the Human class adopt the Comparable protocol. Sorting should be based on age. Create another
three instances of a Human, then create an array called people of type [Human] with all of the
Human objects that you have initialized. Create a new array called sortedPeople of type [Human] 
that is the people array sorted by age.
</pre> 

```swift
class Human: CustomStringConvertible,Equatable,Comparable {
    static func < (lhs: Human, rhs: Human) -> Bool { // comparable
        return
        lhs.age < rhs.age
    }
    
    static func == (lhs: Human, rhs: Human) -> Bool { // Equatable
        return
        lhs.age == rhs.age && lhs.name == rhs.name
    }
    
    var description: String {
        return "the name of the human is \(name) and age \(age)"
    }

    var name: String
    var age: Int
    init(name:String, age:Int) {
        self.name = name
        self.age = age
    }
}

let john = Human(name: "John", age: 23)
let mary = Human(name: "Mary", age: 34)
let matthew = Human(name: "Matthew", age: 22)
print(john)
print(mary)
print(matthew)



if john == mary {
    print("they are the same")
} else {
    print("they are different")
}
var people = [john,matthew,mary]
let sortedPeople = people.sorted{$0.age < $1.age}
print(sortedPeople)

```

</br> </br> 


<pre> 
Question 2. 
Create a protocol called Vehicle with two requirements: a nonsettable numberOfWheels property of
type Int, and a function called drive().

Define a Car struct that implements the Vehicle protocol. numberOfWheels should return a value of 4,
and drive() should print "Vroom, vroom!" Create an instance of Car, print its number of wheels, 
then call drive().

Define a Bike struct that implements the Vehicle protocol. numberOfWheels should return a value of 2,
and drive() should print "Begin pedaling!". Create an instance of Bike, print its number of wheels,
then call drive().
</pre>  

``` Swift

protocol Vehicle {
    var numberOfWheels: Int { get }
    static func drive()
    
}

struct Car: Vehicle {
    var numberOfWheels: Int {
        return 4
    }
    
    static func drive() {
        print("Vroom, vroom!")
    }
}
let nissan = Car()
print(nissan.numberOfWheels)
Car.drive()


```




</br> 




</br> 

<pre> 
Question 3. 
// Given the below two protocols, create a struct for penguin(a flightless bird) and an eagle.
Give your structs some properties and have them conform to the appropriate protocols.

protocol Bird {
 var name: String { get }
 var canFly: Bool { get }
}

protocol Flyable {
 var airspeedVelocity: Double { get }
}
</pre> 
``` Swift

protocol Bird {
    var name: String { get }
    var canFly: Bool { get }
}

protocol Flyable {
    var airspeedVelocity: Double { get }
}

struct Penguin: Bird {
    var name: String
    var canFly: Bool
    var color: String
    
    
}
struct Egale: Bird, Flyable{
    var name: String
    var canFly: Bool
    var airspeedVelocity: Double
    
}
let penguin = Penguin.init(name: "Penguin", canFly: false, color: "black and white")
let eagle = Egale.init(name: "Egale", canFly: true, airspeedVelocity: 34.0)




```
</br> </br> 

<pre>
Question 4. 
// Create a protocol called Transformation

// create a mutating method called transform

// Make an enum called SuperHero (have it conform to Transformation) and an instance of it named
bruceBanner. Make it so that when the transform function is called that bruceBanner turns from 
.notHulk to .hulk.

enum SuperHero: Transformation {
    // write code here.
}

Example Output: 
var bruceBanner = SuperHero.notHulk

bruceBanner.transform() . // hulk

bruceBanner.transform()  // notHulk
</pre> 

</br> </br> 
``` Swift

protocol Transformation {
    mutating func transformation()
}

enum SuperHero: Transformation {
    case hulk, notHulk
    mutating func transformation() {
        switch self {
        case .hulk:
            self = .notHulk
        case .notHulk:
            self = .hulk
        }
    }
  
}
var bruceBanner = SuperHero.notHulk
bruceBanner.transformation()





```
<pre>
Question 5. 
// 1. Create a protocol called Communication

// 2. Give it a property called talk, of type String, and assign it an explicit getter.

// 3. Create three Classes. Cow, Dog, Cat.

// 4. Have your three classes conform to Communication

// 5. talk should return a unique message for each animal when talk is called.

// 6. Put an instance of each of your Classes in an array.

// 7. Iterate over the array and have them print talk.
</pre> 

``` Swift
protocol Communication {
    var talk: String {get set}
}

class Cow: Communication, CustomStringConvertible{
    var description: String {
       return  "the sound the cow makes is \(talk)"
    }
    
    var talk: String = "MOOOOOOOOO"
    
}

class Dog: Communication, CustomStringConvertible{
    var description: String {
       return "the sound the dog makes is \(talk)"
    }
    
    var talk: String = "RUFFFF"
    
}
class Cat: Communication, CustomStringConvertible{
    var description: String {
        return  "the sound the cat makes is \(talk)"
    }
    
    var talk: String = "Meow"
}

let blackCat = Cat.init()
let brownDog = Dog.init()
let cow = Cow.init()

let animals = [blackCat,brownDog,cow] as [Any]

for animal in animals{
    print(animal)
}



```
