# Lesson 5 Solutions

[Previous Lesson](../lesson4/solutions.md)
<!-- TOC -->

- [Lesson 5 Solutions](#lesson-5-solutions)
    - [5.2 Getting an element's position on screen](#52-getting-an-elements-position-on-screen)
    - [5.5 Off-canvas starter](#55-off-canvas-starter)
    - [5.6 Modal window starter](#56-modal-window-starter)
    - [5.7 Accordion starter](#57-accordion-starter)
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

## 5.5 Off-canvas starter

[Back to top](#lesson-5-solutions)

```js
// Select the button by the js class jsOffsiteToggle
const offsiteToggle = document.querySelector('.jsOffsiteToggle');

// Event Listener that adds class offsite-is-open to body
// Select the body's class list
// Define the toggle class
// if it contains offsite-is-open, then remove otherwise add (ternary expression)
offsiteToggle.addEventListener('click', () => {
  const bodyClassList = document.body.classList;
  const toggleClass = 'offsite-is-open';

  bodyClassList.contains(toggleClass)
    ? bodyClassList.remove(toggleClass)
    : bodyClassList.add(toggleClass);
});
```

## 5.6 Modal window starter

[Back to top](#lesson-5-solutions)

```js
// Add styling of modal, before open and after it is open
// opacity and z-index

// Assign the classList of the body to a variable
// Assign the toggle class string to a variable
// Add js classes to the modal container and the regular button and modal `x` button
// `Click Me! button` === jsModalToggle
// `Modal-Container` === jsModalContainer
// `x` button on the modal === jsModalClose
// Select the buttons, the modal container
// Add the x button and overlay to an array of modalClosers
const bodyClassList = document.body.classList;
const toggleClass = 'modal-is-open';

const modalToggler = document.querySelector('.jsModalToggle');
const modalCloseButton = document.querySelector('.jsModalClose');
const modalOverlay = document.querySelector('.jsModalContainer');
const modalClosers = [modalCloseButton, modalOverlay];

// Open & Close
// EL that adds class modal-is-open to body
modalToggler.addEventListener('click', () => {
  bodyClassList.add(toggleClass);
});

// EL that removes class modal-is-open from body
// Looks at the two method of closing; x button and clicking outside the modal
// in the container, applies an EL that removes the class to each of them with
// forEach
modalClosers.forEach(item => {
  item.addEventListener('click', () => bodyClassList.remove(toggleClass));
});
```

## 5.7 Accordion starter

[Back to top](#lesson-5-solutions)

<!-- Solutions above only -->

## End of document

[Next Lesson](../lesson6/solutions.md)
