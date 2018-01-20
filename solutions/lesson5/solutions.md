# Lesson 5 Solutions

[Previous Lesson](../lesson4/solutions.md)
<!-- TOC -->

- [Lesson 5 Solutions](#lesson-5-solutions)
    - [5.2 Getting an element's position on screen](#52-getting-an-elements-position-on-screen)
    - [End of document](#end-of-document)

<!-- /TOC -->
<!-- Solutions below only -->

## 5.2 Getting an element's position on screen

* **Using `getBoundingClientRect`**

_on [Google's website](https://google.com)_

```js
// Inspect Google's site and select the logo
// You'll see that the element has an id of `#hplogo`
const logo = document.querySelector('#hplogo')

const domRect = logo.getBoundingRect()

console.log(domRect) 
// returns
// bottom: 290
// height: 201
// left: 359
// right: 631
// top: 89
// width: 272
// x: 359
// y: 89
```

[Back to top](#lesson-5-solutions)


<!-- Solutions above only -->

## End of document

[Next Lesson](../lesson6/solutions.md)
