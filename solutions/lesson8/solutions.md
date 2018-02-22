# Lesson 8 Solutions

[Previous Lesson](../lesson7/solutions.md)

<!-- TOC -->

- [Lesson 8 Solutions](#lesson-8-solutions)
    - [8.1 Enhanced Object Literals](#81-enhanced-object-literals)
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

<!-- Solutions above only -->

## End of document

[Next Lesson]()
