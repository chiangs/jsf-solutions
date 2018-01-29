# Lesson 6 Solutions

[Previous Lesson](../lesson5/solutions.md)

<!-- TOC -->

- [Lesson 6 Solutions](#lesson-6-solutions)
	- [6.1 CSS Transitions](#61-css-transitions)
	- [6.2 CSS Animations](#62-css-animations)
	- [End of document](#end-of-document)

<!-- /TOC -->

<!-- Solutions below only -->

## 6.1 CSS Transitions

[Back to top](#lesson-6-solutions)

* ***Change the opacity property of an element from 0.5 to 1 over 1.5 seconds when you hover on it.***
```html
<h1 class="opacityChange">Hover to change my opacity!</h1>
```
```css
// class before change
.opacityChange {
	color: #fff;
	background-color: #0091ea;
	opacity: 0.5;
}

// class change after hover
.opacityChange:hover {
	opacity: 1;
	transition-duration: 1.5s;
}
```
* ***Rotate an element from 0deg to 180deg when you add the is-rotated class to it. (Hint: you can transition the transform property).***
```html
<div class="rotateChange">Add 'is-rotated' class to rotate me!</div>
```
```css
.rotateChange {
    background-color: #ffab00;
}
.is-rotated {
	transform: rotate(180deg);
	transition-duration: 1.5s;
}
```
```js
const isRotated = document.querySelector('.rotateChange')
isRotated.addEventListener('click', e => e.target.classList.add('is-rotated'))
```

* ***Experiment with ease, ease-in, ease-out timing functions.***

_similar to Zell's codepen example_
```html
 <section>
    <button class="goEase">Click Here!</button>
</section>
<div class="easeDivs">
    <div class="easeButtons easeIn">ease-in</div>
    <div class="easeButtons easeOut">ease-out</div>
    <div class="easeButtons easeInOut">ease-in-out</div>
</div>
```
```css
.goEase {
	border: 1px solid black;
	color: #fff;
	background-color: #0091ea;
	font-weight: bold;
	height: 50px;
	width: 100px;
}

.easeButtons {
	border: 1px solid #d500f9;
	font-weight: bold;
	height: 50px;
	width: 100px;
	transform: translateX(0);
	transition: transform 2s linear;
}

.go {
	transform: translateX(500px);
}

.easeIn {
	transition-timing-function: ease-in;
}

.easeOut {
	transition-timing-function: ease-out;
}

.easeInOut {
	transition-timing-function: ease-in-out;
}
```
```js
const goButton = document.querySelector('.goEase');
const easeList = document.querySelector('.easeDivs');
let easers = Array.from(easeList.children);
goButton.addEventListener('click', () =>
    easers.forEach(element => element.classList.add('go')));
```

* ***Create your own timing function with Cubic bezier.***

_this is a custom ease-in-out_
```html
<section>
    <p>Custom cubic-bezier</p>
    <button class="goButton">Click Here!</button>
    <div class="box easeInOut cubicBezier" id="box"></div>
</section>
```
```css
.box {
	border: 1px solid black;
	background-color: #0091ea;
	color: #fff;
	font-weight: bold;
	height: 50px;
	width: 50px;
	transform: translateX(0);
	transition: transform 2s;
}

.go {
	transform: translateX(500px);
}

.easeInOut {
	transition-timing-function: ease-in-out;
}

.cubicBezier {
	transition-timing-function: cubic-bezier(0.74, -0.81, 0.62, 1.61);
}
```
```js
const goButton = document.querySelector('.goButton');
goButton.addEventListener('click', () => {
    const box = document.querySelector('#box');
    box.classList.add('go');
});
```

* ***Create a transition that uses the ease-out timing function when transitioning in and ease-in when transitioning out.***

_button will ease-out transition to a new color and return to original state when mouseoff_
```html
<button class="btn">Hover over me!</button>
```
```css
.btn {
	border: 1px solid black;
	background-color: #2962ff;
	color: #fff;
	font-weight: bold;
	height: 50px;
	width: 100px;
	transition: background-color 1.5s ease-in;
}

.btn:hover {
	background-color: #1de9b6;
	transition-timing-function: ease-out;
	transition: 0.5s ease-out;
}
```

## 6.2 CSS Animations

[Back to top](#lesson-6-solutions)

* ***Create a @keyframes declaration and use the animation.***

* ***Experiment with animation-direction. Try all four values and see how your animation-timing-function affects it.***

* ***Pause and play your animation with CSS and JavaScript.***

* ***Play around with animation-fill-mode and see if you can find a use for none, backwards and both. Let me know if you do. Otherwise, learn the forwards mode :)***

* ***Try and create a more life-like heartbeat animation!***

<!-- Solutions above only -->

## End of document

[Next Lesson](../lesson7/solutions.md)
