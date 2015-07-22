# Inserting and deleting nodes

## Creating and appending nodes

```document.createElement(element)``` - Makes a new element but does not added it to the DOM.

```myNode.appendChild(element)``` - Adds element inside a node.

```js
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

// Find location to insert using dir(newNode) to find child node, before node 5 for our example.
var newNode = document.querySelector("#location");

// Insert
newNode.insertBefore(pNode, newNode.childNodes[5]);
```

## Cloning and removing nodes

```cloneNode()``` - makes a copy and you can the reposition the node.

```removeChild(myNode)``` - removs the node but has to be called from a parent node.

```js
// Cloning, use true to copy all child nodes. 
var newNode = myNode.cloneNode(true)

// Remove node by referencing to its parent.
myNode.parentNode.removeChild(myNode)
```

## Replacing existing nodes

```replaceChild()``` - replaces a node, must be called from parent node.

```js
replaceNode.parentNode.replaceChild(myNode, replaceNode);
```


