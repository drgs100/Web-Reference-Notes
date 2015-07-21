# [Enhancing the DOM with Ray Villalobos](http://www.lynda.com/HTML-tutorials/JavaScript-Enhancing-DOM/122462-2.html)

## Selecting DOM Elements

```getElementById()``` - most common method.

```getElementsbyTagName() - returns html elements in an array

```getElementsByClassName() - returns elements with specific class, does not work in Oldie. 

```querySelector()``` and ```querySelectorAll()``` - similar to jQuery, problems with Oldie but better than ```getElementsByClassName()```.

### Selecting Form Elements

```js
document.forms

// by array
document.forms[0]

// Form name and element name using Dot notation
document.register.myName 

// Change field value
document.register.myName = "Foo Bar"
```

### Moving up and down

```parentNode``` - Goes up a level.

```chilsNode``` - Array of children.

```firstChild/lastChild``` - Firest/Last element.

```previousSibbling/nestSibbling``` - Elements with same parent.

### Targeting Node Elements

Use to avoid picking up empty text elements. Losey browser support.

```firstElementChild``` - First element child, ingnores comments or text nodes.

```lastElementsChild```

```children```

```previousElementSibbling/nextElementSibbling```





