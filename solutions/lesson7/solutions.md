# Lesson 7 Solutions

[Previous Lesson](../lesson6/solutions.md)

<!-- TOC -->

- [Lesson 7 Solutions](#lesson-7-solutions)
    - [7.3 Preventing objects from mutating](#73-preventing-objects-from-mutating)
    - [7.6 Function composition](#76-function-composition)
    - [7.7 Functional array methods](#77-functional-array-methods)
    - [7.9 Destructuring](#79-destructuring)
    - [End of document](#end-of-document)

<!-- /TOC -->
<!-- Solutions below only -->

## 7.3 Preventing objects from mutating

[Back to top](#lesson-7-solutions)

* ***Combine two objects with Object.assign.***
```js
const obj1 = {
    name: 'object 1',
    type: 'object',
    value: 200,
    appearance: {
        size: 'large'
    }
}

const obj2 = {
    name: 'object 2',
    type: 'object', 
    appearance: {
        size: 'small',
        shape: 'cube'
    }
}

const newObj = Object.assign({}, obj1, obj2)

// RESULT of newObj, appearance takes obj1 then gets overwritten by obj2's properties
// appearance: Object { size: "small", shape: "cube" }
// name: "object 2"
// type: "object"
// value: 200

// obj1 does not change
// obj2 does not change
```

* ***Combine two objects with assignment.***

```js
const newObj = assignment({}, obj1, obj2)

newObj.appearance.shape = 'cone'

// obj2 remains the same
```

* ***Try to mutate your objects. Take note of any mutation you found.***

```js
newObj.appearance.shape = 'cone'

// obj2 gets mutated from cube to cone!
```

## 7.6 Function composition

[Back to top](#lesson-7-solutions)

```js
// simple pipe allows for combining 2 functions
function simplePipe (fn1, fn2) {
  return function (num) {
    return fn2(fn1(num))
  }
}
```

## 7.7 Functional array methods

[Back to top](#lesson-7-solutions)

```js
const people = [
  { firstName: 'Benjamin', lastName: 'Franklin', yearBorn: 1706, yearOfDeath: 1790 },
  { firstName: 'Thomas', lastName: 'Edison', yearBorn: 1847, yearOfDeath: 1931 },
  { firstName: 'Franklin', lastName: 'Roosevelt', yearBorn: 1882, yearOfDeath: 1945 },
  { firstName: 'Napolean', lastName: 'Bonaparte', yearBorn: 1830, yearOfDeath: 1821 },
  { firstName: 'Abraham', lastName: 'Lincoln', yearBorn: 1809, yearOfDeath: 1865 },
  { firstName: 'Mahatma', lastName: 'Gandhi', yearBorn: 1869, yearOfDeath: 1948 },
  { firstName: 'Winston', lastName: 'Churchill', yearBorn: 1874, yearOfDeath: 1965 },
  { firstName: 'Charles', lastName: 'Darwin', yearBorn: 1809, yearOfDeath: 1882 },
  { firstName: 'Albert', lastName: 'Einstein', yearBorn: 1879, yearOfDeath: 1955 },
  { firstName: 'Pablo', lastName: 'Picasso', yearBorn: 1881, yearOfDeath: 1973 },
  { firstName: 'Ludwig', lastName: 'Beethoven', yearBorn: 1770, yearOfDeath: 1827 },
  { firstName: 'Walt', lastName: 'Disney', yearBorn: 1901, yearOfDeath: 1966 },
  { firstName: 'Henry', lastName: 'Ford', yearBorn: 1863, yearOfDeath: 1947 },
  { firstName: 'Steve', lastName: 'Jobs', yearBorn: 1955, yearOfDeath: 2012 }
]
```

* ***Find the index of Thomas Edison.***

```js
const edisonIndex = people.findIndex( person => person.lastName === 'Edison')
// people[1] or index of 1
```

* ***Find the object that contains Winston Churchill.***

```js
const churchill = people.find(person => person.lastName === 'Churchill')
// gets churchill object 
// {
// firstName: "Winston",
// lastName: "Churchill",
// yearBorn: 1874,
// yearOfDeath: 1965,
// }
```

* ***Create an array that contains people that died before 1940.***

```js
const deadPeople = people.filter(person => person.yearOfDeath < 1940)
// an array of 6
```

* ***Create an array that contains people that are alive between 1850 and 1900.***

```js
const between1850n1900 = people.filter(person => person.yearOfDeath > 1850 && person.yearBorn < 1900)
// an array of 9
```

* ***Create an array that contains the firstName, lastName and yearsLived for each person (where yearsLived is the number of years the person lived).***

```js
const namesAndYears = people.map(person => ({
    firstName: person.firstName,
    lastName: person.lastName,
    yearsLived: person.yearOfDeath - person.yearBorn
    })
)
// We are creating a new object array for each person that consists of firstName, lastName, and a new property 
// yearsLived. So we have to define them in the javascript object to be created for each person and the
// syntax for creating a js object is { key: value }
// so we need to creat a new array of objects like this: 
// const objectArray = [
//     { key1: value1, key2: value2, key3: value3 }, <= object1
//     { key1: value1, key2: value2, key3: value3 }, <= object2
//     { key1: value1, key2: value2, key3: value3 } <= object3
// ]
```

* ***Get the total number of yearsLived of the people who were alive between 1750 and 1900.***

```js
// Get array of people objects alive in time window => 12
const between1750n1900 = people.filter(person => person.yearOfDeath > 1750 && person.yearBorn < 1900)

// Map the years alive for each person object
const yearsAlive = between1750n1900.map(person => person.yearOfDeath - person.yearBorn)

// Reduce the yearsAlive to a single number
const totalYrsLived = yearsAlive.reduce((acc, num) => acc + num, 0)

// 830, because at the time of this writing, Napoleon was alive -9 yrs

// BONUS: do it all at once by chaining and pass in the range:
const totalYearsLived = ((array, minYear, maxYear) => {
    return array.filter(person => person.yearOfDeath > minYear && person.yearBorn < maxYear )
    .map(person => person.yearOfDeath - person.yearBorn)
    .reduce((acc, num) => acc + num, 0)
})

// BONUS2: just a single reduce
const totalYearsLived2 = ((array, minYear, maxYear) => {
    return array.reduce((sum, item) => {
    let yearOfDeath = item.yearOfDeath
    let yearBorn = item.yearBorn
    (yearBorn < 1900 && yearOfDeath > 1750 )
        ? (sum + (yearOfDeath - yearBorn))
        : sum
    }), 0
})

// totalYearsLived(people, 1750, 1900) 
// returns 830
```

## 7.9 Destructuring

[Back to top](#Lesson-7-solutions)

```js
const posts = [
    {
    id: 800,
    title: 'This is 💩'
    }, 
    {
    id: 801,
    title: 'Pooing is a natural thing!'
    }, 
    {
    id: 802,
    title: 'This is getting irritating'
    }
]
```

_Perform these actions with the following set of data:_

* ***Get the first two items in posts with destructuring.***

```js
// Even though each post is an object, this is an array of objects, furthermore, you
// are attempting to get the entire object
const [firstItem, secontItem] = posts
console.log(firstItem) //{ id: 800, title: 'This is 💩'} 
console.log(secondItem) //{id: 801, title: 'Pooing is a natural thing!'}
```

* ***Get the id and title of the first post with destructuring.***

```js
const {id, title} = firstItem
console.log(id) //800
console.log(title) //This is 💩
```

* ***Rename the title of the first post to content while you destructure.***

```js
```

* ***Create a description variable and provide it with a default value Nothing is better than leaving the description empty.***


<!-- Solutions above only -->

## End of document

[Next Lesson](../lesson8/solutions.md)
