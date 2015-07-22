# Inserting and deleting nodes

## Creating and appending nodes

```js
document.createElement(element) // Makes a new element but does not added it to the DOM.

myNode.appendChild(element) // Adds element inside a node.

// Example 

// Create element and give it some properties. 
var myElement = document.createElement("img");
myElement.src = "images/example.svg";
myElement.alt = "This is an example of an image.";

// Add element to previously created node, we found the node using querySelectorAll which returns an array.
myNode[6].appendChild(myElement)
```

## Controlling node insertions with ```insertBefore```

```appendChild()``` lacks precision, use ```insertBefore()``` for surgical insertions. 

```js
// Example
var pNode = document.createElement("p");
var myText = document.createTextNode("foo bar");
pNode.appendChild(myText)

// Find location to insert us dir(newNode) to find child node, before node 5 for our example.
var newNode = document.querySelector("#location");

// Insert
newNode.insertBefore(pNode, newNode.childNodes[5]);






