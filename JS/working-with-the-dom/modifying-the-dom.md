# Modifying DOM Attributes and Content

Simplest form is Dot notation. Some attribures, like class and for , are reserved. 

```js
img.src

// Change attribute
img.src = "http://nosuchsite.com""
```

If Dot notation is not viable:

```
// Get value
myNode.getAttribute(attributeName)

// Set value
myNode.setAttribute(attributeName, value)

// Boolean
myNode.setAttribute(attributeName)

// Remove attribute
myNode.removeAttribute(attributeName)
```

It is possible to create unvalid attributes using ```data-```

```js
myNode.setAttribute("data-foo", "bar")
```

## Targeting the attribute property

Returns attributes as a list anc can be access using numeric or named index and dot notation.

```js
var myNode = document.querySelector("#example img")

myNode.attributes[0]
myNode.attributes.src
myNode.attributes["src"]
```

## Text content modifiers

```js
myNode.innerHTML // changes text as HTML
myNode.outerHTML // includes elements's tag
myNodeinsertAdjacentHTML(insertionPoint, htmlText) // can insert text at beginning or end 
```

Possible to modify element as text by Firefox has seperate implementation.

```js
if (myNode.innerText){
  myText = myNode.innerText; // Everyone else
} else {
  myText = mynode.textContent; // FF version
}

```




