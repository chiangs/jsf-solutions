# Lesson 2 Solutions

[Previous Lesson](../lesson1/solutions.md)

<!-- TOC -->

- [Lesson 2 Solutions](#lesson-2-solutions)
  - [2.7 Functions](#27-functions)
  - [2.8 Arrow Functions](#28-arrow-functions)
  - [2.9 Scopes & Closures](#29-scopes-closures)
  - [2.10 Intro to objects](#210-intro-to-objects)
  - [2.11 Arrays](#211-arrays)
  - [2.12 If/Else Statements](#212-ifelse-statements)
  - [2.13 &&, || and !](#213-and)
  - [2.15 For loops](#215-for-loops)
  - [2.16 Debugging errors](#216-debugging-errors)
  - [End of document](#end-of-document)

<!-- /TOC -->

<!-- Solutions below only -->

## 2.7 Functions

[Back to top](#lesson-2-solutions)

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

[Back to top](#lesson-2-solutions)

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

[Back to top](#lesson-2-solutions)

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

[Back to top](#lesson-2-solutions)

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
// Starting from an empty object
const myMac = {}

// Add various properties
myMac.make = 'Apple' 
myMac.model = 'MacBook Pro'
myMac.opSys = 'OS X'
myMac.year = 2017
myMac.screenSize = 15

// creates myMac object
myMac = {
  make: 'Apple',
  model: 'MacBook Pro',
  opSys: 'OS X',
  year: 2017,
  screenSize: 15
}
```

* **Make a property for your object with the bracket notation. Give it a value**

```js
// using the myMac obj
// create a property and set the value using bracket notation
myMac['hardDrive'] = '1TB'

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
// Printer method defined
myMac.printer = Object.keys(myMac).forEach(key => {
  console.log(myMac[key]);
});

// Calling the method
myMac.printer
```

* **Make a method that takes in an argument. Call this method**

```js
// Printer method defined that takes any obj
// runs through the obj to find it's key, value pairs to print
const printer = function (obj) {
 const keys = Object.keys(obj)
 keys.forEach(key => 
  console.log(‘Property=’ + key + ' Value=' + obj[key]))
}

// object property set to the method
myMac.print = printer

// object calls the method on itself as the argument
// but could take another obj instead
myMac.print(this)
```

## 2.11 Arrays

[Back to top](#lesson-2-solutions)

* **Make an empty array that contains nothing.**

```js
const myArray = []
```

**Make an array that contains three items.**

```js
const myNumberArray = [1, 2, 3]
const myStringArray = ['one', 'two', 'three']
const myMixedArray = [1, 'two', true]
const myArrayArrays = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

* **What is the index of Mahatma Gandhi in this list of people?**

```js
// print the index position of the people array where the value
// matches to the string of Mahatma Gandhi
console.log(people.indexOf('Mahatma Gandhi'))
// 6, because arrays start at 0
```

* **Get Pablo Picasso from the people array.**

```js
people[10]
// or
console.log(people[10])
```

* **Set Walt Disney to Disneyland.**

```js
// find the length of the people array
people.length // 15, which means the last item Steve Jobs is people[14]

// because Walt Disney is people[12]...
people[12] = 'Disneyland'

// to check print out the people array
people
// shows
0: "Benjamin Franklin"
1: "Thomas Edison"
2: "Franklin Roosevelt"
3: "Napolean Bonaparte"
4: "Abraham Lincoln"
5: "Mother Theresa"
6: "Mahatma Gandhi"
7: "Winston Churchill"
8: "Charles Darwin"
9: "Albert Einstein"
10: "Pablo Picasso"
11: "Ludwig Beethoven"
12: "Disneyland" // great success
13: "Henry Ford"
14: "Steve Jobs"
length: 15
```

* **Add your best friend's name to the end of the list**

```js
// We don't want to mutate the original array, only a copy of it
// So we create a new array and concat the new item with the people array
// and then add them into the new array
// Concat puts the new item to the end of the array
const newPeopleArray = people.concat('Beer')
// check
newPeopleArray
// shows
0: "Benjamin Franklin"
1: "Thomas Edison"
2: "Franklin Roosevelt"
3: "Napolean Bonaparte"
4: "Abraham Lincoln"
5: "Mother Theresa"
6: "Mahatma Gandhi"
7: "Winston Churchill"
8: "Charles Darwin"
9: "Albert Einstein"
10: "Pablo Picasso"
11: "Ludwig Beethoven"
12: "Disneyland"
13: "Henry Ford"
14: "Steve Jobs"
15: "Beer" // great success
length: 16
```

* **Add another friend's name to the start of the list**

```js
// To put the new item at the beginning -or- before the original array
// we have to conver the item(s) into an array before we concat
const originalArray = ['pong']
const prependItem = 'beer'
// convert it to an array
const prependArray = [prependItem]

const newCombinedArray = prependArray.concat(originalArray) // ['beer', 'pong']
```

* **Add your name after Winston Churchill in the list**

```js
// Winston Churchill's index of the people array is people[7]
// Last index of the original array is people[14]
// We need to divide the array into 2 parts and add my name in between
// Create an array with my name in it
const firstPart = people.slice(0, 8) // all names including Winston Churchill
const secondPart = people.slice(8) // all names after Winston Churchill
const namePart = ['Stephen']
const combinedArray = [].concat(firstPart, namePart, secondPart)

// or all in one step
const combinedArray = [].concat(
  people.slice(0, 8),
  ['Stephen'],
  people.slice(8)
)
```

* **Remove Benjamin Franklin from this list**

```js
// Benjamin Franklin is people[0]
// So we just slice the entire array except the 1st index and return it
const noBenjamins = people.slice(1)
```

* **Remove Steve Jobs from this list**

```js
//  Slice from the beginning for the entire length of the array minus the last index
const noJobs = people.slice(0, people.length - 1)
```

* **Remove Napolean Bonaparte from this list**

```js
// Napolean's position is people[3]
const firstPart = people.slice(0, 3) // all items before Napolean
const secondPart = people.slice(4) // all items after Napolean
const noNapolean = [].concat(firstPart, secondPart)

// or
const noNapolean = [].concat(people.slice(0, 3), people.slice(4))
```

## 2.12 If/Else Statements

[Back to top](#lesson-2-solutions)

```js
const someValue = 22
if (someValue) {
  // Executes if true
} else {
  // Executes if false
}
```

* **If someValue is false?**
  _No, the else statement executes_

* **If someValue is true?**
  _Yes_

* **If someValue is null?**
  _No, the else statement executes_

* **If someValue is undefined?**
  _No, the else statement executes_

* **If someValue is 0?**
  _No, the else statement executes_

* **If someValue is -1?**
  _Yes_

* **If someValue is ''?**
  _No, the else statement executes_

* **If someValue is 'has a value!'?**
  _Yes_

* **If someValue is {}?**
  _Yes_

* **If someValue is { isHavingFun: true }?**
  _Yes_

* **If someValue is []?**
  _Yes_

* **If someValue is ['one', 'two', 'three']?**
  _Yes_

## 2.13 &&, || and !

[Back to top](#lesson-2-solutions)

`All of the following can be entered into the console to check`

* **'Benjamin' && 'Thaddeus'**
  _'Thaddeus'_

* **'Benjamin' || 'Thaddeus'**
  _'Benjamin'_

* **'' && null**
  _''_

* **'' || null**
  _null_

* **2550284 && 0**
  _0_

* **2550284 || 0**
  _2550284_

* **!2550284**
  _false_

* **!true**
  _false_

* **!NaN**
  _true_

* **!{}**
  _false_

## 2.15 For loops

[Back to top](#lesson-2-solutions)

`const numbers = [1, 12, 4, 18, 9, 7, 11, 3, 50, 5, 6]`

* **Loop through the numbers and console.log each number within**

```js
// standard for loop
for (var i = 0; i < numbers.length; i++) {
  console.log(numbers[i])
}

// for...of
for (let number of numbers) {
  console.log(number)
}

// for each
numbers.forEach(function(number) {
  console.log(number)
})

// or using arrow function
numbers.forEach(number => console.log(number))
```

* **Loop through the numbers. If the numbers are greater than 5, console.log them.**

```js
for (let number of numbers) {
  if (number > 5) {
    console.log(number)
  }
}
```

* **Create a new array. Add all numbers that are greater than 10 into this new array.**

```js
// create new array
let newArray = []

// using push
for (let number of numbers) {
  if (number > 10) {
    newArray.push(number)
    // or
    newArray = newArray.concat(number)
  }
}
```

* **Create a new array. Multiply all numbers by 5 and put them into the new array.**

```js
let newArray = []

numbers.forEach(number => (newArray = newArray.concat(number * 5)))
```

## 2.16 Debugging errors

[Back to top](#lesson-2-solutions)

`Is there an error with the following code? If yes, find out what it is and fix it.`

```js
const anObject = {}
console.log(anObject.someMethod())
```

_The resulting error means `someMethod` doesn't exist aka is `undefined` thus it's not a `function` and thus can't be called as such, which is what we're attempting to do because of the `()` at the end of `someMethod()`._

_The solution is to define `someMethod` as a function using dot notation since we're working with an object._

```js
anObject.someMethod = function() {}
```

<!-- Solutions above only -->

## End of document

[Next Lesson](../lesson3/solutions.md)
