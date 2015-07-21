# Modifying DOM Attributes and Content

Simplest form is Dot notation. Some attribures, like class and for , are reserved. 

```js
img.src

// Change attribute
img.src = "http://nosuchsite.com""
```

If Dot notation is not viable:

```
\\ Get value
myNode.getAttribute(attributeName)

\\ Set value
myNode.setAttribute(attributeName, value)

\\ Boolean
myNode.setAttribute(attributeName)

\\ Remove attribute
myNode.removeAttribute(attributeName)
```
