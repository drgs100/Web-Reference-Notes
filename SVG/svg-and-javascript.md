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

## Sources

  *  [Using Javascript to control an SVG](http://www.petercollingridge.co.uk/data-visualisation/using-javascript-control-svg)
  *  [d3js.org](http://d3js.org/)
