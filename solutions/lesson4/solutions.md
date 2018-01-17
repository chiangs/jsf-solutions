# Lesson 4 Solutions

[Previous Lesson](../lesson3/solutions.md)
<!-- TOC -->

- [Lesson 4 Solutions](#lesson-4-solutions)
    - [4.1 Events in JavaScript](#41-events-in-javascript)
    - [4.2 The listening element](#42-the-listening-element)
    - [4.3 Remove event listeners](#43-remove-event-listeners)
- [4.4 Default actions](#44-default-actions)
    - [End of document](#end-of-document)

<!-- /TOC -->
<!-- Solutions below only -->

## 4.1 Events in JavaScript

[Back to top](#lesson-4-solutions)

* **Write an click event listener. Log something into the console so you know the listener works.**

```js
// Select a button from the html document
const button = document.querySelector('button')

// Add the event listener, console will show 'clicked!' with count
// Count increments with each button press
button.addEventListener('click', function() {
    console.log('clicked!')
})

// Using arrow function
// just console.log(evt) will get you a ton of information
// evt.type gets you the type of event which in this case is 
// 'click' and not a predefined message like 'clicked!' but the 
// counter incrementing will still display
button.addEventListener('click', evt => console.log(evt.type))
//or
button.addEventListener('click', () => console.log('clicked'))
```

* **Add a class to the component when it is clicked. Remove a class from the component when it is clicked again.**

```html
<button>This is a button</button>
```

```js
// Select the button
const button = document.querySelector('button')

// Add the listener and toggle using a ternary expression
// ternary structure: condition ? true : false
button.addEventListener('click', function() {
    button.classList.contains('clicked') ? button.classList.remove('clicked') : button.classList.add('clicked')
})

// Using arrow function
button.addEventListener('click', () => 
    button.classList.contains('clicked') ? button.classList.remove('clicked') : button.classList.add('clicked'))
```

* **Add a custom attribute to the component when it is clicked. Remove the custom attribute when the component is clicked again.**

```js
// Using same html
// On click if there's no custom attribute, add it and set it to true
// Otherwise, remove it.
button.addEventListener('click', () => 
    !button.hasAttribute('data-custom') ? button.setAttribute('data-custom', true) : button.removeAttribute('data-custom'))
```

## 4.2 The listening element

[Back to top](#lesson-4-solutions)

* **Get the listening element with this.**

```js
// select button
const button = document.querySelector('button')

// event listener
button.addEventListener('click', function(){
    console.log(this)
})
```

* **Get the listening element with Event.currentTarget.**

```js
button.addEventListener('click', event => console.log(event.currentTarget))
```

* **Read the lesson on arrow functions. We'll use arrow functions from the next lesson onwards.**

```js
okey dokey artichokey
```

## 4.3 Remove event listeners

[Back to top](#lesson-4-solutions)

* **Add a click event listener.**

```js
// select the button
const button = document.querySelector('button')

// add event listener
const clickCallBack = () => console.log('clicked')
button.addEventListener('click', clickCallBack)
```

* **Remove the event listener you've added.**

```js
button.removeEventListener('click', clickCallBack)
```

* **Create an event listener that only listens for five clicks.**

```js
// select button
const button = document.querySelector('button')

// create counter variable
// set callback that increments button clicks and does something
let counter = 0

const clickCallBack = e => {
    counter ++
    console.log('clicked')
    if (counter > 4) {
        e.currentTarget.removeEventListener('click', clickCallBack)
    }
}

// add event listener
button.addEventListener('click', clickCallBack)
```

# 4.4 Default actions

[Back to top](#lesson-4-solutions)


<!-- Solutions above only -->

## End of document

[Next Lesson](../lesson5/solutions.md)
