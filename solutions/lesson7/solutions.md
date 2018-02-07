# Lesson 7 Solutions

[Previous Lesson](../lesson6/solutions.md)

<!-- TOC -->

- [Lesson 7 Solutions](#lesson-7-solutions)
    - [7.3 Preventing objects from mutating](#73-preventing-objects-from-mutating)
    - [7.6 Function composition](#76-function-composition)
    - [7.7 Functional array methods](#77-functional-array-methods)
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
const between1850n1900 = people.filter(person => person.yearOfDeath > 1850 && person.yearOfDeath < 1900)
// an array of 2
```

* ***Create an array that contains the firstName, lastName and yearsLived for each person (where yearsLived is the number of years the person lived).***

```js
```

* ***Get the total number of yearsLived of the people who were alive between 1750 and 1900.***

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

<!-- Solutions above only -->

## End of document

[Next Lesson](../lesson8/solutions.md)
