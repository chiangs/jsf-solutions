# Lesson 8 Solutions

[Previous Lesson](../lesson7/solutions.md)

<!-- TOC -->

- [Lesson 8 Solutions](#lesson-8-solutions)
    - [8.1 Enhanced Object Literals](#81-enhanced-object-literals)
    - [8.2 Template literals](#82-template-literals)
    - [8.3 OOP](#83-oop)
    - [8.4 `This`](#84-this)
        - [Important to remember:](#important-to-remember)
    - [8.5 JavaScript classes](#85-javascript-classes)
    - [8.6 Inheritance](#86-inheritance)
    - [8.7 Prototypes](#87-prototypes)
    - [8.9 Objects instead of Constructors and Classes](#89-objects-instead-of-constructors-and-classes)
    - [8.10 Composition and Inheritance](#810-composition-and-inheritance)
    - [8.11 Private variables](#811-private-variables)
    - [End of document](#end-of-document)

<!-- /TOC -->
<!-- Solutions below only -->

## 8.1 Enhanced Object Literals

[Back to top](#lesson-8-solutions)

* ***Try creating a property with property value shorthands***

```js
// shorthand
const obj = {
    someProperty
}

// regular way
const obj _ {
    someProperty: someProperty
}
```

* ***Try creating a method with method shorthands***

```js
// shorthand
const obj = {
    doSomething() { console.log('Doing something') }
}

// regular way
const obj _ {
    doSomething: function() {console.log('Doing something)}
}
```

* ***Try adding two dynamic variables into Javascript with computed property names***

```js
const ham = 'ham'
const burger = 'burger'

const sandwich = {
    [ham]: 'bbq',
    [ham + burger]: 'angus'
}

// results in
Object {ham: 'ham', hamburger: 'angus'}
```

## 8.2 Template literals

[Back to top](#lesson-8-solutions)

* ***console.log a string that contains a variable with template literals***

```js
const partOne = `An apple a day...`
const partTwo = `keeps the doctor away`

console.log(`${partOne}${partTwo}`)
// An apple a day...keeps the doctor away
```

* ***console.log a string that spans multiple lines with template literals***

```js
const poem = `Roses are red,
Violets are blue,
I love Javascript,
don't you?`

console.log(`${poem}`)
// Roses are red,
// Violets are blue,
// I love Javascript,
// don't you?
```

## 8.3 OOP

* ***Create a constructor function***

```js
function Car(make, model, year, color) {
    this.make = make
    this.model = model
    this.year = year
    this.color = color
    this.drive = () =>
        console.log(`The ${color} ${make}, ${model}, from ${year} goes vroom!`)
}
```

* ***Create three instances that have different names and ages.***

```js
const niceCar = new Car('Ferrari', 'Italia', 2017, 'red')

const coolCar = new Car('BMW', 'M4', 2017, 'black')

const wowCar = new Car('Tesla', 'Model 1', 2018, 'white')
```

* ***Console.log each instance and notice the differences between them.***

```js
// niceCar
color: "red"
drive: function drive()
make: "Ferrari"
model: "Italia"
year: 2017
niceCar.drive() // The red Ferrari, Italia, from 2017 goes vroom!

// coolCar
color: "black"
drive: function drive()
make: "BMW"
model: "M4"
year: 2017
coolCar.drive() // The black BMW, M4, from 2017 goes vroom!

// wowCar
color: "white"
drive: function drive()
make: "Tesla"
model: "Model 1"
year: 2018
wowCar.drive() // The white Tesla, Model 1, from 2018 goes vroom! 
```

## 8.4 `This`

[Back to top](#lesson-8-solutions)

### Important to remember:
- `this` in ***constructor*** functions and directly in a ***method*** point to the **object** itself.
- `this` in a ***global context*** and in a ***simple function*** point to **Window**.
- `this` in an ***arrow function*** always takes up the value of this in its **surrounding scope**.
- `this` in an ***event listener*** points to the **listening** element.

```js
function sayMyName (firstName, lastName) {
  // 1. What's the value of this here?
  // `this` POINTS TO THE OBJECT ITSELF
  // this.firstName is sayMyName's firstName property
  // this.firstName = firstName to assign the value to the object's property
  console.log(`${firstName} ${lastName}`)
}

sayMyName()


const Crab = function (name) {
  // 5. What's the value of `this` here in the following two cases
  // same as above, this refers to the Crab object
  this.name = name
}

const crab1 = Crab('Sebastian') // Case 1 // this doesn't work without `new`
const crab2 = new Crab('Sebastian') // Case 2 // this assigns the name prop to the name value passed

const mermaid = {
  name: 'Ariel',
  hasScales: true,
  hasTail: true,

  sing (song) {
    this.currentSong = song
    console.log(song)
    // 3. What's the value of `this` here?
    // REFERS TO THE mermaid OBJECT, BECAUSE THIS IS A SIMPLY FUNCTION
    // mermaid.sing('lala')
    // console.log(mermaid.currentSong) gets the name of the song you passed in 'lala'

  },

  encore () {
    const song = this.previousSong
    setTimeout((song) => {
      // 4. What's the value of `this` here?
      // REFERS TO THE SURROUNDING SCOPE, so the song passed in
      // which refers to this.previousSong even though it's not defined in this example
      console.log(song)
    }, 1000);
  }
}
```

## 8.5 JavaScript classes

[Back to top](#lesson-8-solutions)

* ***Create a class with class.***

```js
class Pizza {
    constructor(size, veggieTopping, meatTopping) {
        this.size = size
        this.veggieTopping = veggieTopping
        this.meatTopping = meatTopping

        this.toString = () => console.log(`${size} pizza with ${veggieTopping}, ${meatTopping}`)
    }
}
```

* ***Create an instance of your class***

```js
const myPizza = new Pizza('large', 'pineapples', 'bacon')

myPizza.toString()

// large pizza with pineapples, bacon
```

## 8.6 Inheritance

[Back to top](#lesson-8-solutions)

* ***Create a child class that extends from a parent class.***

```js
// Parent class
class Player {
    constructor(firstName, lastName, score) {
    this.firstName = firstName
    this.lastName = lastName
    this.score = score
    this.showScore = () => console.log(`${firstName} ${lastName}'s score: ${score}`)
    }
}

// new instance of Player
const newPlayer = new Player('player', 'one', 0)
newPlayer.showScore() // player one's score: 0

// new type of Player
const cheater = new Player('cheater', 'never-dies', 0)
cheater.alwaysWins = (score) => console.log(`All I do is win-win-win. , score: ${score}`)

cheater.alwaysWins(99999999999999) // All I do is win-win-win. , score: 99999999999999
```

* ***Create a child constructor that extends from a parent constructor***

```js
// Child class
class Sniper extends Player {
    constructor(firstName, lastName, score) {
        super(firstName, lastName, score)

        this.lookThroughScope = () => console.log(`${firstName} ${lastName} looks through scope and shoots. New score: ${score}`)
    }
}
const newSniper = new Sniper('shooter', 'one', 20000)
newSniper
// firstName: "shooter"
// lastName: "one"
// lookThroughScope: function lookThroughScope()
// score: 20000
// showScore: function showScore()
newSniper.lookThroughScope()
// shooter one looks through scope and shoots. New score: 20000
newSniper.showScore()
// shooter one's score: 20000
```

## 8.7 Prototypes

[Back to top](#lesson-8-solutions)


* ***Create a new array. Look at what's in the [[Prototype]] chain.***

```js
const newArray = [1, 2, 3, 4]
Object.getPrototypeOf(newArray)

// concat: function concat()
// constructor: function Array()
// copyWithin: function copyWithin()
// entries: function entries()
// every: function every()
// fill: function fill()
// filter: function filter()
// find: function find()
// findIndex: function findIndex()
// forEach: function forEach()
// includes: function includes()
// indexOf: function indexOf()
// join: function join()
// keys: function keys()
// lastIndexOf: function lastIndexOf()
// length: 0
// map: function map()
// pop: function pop()
// push: function push()
// reduce: function reduce()
// reduceRight: function reduceRight()
// reverse: function reverse()
// shift: function shift()
// slice: function slice()
// some: function some()
// sort: function sort()
// splice: function splice()
// toLocaleString: function toLocaleString()
// toSource: function toSource()
// toString: function toString()
// unshift: function unshift()
// Symbol(Symbol.iterator): undefined
// Symbol(Symbol.unscopables): undefined
// __proto__: Object { … }
```

* ***Create a new object. Look at what's in the [[Prototype]] chain.***

```js
const newObj = {
    size: 23,
    shape: 'round',
    color: 'red'
}

Object.getPrototypeOf(newArray)
// __defineGetter__: function __defineGetter__()
// __defineSetter__: function __defineSetter__()
// __lookupGetter__: function __lookupGetter__()
// __lookupSetter__: function __lookupSetter__()
// constructor: function Object()
// hasOwnProperty: function hasOwnProperty()
// isPrototypeOf: function isPrototypeOf()
// propertyIsEnumerable: function propertyIsEnumerable()
// toLocaleString: function toLocaleString()
// toSource: function toSource()
// toString: function toString()
// valueOf: function valueOf()
```

* ***Create a method. Look at what's in the method's [[Prototype]] chain.***

```js
const method = () => console.log('A method')

Object.getPrototypeOf(method)
// ()
// apply: function apply()
// arguments: null
// bind: function bind()
// call: function call()
// caller: null
// constructor: function Function()
// length: 0
// name: ""
// toSource: function toSource()
// toString: function toString()
// Symbol(Symbol.hasInstance): undefined
// __proto__: Object { … }
```

* ***Create a method that lives in a [[Prototype]] with the class syntax. Look at what's in the instance's [[Prototype]] chain.***

```js
class Machine {
    constructor(name, material) {
        this.name = name
        this.matierial = material

        this.doSomething = () => console.log('Nuts and bolts')
    }
}

Object.getPrototypeOf(myMachine)
// {…}
// constructor: function Machine()
// __proto__: Object { … }
```

## 8.9 Objects instead of Constructors and Classes

[Back to top](#lesson-8-solutions)

* ***Create a constructing object***

```js
const Dog = {
    init (name, breed) {
        this.name = name
        this.breed = breed
    },
    speak() {
        console.log(`woof woof says ${this.name} the ${this.breed}`)
    }
}
```

* ***Create an instance with Object.create***

```js
const newDog = Object.create(Dog)
newDog.init('Pepper', 'Pitbull')
newDog.speak() // woof woof says Pepper the Pitbull
```

* ***Create a child object (like Developer) with Object.create***

```js
const YappyBreed = Object.create(Dog)
```

* ***Add properties and methods to your child object***

```js
YappyBreed.yappiness = 'Level 200'
YappyBreed.fetch = (item) => console.log(`Fetching the ${item}`)
```

* ***Create an instance of the child object.***

```js
YappyBreed.init = (name, breed) => {
  Dog.init(name, breed)
  this.size = 'Small'
}

const balto = Object.create(YappyBreed)
balto.init('Balto', 'Norbottenspits')
```

* ***console.log both parent and child instances. Pay attention to the [[Prototype]] chain.***

```js
console.log(newDog)
// {…}
// breed: "Pitbull"
// name: "Pepper"
// __proto__: {…}
// init: function init()
// speak: function speak()
// __proto__: Object { … }

console.log(balto)
// {}
// __proto__: {…}
// fetch: function fetch()
// init: function init()
// yappiness: "Level 200"
// __proto__: {…}
// breed: "Norbottenspits"
// init: function init()
// name: "Balto"
// speak: function speak()
// __proto__: Object { … }
```

## 8.10 Composition and Inheritance

[Back top top](#lesson-8-solutions)

* ***Create three skills—swim, fly and run.***

```js
const skills = {
  swim () {
    console.log('I can swim!')
  },
  fly() {
    console.log('I can fly!')
  },
  run() {
    console.log('I can run!')
  }
}
```

* ***Create a Bird object. Note that all birds have wings and feathers, but not all birds fly.***

```js
// Added default values for the fly, swim, run skills as an option, but could be left out of the Bird object.
const Bird = {
    init(name, noise) {
        this.name = name
        this.noise = noise
    },
    feathers: true,
    wings: true,
    fly() {
        console.log(`I can't fly`)
    },
    swim() {
        console.log(`I can't swim`)
    },
    run() {
        console.log(`I can't run`)
    },
    makeSound() {
        console.log(`I am a ${this.name}, and I go ${this.noise}`)
    }
}
```

* ***Create a Sparrow. A sparrow should be able to fly.***

```js
const Sparrow = Object.create(Bird)
Object.assign(Sparrow, { fly: skills.fly })
Sparrow.fly() // 'I can fly!'
```

* ***Create a Duck. A duck should be able to fly and swim.***

```js
const Duck = Object.create(Bird)
Object.assign(Duck, { fly: skills.fly, swim: skills.swim })
Duck.init('Duck', 'Quack quack!')
Duck.makeSound() // I am a Duck, and I go Quack quack!
Duck.fly() // I can fly!
Duck.swim() // I can swim!
Duck.run() // I can't run
```

* ***Create an Ostrich. An ostrich can run, but cannot fly or swim.***

```js
const Ostrich = Object.create(Bird)
Object.assign(Ostrich, { run: skills.run })
Ostrich.run() // I can run!
Ostrich.swim() // I can't swim
```

## 8.11 Private variables

[Back top top](#lesson-8-solutions)

* ***Create a private variable with the Object.create syntax.***

```js
```


* ***Create a privileged method with the Object.create syntax***

```js
```


* ***Do the same with a Class syntax***

```js
```


* ***Do the same with a Constructor syntax***

```js
```

<!-- Solutions above only -->

## End of document

[Next Lesson]()
