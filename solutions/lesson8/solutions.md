# Lesson 8 Solutions

[Previous Lesson](../lesson7/solutions.md)

<!-- TOC -->

- [Lesson 8 Solutions](#lesson-8-solutions)
    - [8.1 Enhanced Object Literals](#81-enhanced-object-literals)
    - [8.2 Template literals](#82-template-literals)
    - [8.3 OOP](#83-oop)
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

<!-- Solutions above only -->

## End of document

[Next Lesson]()
