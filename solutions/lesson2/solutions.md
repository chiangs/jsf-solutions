# Lesson 2 Solutions

[Previous Lesson](../lesson1/solutions.md)

<!-- TOC -->

- [Lesson 2 Solutions](#lesson-2-solutions)
    - [2.7 Functions](#27-functions)
    - [2.8 Arrow Functions](#28-arrow-functions)
    - [2.9 Scopes & Closures](#29-scopes-closures)
    - [2.10 Intro to objects](#210-intro-to-objects)
    - [End of document](#end-of-document)

<!-- /TOC -->

<!-- Solutions below only -->

## 2.7 Functions

* **Make a function named logger that console.log the argument you passed into it.**

```js
function logger(argument) {
  console.log(argument)
}
```

* **Make a function called add that adds two numbers together.**

```js
function add(num1, num2) {
  return num1 + num2
}
```

* **Make a function called multiply that multiplies two numbers together.**

```js
function multiply(num1, num2) {
  return num1 * num2
}
```

## 2.8 Arrow Functions

* **Make a function named ten that takes in zero arguments and return the value 10. Try using both () and \_ syntax.**

```js
const ten = () => 10
// or
const ten = _ => 10

// to check
ten() // returns 10
```

* **Make a function named logger that takes in one argument. It logs the argument you passed into it. Try it with and without parenthesis ().**

```js
// with ()
const logger = (argument) => console.log(argument)
// without ()
const logger = argument => console.log(argument)

// to check
logger(type a string, boolean, number) // returns your argument
```

* **Make a function called add that adds two numbers together. Try it with and without implicit returns**

```js
// Without implicit returns
function add(num1, num2) {
  return num1 + num2
}
// Implicit returns
const add = (num1, num2) => num1 + num2
```

* **Make a function called multiply that multiplies two numbers together. Try it with and without implicit returns**

```js
// Without implicit returns
function multiply(num1, num2) {
  return num1 * num2
}
// With implicit returns
const multiply = (num1, num2) => num1 * num2
```

**Bonus custom function**

```js
// a function with implicit returns that tests if a number entered as
// an argument is odd uses the modulus and ternary expression to test
// and return boolean of true or false
const isOdd = num1 => (num1 % 2 === 1 || num1 % 2 === -1 ? true : false)

isOdd(1) // true
isOdd(4) // false
```

## 2.9 Scopes & Closures

* **What is a block scope?**

_Variables declared with const or let in curly braces ({}) are considered to be in a block scope. The curly brace begins and ends the block._

```js
{
  // this is a code block; everything between the
  // curly braces are in the block's scope.
}
```

* **What is a function scope?**

_If a variable is declared in a function, the variable can only be used in the function. These variables are said to be in a function scope._

```js
function func() {
  var funcVar = 100
  return funcVar
}

// outside function
console.log(funcVar) // causes error because funcVar is not defined outside the function
```

* **Can you use global variables in a function scope?**

_Yes_

* **Can you use a local variable in the global scope?**

_No_

* **What is a closure?**

_When you create an innerFn in an outerFn, you have created a closure. The innerFn is the closure._

```js
function outerFn() {
  // innerFn is a closure
  return function innerFn() {}
}
```

_When we work with closures, we usually return the innerFn, so we can use its variables at a later time._

* **Create a global variable.**

```js
var globalVar = someValue
```

* **Create a local variable in a block scope.**

```js
// some code block such as a for loop
{
  var localVar = someValue
}
```

* **Create a local variable in a function scope.**

```js
function someFunc(argument) {
  var localVar = someValue // local variable in function that will always be the same
  return argument + someValue
}
```

* **Create a closure.**

```js
function outerFn() {
  // the closure
  return function innerFn() {
    // the inner function
    console.log('something')
  }
}
```

* **Get the value of a closure after the outerFn is called**

```js
// using the example closure from above
const theClosure = outerFn() // assign the closure a reference 'theClosure()' to call later

theClosure() // calls the closure which refers to outerFn()
```

## 2.10 Intro to objects

* **Make an empty object**

```js
const anObject = {
  key1: 'value1',
  key2: 'value2'
  // key can be named anything and value could be any value type
  // i.e., string, number etc.
}
```

* **Make a property for your object with the dot notation. Give it a value**

```js
const myMac = {
  make: 'Apple',
  model: 'Macbook Pro',
  year: 2017,
  trim: 'touchbar',
  screenSize: 15
}

const screenSize = myMac.screenSize // using dot notation to set a reference to a particular object property

console.log(screenSize) // prints out 15
```

* **Make a property for your object with the bracket notation. Give it a value**

```js
// my object
const myMac = {
  make: 'Apple',
  model: 'Macbook Pro',
  year: 2017,
  trim: 'touchbar',
  screenSize: 15
  // below creates hardDrive: '1TB'
}

// create a property and set the value using bracket notation
myMac[hardDrive] = '1TB'

// using dot notation(preferred)
myMac.hardDrive = '1TB'
```

* **Get the value of a property with the dot notation**

```js
// using myMac object above

console.log(myMac.screenSize) // 15
```

* **Get the value of a property with the square brack notation**

```js
const thePropertyWanted = 'model' // this could be set by the user in a function

console.log(myMac[thePropertyWanted]) // MacBook Pro
```

* **Set the value of a property with the dot notation**

```js
const theValueToSet = 'Asus'

myMac.model = theValueToSet // Changes 'MacBook Pro' to 'Asus'
```

* **Set the value of a property with the square bracket notation**

```js
const theValueToSet = 'Asus'

myMac['model'] = theValueToSet
```

* **Make a method. Call this method**

```js
const myObject = {
  size: 20,
  shape: 'sphere',
  weight: 25,
  color: 'red'
}

const objectColor = myObject.color

console.log(objectColor) // red
```

* **Make a method that takes in an argument. Call this method**

```js
// using the same object above myObject
// implicit return the objects property set by the argument
const objectMethod = argument => myObject[argument]

console.log(objectMethod('color')) // red
```

<!-- Solutions above only -->

## End of document

[Next Lesson](../lesson3/solutions.md)
