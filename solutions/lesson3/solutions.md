# Lesson 3

[Previous Lesson](../lesson2/solutions.md)

<!-- TOC -->

* [Lesson 3](#lesson-3)
  * [3.2 Selecting an element](#32-selecting-an-element)
  * [3.3 Changing style](#33-changing-style)
  * [3.8 Changing Attributes / Exercise](#38-changing-attributes--exercise)
  * [End of document](#end-of-document)

<!-- /TOC -->

<!-- Solutions below only -->

## 3.2 Selecting an element

[Back to top](#lesson-3-solutions)

```html
<div id="star-wars">
  <div class="character" data-type="hero">Luke Skywalker</div>
  <div class="character" data-type="master">Yoda</div>
  <div class="character" data-type="villain">Darth Vader</div>
</div>
```

* **The entire star-wars element**
  _by id:_

```js
const starWarsElement = document.querySelector('#star-wars')
```

* **The Luke Skywalker element**
  _by tag:_

```js
// building off of the first selector and knowing that
// querySelector matches the first character class element
const lukeElement = starWarsElement.querySelector('div')
```

* **The Yoda element**
  _by class:_

```js
// how is this possible if it only matches the first element and there's no unique tag?
const yodaElement = characterElements.querySelector('.character')
```

* **The Darth Vader element**
  _by attribute:_

```js
const darthElement = starWarsElement.querySelect('[villain]')
```

## 3.3 Changing style

[Back to top](#lesson-3-solutions)

* **Familiarize yourself with getting and setting values of various CSS properties. You can use any property you can think of. Here's a few to start with:**

* **Try using these two methods to get and set your styles:**

1. `Element.style`
2. `window.getComputedStyle`

_Using `Panda Cub` sample code._

1. color

```js
// get the element
const pandaCub = document.querySelector('div')

// set the color inline style
const color = (pandaCub.style.color = 'green')

// get the inline styles
const inlineStyles = window.getComputedStyle(pandaCub, null)
inlineStyles.color
```

2. backgroundColor

```js
// set
const backgroundColor = (pandaCub.style.backgroundColor = 'red') // or rgb(255,0,0)

// get the styles
const inlineStyles = window.getComputedStyle(pandaCub, null) // returns all style
inlineStyles.backgroundColor // rgb(255,0,0)
```

3. fontSize

```js
// set
const fontSize = (pandaCub.style.fontSize = '20px')

// get from inlineStyles
inlineStyles.fontSize // 20px
```

4. fontWeight

```js
const fontWeight = (pandaCub.style.fontWeight = 'bold')

// get from inlineStyles
inlineStyles.fontWeight // bold or 700
```

## 3.8 Changing Attributes / Exercise

[Back to top](#lesson-3-solutions)

* HTML

```html
<div class="clown-hat" data-color="red" data-num-stripes="3">A Clown hat</div>
```

* Set an attribute with Element.setAttribute

```js
const getClown = document.querySelector('.clown-hat')
getClown.setAttribute('data-awesomeness', true)
```

* Get an attribute with Element.getAttribute

```js
const getAwesome = getClown.getAttribute('data-awesomeness')
console.log((title = 'data-awesomeness:'), getAwesome)
```

* Get an attribute with Element.dataset

```js
const getNumStripes = getClown.dataset.numStripes
console.log((title = 'data-num-stripes:'), getNumStripes)
```

* Set an attribute with Element.dataset

```js
getClown.dataset.hatSize = 'huge'
```

* Remove attribute with Element.removeAttribute

```js
getClown.removeAttribute('data-awesomeness')
```

<!-- Solutions above only -->

## End of document

[Next Lesson](../lesson4/solutions.md)
