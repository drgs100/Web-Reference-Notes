# SVG and Javascript

As with HTML/CSS you can use javascript to manipulate the SVG DOM. There are two routes to manage this, either with straight JavaScript or by using a generic JavaScript library like JQuery or specific library for manipulating SVG like D3.js.

## Simple JS

SVG circle

```svg
<svg ...  width="400" height="300">
  <style>
    circle {
      fill-opacity: 0.5;
      stroke-width: 4;
      fill: #3080d0;
      stroke: #3080d0;
    }
  </style>
  <circle id="my-circle" cx="100" cy="100" r="50" />
</svg>
```

Change an element (in this case cx) with javasctipt.

```javascript
var svg = document.getElementById("circle-svg"); 
var svgDoc = svg.contentDocument;
var circle = svgDoc.getElementById("my-circle");
circle.setAttributeNS(null, "cx" 200);

```
## Using D3

D3 is a really neet javascript library which is probably best way of working with SVGs. It employs a technique called *chaining syntax*, allowing you to perform several actions in a single line of code. 

```javascript
d3.select("body").append("p").text("New paragraph!");
```

### Examples Methods

```.select()``` - Selects the first element that matches the specified selector string.

```.selectAll()``` - Selects all elements that match the specified selector.

### Using D3

Make life easier, use a variable. 

```javascript
var svg = d3.select("body")
              .append("svg")
              .attr("width", w)
              .attr("height", h);
````

Then when using D3 you must select something that doesn't exist, bind the data to it and then create it (I think).

```javascript
svg.selectAll("circle")
    .data(dataset)
    .enter()
    .append("circle");
```

### JSON

A specific syntax for organizing data as JavaScript objects. 

For more information I have been using the tutorials from [Interactive Data Visualisation](http://alignedleft.com/tutorials/d3/). 

## Sources

  *  [Using Javascript to control an SVG](http://www.petercollingridge.co.uk/data-visualisation/using-javascript-control-svg)
  *  [d3js.org](http://d3js.org/)
