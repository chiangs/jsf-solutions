# Lesson 9 Solutions
_Also known as Lesson 7 - Text & Content_

[Previous Lesson](../lesson8/solutions.md)

<!-- TOC -->

- [Lesson 9 Solutions](#lesson-9-solutions)
    - [9.1 Changing Text and HTML](#91-changing-text-and-html)
    - [9.2 Creating HTML Elements with JavaScript](#92-creating-html-elements-with-javascript)
    - [End of document](#end-of-document)

<!-- /TOC -->
<!-- Solutions below only -->

## 9.1 Changing Text and HTML

[Back to top](#lesson-9-solutions)
 
**Use `textContent` whenever you can because textContent works faster than `innerHTML`. The reason? There's no need to parse HTML.**

```html
<h1>Title</h1>
<h2>Subtitle</h2>
<p>Lorem ipsum dolor sit amet consectetur adipisicing elit...</p>
```

* ***Change text with textContent***

```js
const title = document.querySelector('h1')
title.textContent = 'Hello World'
```

* ***Change text with innerHTML***

```js
const paragraph = document.querySelector('p')
paragraph.innerHTML = 'New informatino about something somewhere somehow'
```

* ***Change HTML with innerHTML***

```js
paragraph.innerHTML = '<h4 class="bold">This p element has been changed to an h4 element and assigned the attributes of the bold class"</h4>'
```

## 9.2 Creating HTML Elements with JavaScript

[Back to top](#lesson-9-solutions)

```html
<div class="characters">
  <ul class="hobbits">
    <li>Frodo Baggins</li>
    <li>Samwise "Sam" Gamgee</li>
    <li>Meriadoc "Merry" Brandybuck</li>
    <li>Peregrin "Pippin" Took</li>
  </ul>
  <ul class="elves">
    <li>Glorfindel</li>
    <li>Elrond</li>
    <li>Arwen Evenstar</li>
  </ul>
  <ul class="humans">
    <li>Gandalf</li>
    <li>Saruman</li>
    <li>Boromir</li>
    <li>Faramir</li>
  </ul>
</div>
```

* ***Create a list item, <li>Bilbo Baggins</li>, and add it as the last item in .hobbits***

```js
// First create the list item, then add the text
const bilbo = document.createElement('li')
bilbo.textContent = `Bilbo Baggins`

// To insert bilbo, we need to select the hobbits div first
const hobbitsList = document.querySelector('.hobbits')

// Use appendChild to add bilbo to the end of the list
hobbitsList.appendChild(bilbo)
```


* ***Create a list item, <li>Legolas</li>, and insert it as the first item in .elves.***

```js
const legolas = document.createElement('li')
legolas.textContent = `Legolas`

const elvesList = document.querySelector('.elves')
const glorfindel = elvesList[0]

elvesList.insertBefore(legolas, glorfindel)
```


* ***Create a list item, <li>Aragorn</li>, and insert it before <li>Boromir</li>.***

```js
const aragorn = document.createElement('li')
aragorn.textContent = `Aragorn`

const humansList = document.querySelector('.humans')
const boromir = humansList[2]
humansList.insertBefore(aragorn, boromir)
```

<!-- Solutions above only -->

## End of document

[Next Lesson]()
