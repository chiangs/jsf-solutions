# Lesson 4 Solutions

[Previous Lesson](../lesson3/solutions.md)
<!-- TOC -->

- [Lesson 4 Solutions](#lesson-4-solutions)
    - [4.1 Events in JavaScript](#41-events-in-javascript)
    - [4.2 The listening element](#42-the-listening-element)
    - [4.3 Remove event listeners](#43-remove-event-listeners)
    - [4.4 Default actions](#44-default-actions)
    - [4.5 Event propogation](#45-event-propogation)
    - [4.6 Event delegation](#46-event-delegation)
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

// Create counter variable
// Set callback that increments button clicks and does something
// Note that the counter version of this solution only works 
// when you need it once
// Please see the next version where you set a custom attribute
// for a more reusable version
let counter = 0

const clickCallBack = e => {
    console.log('clicked')
    counter ++
    if (counter > 4) {
        e.currentTarget.removeEventListener('click', clickCallBack)
    }
}

// Setting a custom attribute version
const clickCallBack = e => {
    // log the click
    console.log('clicked')
    // assign to variables for easier use
    // parse the attribute from string to a number
    let element = e.currentTarget
    let clickCount = parseInt(element.getAttribute('data-click-count'))
    
    // if no data-click-count exists initially, clickCount will be NaN which is falsey
    // if it doesn't exit, set it to first click
    // if it exists then increment by 1
    !clickCount ? element.setAttribute('data-click-count', 1) : element.setAttribute('data-click-count', clickCount + 1)
    
    // check the current clickCount and if at threshold then remove listener
    // else just return the original element aka do nothing
    clickCount >= 4 ? element.removeEventListener('click', clickCallBack) : element
}

// add event listener
button.addEventListener('click', clickCallBack)

// final result is
click (5)
<button data-click-count="5">
```

## 4.4 Default actions

[Back to top](#lesson-4-solutions)

* **Try adding event.preventDefault to a link, a checkbox and a submit button. Watch what happens when you trigger the event after doing so. (Hint: Nothing should happen).**

_First, check the default operations happen, i.e., checkbox makes a check on click_

```html
<!-- link -->
<a href="https://github.com/chiangs" target="_blank">@Chiangs</a>

<!-- checkbox -->
<input type="checkbox">

<!-- button -->
<button type="submit">Button</button>
```

```js
// link
// select the link
const link = document.querySelector('a')

// add event listener with preventDefault
link.addEventListener('click', e => e.preventDefault()) // click does not open link

// checkbox
const checkbox = document.querySelector('input')
checkbox.addEventListener('click', e => e.preventDefault()) // click does not check

// button
const button = document.querySelector('button')
button.addEventListener('click', e => e.preventDefault()) // does not submit
```

Grouping elements into an array, e.g. the above three that should be 'preventDefault', helps structuring the code. It's then possible to apply the behaviour `preventDefault()` in a single step when adding the event listener by using forEach on the newly created array.

```js
// optionally, you can preventDefault on elements at the same time by grouping them 
// into an array and using forEach to add the event listener.
const elementsToPreventDefault = [link, checkBox, submit]

elementsToPreventDefault.forEach(element => {
  element.addEventListener('click', elem => elem.preventDefault())
})
```

## 4.5 Event propogation

[Back to top](#lesson-4-solutions)

* **Try adding an event listener in the capturing phase**

```js
// In the capturing phase, only listeners with useCapture set to true/false will fire. It is set as the optional boolean third argument.
Element.addEventListener('click', () => console.log('clicked'), true)
```

* **Try adding an event listener in the bubbling phase**

```js
// In bubbling phase, only listeners without useCapture set to true
// will fire
Element.addEventListener('click', () => console.log('clicked))
```

* **Which phase comes first? The capturing phase or the bubbling phase?**

_Capturing phase_

* **What event listeners are fired in the capturing phase?**

_Event listeners with useCapture flag set_

* **What event listeners are fired in the target phase?**

_All event listeners_

* **What event listeners are fired in the bubbling phase?**

_Only event listeners without the useCapture flag_

## 4.6 Event delegation

[Back to top](#lesson-4-solutions)

* **Here's a list of famous people. Create an event listener that uses the event delegation pattern. Log the li element of the person you've clicked into the console.**

```html
<ul>
  <li><a href="#">Benjamin Franklin</a></li>
  <li><a href="#">Thomas Edison</a></li>
  <li><a href="#">Franklin Roosevelt</a></li>
  <li><a href="#">Napolean Bonaparte</a></li>
  <li><a href="#">Abraham Lincoln</a></li>
</ul>
```

```js
// Select the list first
const ul = document.querySelector('ul')

// Add the event listener
// Search for the closest li, which is the parentElement of the a 
// tag. Because 'e' is the event object, you'll need the e.target 
// which is the actual element clicked on, then it's closest.
ul.addEventListener('click', e => {
    const li = e.target.closest('li')
    if (li) {
        console.log(li)
    }
})
```

<!-- Solutions above only -->

## End of document

[Next Lesson](../lesson5/solutions.md)
