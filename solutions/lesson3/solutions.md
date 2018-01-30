# Lesson 3 Solutions

[Previous Lesson](../lesson2/solutions.md)

<!-- TOC -->

- [Lesson 3 Solutions](#lesson-3-solutions)
  - [3.2 Selecting an element](#32-selecting-an-element)
  - [3.3 Changing style](#33-changing-style)
  - [3.4 Array.forEach](#34-arrayforeach)
  - [3.5 Selecting multiple elements](#35-selecting-multiple-elements)
  - [3.7 Changing classes](#37-changing-classes)
  - [3.8 Changing Attributes / Exercise](#38-changing-attributes-exercise)
  - [3.9 DOM traversals](#39-dom-traversals)
  - [End of document](#end-of-document)

<!-- /TOC -->

<!-- Solutions below only -->

## 3.2 Selecting an element

[Back to top](#lesson-3-solutions)

```html
<div id="star-wars">
  <div class="character" data-type="hero">Luke Skywalker</div>
  <div class="character" data-type="master">Yoda</div>
  <div class="character" data-type="villain">Darth Vader</div>
</div>
```

* **The entire star-wars element**
  _by id:_

```js
const starWarsElement = document.querySelector('#star-wars')
```

* **The Luke Skywalker element**
  _by tag:_

```js
// building off of the first selector and knowing that
// querySelector matches the first character class element
const lukeElement = starWarsElement.querySelector('div')
```

_by class:_

```js
const lukeElement = starWarsElement.querySelect('.character')
```

* **The Yoda element**
  _by attribute:_

```js
const yodaElement = starWarsElement.querySelector('[data-type="master"]')
```

* **The Darth Vader element**
  _by attribute:_

```js
const darthElement = starWarsElement.querySelect('[data-type="villain"]')
```

## 3.3 Changing style

[Back to top](#lesson-3-solutions)

* **Familiarize yourself with getting and setting values of various CSS properties. You can use any property you can think of. Here's a few to start with:**

* **Try using these two methods to get and set your styles:**

1. `Element.style`
2. `window.getComputedStyle`

_Using `Panda Cub` sample code._

1. color

```js
// get the element
const pandaCub = document.querySelector('div')

// set the color inline style
const color = (pandaCub.style.color = 'green')

// get the inline styles
const inlineStyles = window.getComputedStyle(pandaCub, null)
inlineStyles.color
```

2. backgroundColor

```js
// set
const backgroundColor = (pandaCub.style.backgroundColor = 'red') // or rgb(255,0,0)

// get the styles
const inlineStyles = window.getComputedStyle(pandaCub, null) // returns all style
inlineStyles.backgroundColor // rgb(255,0,0)
```

3. fontSize

```js
// set
const fontSize = (pandaCub.style.fontSize = '20px')

// get from inlineStyles
inlineStyles.fontSize // 20px
```

4. fontWeight

```js
const fontWeight = (pandaCub.style.fontWeight = 'bold')

// get from inlineStyles
inlineStyles.fontWeight // bold or 700
```

## 3.4 Array.forEach

[Back to top](#lesson-3-solutions)

* **console.log the first name of each person in the array.**

```js
// People is an array of objects, or persons
// Call the forEach method on the people array
// for each item in the arry, that is now named person,
// print first name of the person
people.forEach(person => console.log(person.firstName))
```

* **Make a second array that contains only the first name of each person.**

```js
// For each person, copy the firstName property of the object into a new array
// To do this, we need to copy the firstname and move up an index in the new array 
// for the next person. Since we are copying from an array (people) we just use 
// that original person's index using indexOf as a reference. 
let newArray = []
people.forEach(person => firstNamnewArrayes[people.indexOf(person)] = person.firstName)

// alternatively using concat
let peopleFirstName = []
people.forEach(person => peopleFirstName = peopleFirstName.concat(person.firstName))

// alternatively just use the newArray's increasing length from each
// iteration of adding a person
people.forEach(person => newArray[newArray.length] = person.firstName)
```

* **Make a third array that contains people that have died after 1950.**

```js
// For each person, check the yearOfDeath property
// if > 1950 then copy the person object to the new array
// to do this, create a new array, after1950
// we can use the new array's length to increment the position as
// you add a new person and the new array's length grows.
let after1950 = []
people.forEach(person => {
  if (person.yearOfDeath > 1950) {
    after1950[after1950.length] = person
  }
}) // 6 person objects

// alternatively using filter method
const after1950 = people.filter(person => person.yearOfDeath > 1950)

// alternatively using concat which requires to be reassigned to the 
// variable because concat returns a new array
let after1950 = []
people.forEach(person => {
  if (person.yearOfDeath > 1950) {
    after1950 = after1950.concat(person)
  }
}) 
```

* **Find index of Charles Darwin in the array.**

```js
// Using forEach which takes 3 args (current value, index, array)
// in this case, we say that each item is an object named person.
// if the object at each index position of the people array has a lastName
// property that is the last name we are looking for, then print the index
people.forEach((person, index) => {
  if (people[index].lastName === 'Darwin')
  console.log(index)
}) // 8

// Use findIndex and match on last name
people.findIndex(person => person.lastName === 'Darwin')
// 8
```

## 3.5 Selecting multiple elements

[Back to top](#lesson-3-solutions)

```html
<div id="star-wars">
  <div class="character" data-type="hero">Luke Skywalker</div>
  <div class="character" data-type="master">Yoda</div>
  <div class="character" data-type="villain">Darth Vader</div>
</div>
```

_Try the following while using querySelectorAll:_

* **Change fontSize of all characters to 2em**

```js
const container = document.querySelector('#star-wars')
const characters = container.querySelectorAll('.character')
characters.forEach(element => element.style.fontSize = '2em')
```

* **Change Luke's text to white and backgroundColor to black**

```js
const luke = document.querySelectorAll('[data-type="hero"]')
luke.forEach(element => {
  element.style.color = 'white'
  element.style.backgroundColor = 'black'
})
```

* **Change Yoda's text to green.**

```js
const yoda = document.querySelectorAll('[data-type="master"]')
yoda.forEach(element => element.style.color = 'green')
```

* **Change Darth Vader's text to red.**

```js
const vader = document.querySelectorAll('[data-type="villain"]')
vader.forEach(element => element.style.color = 'red')
```

## 3.7 Changing classes

[Back to top](#lesson-3-solutions)

```html
<ul class="superheroes">
  <li>Wonderwoman</li>
  <li>Superman</li>
  <li>Ironman</li>
  <li>Batman</li>
  <li>The Flash</li>
  <li></li>
</ul>
```

_Try adding a class of superhero to each hero in following HTML with querySelectorAll, forEach and classList.add._

```js
// select the container not required, but useful to be specific
const container = document.querySelector('.superheroes')

// select all superheroes
const superheroes = container.querySelectorAll('li')

// add class using forEach, but only if that hero is named
// so the last <li></li> won't get the class
superheroes.forEach(hero => {
  if (hero.innerText != '') {
    hero.classList.add('superhero')
  }
})
```

## 3.8 Changing Attributes / Exercise

[Back to top](#lesson-3-solutions)

* HTML

```html
<div class="clown-hat" data-color="red" data-num-stripes="3">A Clown hat</div>
```

* Set an attribute with Element.setAttribute

```js
const getClown = document.querySelector('.clown-hat')
getClown.setAttribute('data-awesomeness', true)
```

* Get an attribute with Element.getAttribute

```js
const getAwesome = getClown.getAttribute('data-awesomeness')
console.log((title = 'data-awesomeness:'), getAwesome)
```

* Get an attribute with Element.dataset

```js
const getNumStripes = getClown.dataset.numStripes
console.log((title = 'data-num-stripes:'), getNumStripes)
```

* Set an attribute with Element.dataset

```js
getClown.dataset.hatSize = 'huge'
```

* Remove attribute with Element.removeAttribute

```js
getClown.removeAttribute('data-awesomeness')
```

## 3.9 DOM traversals

[Back to top](#lesson-3-solutions)

```html
<div class="characters">
  <ul class="hobbits">
    <li>Frodo Baggins</li>
    <li>Samwise "Sam" Gamgee</li>
    <li>Meriadoc "Merry" Brandybuck</li>
    <li>Peregrin "Pippin" Took</li>
    <li>Bilbo Baggins</li>
  </ul>
  <ul class="humans">
    <li>Gandalf</li>
    <li>Saruman</li>
    <li>Aragorn</li>
    <li>Boromir</li>
    <li>Faramir</li>
  </ul>
  <ul class="elves">
    <li>Legolas</li>
    <li>Glorfindel</li>
    <li>Elrond</li>
    <li>Arwen Evenstar</li>
  </ul>
  <ul class="enemies">
    <li>Sauron</li>
    <li>Nazgûl</li>
  </ul>
</div>
```

* **Select .characters with document.querySelector**
```js
// select the list's container
const characters = document.querySelector('.characters')
```

* **Select .humans from .characters**
```js
// select the humans list from the container
const humans = characters.querySelector('.humans')
```

* **Select all humans with querySelectorAll, starting from .humans**
```js
// from the humans list select all of it's list items
humans.querySelectorAll('li')
```

* **Select all hobbits with children**
```js
// select the hobbits list
const hobbits = characters.querySelector('.hobbits')
const hobbitItems = hobbits.children
```

* **Select the Merry (the hobbit)**
```js
const merry = hobbits.children[2]
```

* **Select .enemies from Sauron**
```js
// select all character by li tag
const characters = document.querySelectorAll('li')

// select Sauron
const sauron = characters[14]

// select the parentElement
const enemies = sauron.parentElement 

// select by closest tag
const enemies = sauron.closest('ul')

// select by closest class
const enemies = sauron.closest('.enemies')
```

* **Select the .characters div from Nazgûl**
```js
const characters = document.querySelectorAll('li')

const nazgul = characters[15]

const charactersDiv = nazgul.closest('.characters')
```

* **Select Elrond from Glorfindel**
```js
const characters = document.querySelectorAll('li')

const glorfindel = characters[11]

const elrond = glorfindel.nextElementSibling
```

* **Select Legolas from Glorfindel**
```js
const characters = document.querySelectorAll('li')

const glorfindel = characters[11]

const legolas = glorfindel.previousElementSibling
```

* **Select Arwen from Glorfindel**
```js
const characters = document.querySelectorAll('li')

const glorfindel = characters[11]

const arwen = glorfindel.parentElement.children[3]
```

<!-- Solutions above only -->

## End of document

[Next Lesson](../lesson4/solutions.md)
