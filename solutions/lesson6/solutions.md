# Lesson 6 Solutions

[Previous Lesson](../lesson5/solutions.md)

<!-- TOC -->

- [Lesson 6 Solutions](#lesson-6-solutions)
	- [6.1 CSS Transitions](#61-css-transitions)
	- [6.2 CSS Animations](#62-css-animations)
	- [6.5 Greensock API](#65-greensock-api)
	- [6.6 Animating the off-canvas menu](#66-animating-the-off-canvas-menu)
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

_Animation is a purple rectangle the stretches horizontally then back to normal size and then stretches vertically and repeates_
```html
<div class="box animated"></div>
```

```css
@keyframes myFirstAnimation {
	0%,
	100% {
		transform: scaleX(1);
	}

	25% {
		transform: scaleX(3);
	}

	50% {
		transform: scaleX(1);
	}

	75% {
		transform: scaleY(3);
	}
}

.box {
	border: 1px solid black;
	background-color: blueviolet;
	height: 50px;
	width: 100px;
	margin: 0 auto;
}

.animated {
	animation: myFirstAnimation 5s ease-in-out infinite alternate forwards running;
}
```

* ***Experiment with animation-direction. Try all four values and see how your animation-timing-function affects it.***

_normal: plays from beginning to end and starts over_

_reverse: plays from end to beginning and starts from end again_

_alternate and alternate-reverse: plays the animation then in opposite direction, so that you get the ends twice_

* ***Pause and play your animation with CSS and JavaScript.***

_using the same HTML and CSS in exercise 1..._
```css
.paused {
	animation-play-state: paused;
}

/* pausing via pure css and hover event, will continue 
when mouseoff */
.box:hover {
	animation-play-state: paused;
}
```

```js
const box = document.querySelector('.box')

box.addEventListener('click', () => {
	// toggle the animated class
	box.classList.toggle('animated')
	// or alternatively toggle a paused class
	box.classList.toggle('paused')
});
```

* ***Play around with animation-fill-mode and see if you can find a use for none, backwards and both. Let me know if you do. Otherwise, learn the forwards mode :)***

* ***Try and create a more life-like heartbeat animation!***

_Using the example HTML & CSS, modify the animation to match a heartbeat graph_

```css
@keyframes heartbeat {
	0%,
	50%,
	80% {
		transform: scale(1) rotate(-45deg);
	}

	35% {
		transform: scale(1.1) rotate(-45deg);
	}

	65% {
		transform: scale(1.5) rotate(-45deg);
	}
}
```

## 6.5 Greensock API

[Back to top](#lesson-6-solutions)

* ***Install GSAP into your project.***

_To install GSAP in your project, you need to include the library before you include your JavaScript file._

```js
// Link to GSAP
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/1.20.3/TweenMax.min.js"></script>

// Your main JavaScript comes next
<script src="js/main.js"></script>
```

* ***Create a tween that moves an object from 200px from the left to the right.***

_A tween is a single movement in an animation. In GSAP, a tween has the following syntax: `TweenMax.method(element, duration, vars)`_

```html
<div class="box"></div>
```

```css
.box {
	border: 1px solid black;
	background-color: #f50057;
	width: 100px;
	height: 100px;
}
```

```js
// select the box by class
const box = document.querySelector('.box')
// set the method `to` on the box element, pick any integer duration 
// and the x distance
TweenMax.to(box, 3, { x: 200 })
```

* ***Create a tween that moves an object 200px from the top to the bottom.***

_Using the same box object..._

```js
TweenMax.to(box, 3, { y: 200 })
```

* ***Create a tween that turns an object invisible.***

_Using the same box object..._

```js
TweenMax.to(box, 3, {opacity: 0})
```

* ***Chain five tweens with TimelineMax***'

```js
const box = document.querySelector('.box');
const tl = new TimelineMax({});

box.addEventListener('click', () => {
	tl.from(box, 2, {
		x: 200,
		rotation: 720,
		borderRadius: 50,
		ease: 'Power1.easeOut'
	});
	tl.to(box, 2, {
		y: 400,
		ease: 'Bounce.easeOut'
	});
	tl.to(box, 1, {
		borderRadius: 0,
		x: 350,
		ease: 'Power2.easeIn'
	});
	tl.to(box, 1, {
		rotation: 90,
		transformOrigin: 'right bottom',
		ease: 'Power2.easeIn'
	});
	tl.to(box, 3, {
		y: -300,
		borderRadius: 50,
		ease: 'Bounce.easeOut'
	});
});
```

## 6.6 Animating the off-canvas menu

_Only the transition property needs to be added the 2 container 
CSS classes._

```CSS
.site-container {
	transition: transform 0.5s ease-out;

}

.offsite-container {
	transition: transform 0.5s ease-out;
}
```

[Back to top](#lesson-6-solutions)

<!-- Solutions above only -->

## End of document

[Next Lesson](../lesson7/solutions.md)
