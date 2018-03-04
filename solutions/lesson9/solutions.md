# Lesson 9 Solutions

[Previous Lesson](../lesson8/solutions.md)

<!-- TOC -->

- [Lesson 9 Solutions](#lesson-9-solutions)
    - [9.1 Changing Text and HTML](#91-changing-text-and-html)
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

<!-- Solutions above only -->

## End of document

[Next Lesson]()
