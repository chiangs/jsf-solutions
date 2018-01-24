# Lesson 5 Solutions

[Previous Lesson](../lesson4/solutions.md)
<!-- TOC -->

- [Lesson 5 Solutions](#lesson-5-solutions)
  - [5.2 Getting an element's position on screen](#52-getting-an-elements-position-on-screen)
  - [5.5 Off-canvas starter](#55-off-canvas-starter)
  - [5.6 Modal window starter](#56-modal-window-starter)
  - [5.7 Accordion starter](#57-accordion-starter)
  - [5.8 Tabs starter](#58-tabs-starter)
  - [5.9 Carousel starter](#59-carousel-starter)
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

```js
// Add the css for the button and content on the is-open class
// Using the event delegation method where an event listener
// is placed on the accordion-container and open and closes
// the portion of the accordion that matches the item (accordionHeader) passed
// to the listener.

// Add the js classes to the container and headers
// accordion-container === jsAccordionContainer
// accordion-header === jsAccordionHeader

// select the container
const accordion = document.querySelector('.jsAccordionContainer');

// add the event listener
// select the header by getting the next parent up that has the right class from
// whatever was clicked.
// If it matches as a header, toggle the is-open class on the parent, which is the accordion-container
accordion.addEventListener('click', e => {
  const accordionHeader = e.target.closest('.jsAccordionHeader');
  if (accordionHeader) {
    accordionHeader.parentNode.classList.toggle('is-open');
  }
});
```

[Back to top](#lesson-5-solutions)

## 5.8 Tabs starter

[Back to top](#lesson-5-solutions)

## 5.9 Carousel starter

[Back to top](#lesson-5-solutions)

***This version is a slightly more advanced version than what the starter exercise calls for***

Instead of deactivating the buttons once you reach the end of the carousel, it allows for an infinite scroll. Additionally, many of the common functions shared between the event listeners were refactored into their own functions that could be called by the event listener, rather than being defined in the event listener each time.

```js
// Declare common variables you'll need for event listeners
// Select the track, buttons, dots, slides
// Convert slides and dots into arrays to assist you in selecting them individually later
// Get the width of one slide stored for later use
// Set the is-selected class to a variable as you'll need it many times
const track = document.querySelector('.jsTrack');
const nextButton = document.querySelector('.jsNextButton');
const prevButton = document.querySelector('.jsPrevButton');
const dotsContainer = document.querySelector('.jsDotContainer');
const slides = Array.from(track.children);
const dots = Array.from(dotsContainer.children);
const rect = slides[0].getBoundingClientRect();
const slideWidth = rect.width;
const isSelectedClass = 'is-selected';

// apply the left style to all slides in the slides array, this allows for
// the slides array to grow (increase in number of slides) without having to
// update this function
slides.forEach(
	(slide, index) => (slide.style.left = slideWidth * index + 'px')
);

// repeated or common functions in event listeners
// get all elements passed in elementArray that contain the class name
const getCurrent = (elementArray, className) =>
	elementArray.find(element => element.classList.contains(className));

// remove or add the class from the classList of the slide and dot element passed in
const changeClass = (slide, dot, action, className) => {
	if (action === 'remove') {
		[slide, dot].forEach(element => element.classList.remove(className));
	}
	if (action === 'add') {
		[slide, dot].forEach(element => element.classList.add(className));
	}
};

// add the class name to the classList of the first or last child of the parentElement of the slide and dot passed in
const addClassToChild = (slide, dot, child, className) => {
	if (child === 'first') {
		[slide, dot].forEach(element =>
			element.parentElement.firstElementChild.classList.add(className)
		);
	}
	if (child === 'last') {
		[slide, dot].forEach(element =>
			element.parentElement.lastElementChild.classList.add(className)
		);
	}
};

// amount to slide by getting the track and setting the left style to the amount passed in
const slide = (track, amount) => (track.style.left = '-' + amount);

// nextButton event listener
// select the current slide and dot
// remove the is-selected class
// if there is no next sibling, then it is the last slide so it must go back to the first slide
// and add the is-selected class to that slide
// otherwise slide one over and add the is-selected class to that slide.
nextButton.addEventListener('click', e => {
	let currentSlide = getCurrent(slides, isSelectedClass);
	let currentDot = getCurrent(dots, isSelectedClass);
	changeClass(currentSlide, currentDot, 'remove', isSelectedClass);

	!currentSlide.nextElementSibling
		? (addClassToChild(currentSlide, currentDot, 'first', isSelectedClass),
			(track.style.left = slides[0].style.left))
		: ((nextSlide = currentSlide.nextElementSibling),
			(nextDot = currentDot.nextElementSibling),
			changeClass(nextSlide, nextDot, 'add', isSelectedClass),
			(amountToMove = nextSlide.style.left),
			slide(track, amountToMove));
});

// previousButton event listener
// same as nextButton but in opposite direction
// style.left is a string so it must be parsted into an in and made negative then
// concatenated back into a string with 'px'
// using slides[slides.length - 1] will always get the last slide and allows for
// the number of slides to grow without having to change this logic.
prevButton.addEventListener('click', e => {
	let currentSlide = getCurrent(slides, isSelectedClass);
	let currentDot = getCurrent(dots, isSelectedClass);
	changeClass(currentSlide, currentDot, 'remove', isSelectedClass);

	!currentSlide.previousElementSibling
		? (addClassToChild(currentSlide, currentDot, 'last', isSelectedClass),
			(track.style.left =
				-1 * parseInt(slides[slides.length - 1].style.left) + 'px'))
		: ((prevSlide = currentSlide.previousElementSibling),
			(prevDot = currentDot.previousElementSibling),
			changeClass(prevSlide, prevDot, 'add', isSelectedClass),
			(amountToMove = prevSlide.style.left),
			slide(track, amountToMove));
});

// dotButton event listener
// get the current slide and dot, then remove the is-selected class
// find the index of the clicked dot from the dot array and use that index
// to match the slide at the same index of the slides array
// then set the slide amount to that selected slide and update it with the
// is-selected class
dotsContainer.addEventListener('click', e => {
	if (e.target.matches('button')) {
		const clickedDot = e.target;
		let currentSlide = getCurrent(slides, isSelectedClass);
		let currentDot = getCurrent(dots, isSelectedClass);
		changeClass(currentSlide, currentDot, 'remove', isSelectedClass);

		let index = dots.indexOf(clickedDot);
		const targetSlide = slides[index];
		const amountToMove = targetSlide.style.left;
		slide(track, amountToMove);
		changeClass(targetSlide, clickedDot, 'add', isSelectedClass);
	}
});

```


<!-- Solutions above only -->

## End of document

[Next Lesson](../lesson6/solutions.md)
