# Structs and Classes Lab - 2


## Question 1

Using the Room struct below, write code that demonstrates that it is a value type.

```swift
struct Room {
     let maxOccupancy: Int
     let length: Double
     let width: Double
}

```


```
struct Room {
var maxOccupancy: Int
var length: Double
var  width: Double
}
var condo = Room(maxOccupancy: 3, length: 10.0, width: 15.0)

condo.maxOccupancy
condo.length
condo.width

var newCondo = condo
newCondo.maxOccupancy = 5
print(newCondo)
print(condo)
```

## Question 2

Using the Bike class below, write code that demonstrates that it is a reference type.

```swift
class Bike {
    var wheelNumber = 2
    var hasBell = false
}
```

```
class Bike {
var wheelNumber = 2
var hasBell = false
}
let freddiBike = Bike ()

print(freddiBike.wheelNumber)
let newBike = freddiBike
print(newBike.wheelNumber)
freddiBike.wheelNumber = 3
print(freddiBike.wheelNumber)
newBike.wheelNumber
print(newBike.wheelNumber)

```

## Question 3

a. Given the Animal class below, create a Bird subclass with a new `canFly` property.

```swift
class Animal {
    var name: String = ""
    func printDescription() {
        print("I am an animal named \(name)")
    }
}

class Animal {
var name: String

init(name: String) {
self.name = name
}
func printDescription () {
print("I am an animal named \(name)")
}
}

let newAnimal = Animal(name: "Polly")
newAnimal.name

class Bird: Animal {
var species: String
var canFly: Bool

init(name:String, species: String, canFly: Bool) {
self.canFly = canFly
self.species = species
super.init(name: name)
}
}



```

b. Override the printDescription method to have the instance of the Bird object print out its name and whether it can fly


## Question 4

```swift
class Bike {
  let wheelNumber = 2
  let wheelWidth = 1.3
  var hasBell = true
  func ringBell() {
    if hasBell {
      print("Ring!")
    }
  }
}

class Bike {
var wheelNumber = 2
var wheelWidth = 1.3
var hasBell = true
func ringBell() {
if hasBell {
print("Ring!")
}
}
}

class Loudbike: Bike {

var color: String
init (color: String, wheelNumber: Int, wheelWidth: Double, hasBell: Bool) {
self.color = color
 hasBell: hasBell)
}
override func ringBell() {
if hasBell {
print("RING! \(printRingBell(times: 4)) times ")
}
}

private func printRingBell(times: Int) -> Int {
return times
}
}

let louderBike = Loudbike(color: "pink", wheelNumber: 2, wheelWidth: 3.0, hasBell: true)
louderBike.ringBell()

```


a. Create a `LoudBike` subclass of Bike.  When you call `ringBell` it should ring the bell in all caps.

b. Give `LoudBike` a new method called `ringBell(times:)` that rings the bell a given number of times


## Question 5

```swift
class Shape {
    var name: String { return "This is a generic shape" }
    var area: Double { fatalError("Subclasses must override the area") }
    var perimeter: Double { fatalError("Subclasses must override the perimeter") }
}
```

a. Given the `Shape` object above, create a subclass `Square` with a property `sideLength` with a default value of 5.

b. Override the `area` and `perimeter` computed values so it returns the area/perimeter of the square as appropriate

c. Override the `name` property of `Square` so that it returns a String containing its name ("Square") and its area and perimeter

d. Create a class `Rectangle` that subclasses from `Shape`.  Give it a `width` property with a default value of 6 and a `height` property with a default value of 4

e. Override the `name` property of `Rectangle` so that it returns a String containing its name ("Rectangle") and its area and perimeter.

f. (BONUS) What happens when you run the code below?  Explain why.

```swift
var myShapes = [Shape]()

myShapes.append(Square())
myShapes.append(Rectangle())

for shape in myShapes {
    print("This is a \(shape.name) with an area of \(shape.area) and a perimeter of \(shape.perimeter)")
}
```

## Question 6

a. Given the Point object below, complete the `distance` method so that it returns the distance between a given point.

The equation for the distance formula can be found [here](https://www.mathsisfun.com/algebra/distance-2-points.html) and is give by:

```swift
let horizontalDistance = pointOneXValue - pointTwoXValue
let verticalDistance = pointOneYValue - pointTwoYValue
let distanceBetweenTwoPoints = sqrt(horizontalDistance * horizontalDistance + verticalDistance * verticalDistance)
```

`sqrt` is a method in Swift that gives the square root.  Make sure to have `import Foundation` or `import UIKit` to use this method.

```struct Point {
let x: Double
let y: Double
func distance(to point: Point) -> Double {
let horizontal = self.x - point.x
let vertical = self.y - point.y
return sqrt(horizontal * horizontal + vertical * vertical )
}
}

let pointOne = Point(x: 0, y: 0)
let pointTwo = Point(x: 10, y: 10)

print(pointOne.distance(to: pointTwo)) //Prints 14.142135623730951
 
```


b. Given the above Point object, and Circle object below, add a `contains` method that returns whether or not a given point is on the circle

```struct Circle {
let radius: Double
let center: Point
func contains (point: Point) -> Bool {
return center.distance(to: point) == radius
}
func getRandomPoint() -> Point {
let x: Double = Double.random(in: 0 - radius...radius)
let y = sqrt(radius * radius - x * x)
return Point(x: x, y: y)
}
}

let pointOne = Point(x: 0, y: 0)
let circleOne = Circle(radius: 5, center: pointOne)
let pointTwo = Point(x: 5, y: 0)
let pointThree = Point(x: 4, y: 0)
let pointFour = Point(x: sqrt(12.5), y: sqrt(12.5))
circleOne.contains(point: pointTwo) //true
circleOne.contains(point: pointThree) // false
circleOne.contains(point: pointFour) //true

```

c. Add another method to `Circle` that returns a random point on the circle

Hint: Given the radius of a circle and the x value of a point on the circle, the y value of the point is defined by:

```
√(r^2) - (x^2)
```

```swift
circleOne.contains(circleOne.getRandomPoint()) //Should always be true
```


## Question 7

a. Create a struct called HangmanModel with 3 properties `targetWord: String`, `numberOfIncorrectGuesses: Int` and `guessedLetters: [Character]`.

b. Add a method called `playerWon` that returns whether all of the characters in `targetWord` are in `guessedLetters`

```swift
var model = HangmanModel()
model.targetWord = "hello"
model.guessedLetters = ["h","e","o","l"]
model.playerWon //true
```

c. Add a method called `printDisplayVersionOfWord` that prints the `targetWord` replacing characters that are not in `guessedLetters` with "\_"

```
var model = HangmanModel()
model.targetWord = "hello"
model.guessedLetters = ["h","l"]
model.printDisplayVersionOfWord
//prints h_ll_
```

d. Add a method called `guess(_:)` that takes in a character as input, and updates `guessedLetters` and `numberOfIncorrectGuesses` as appropriate.

```swift
var model = HangmanModel()
model.targetWord = "hello"
model.guess("h")
model.guess("a")
model.guessedLetters // ["h", "a"]
model.numberOfIncorrectGuesses // 1
```

e. Have `guess(_:)` also print out the current display version of the word, the number of incorrect guesses and if the player has won.
