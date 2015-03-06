# Anatomy of SVG

## SVG Tag

```svg
<svg version="1.1" xmlns="http://www.w3.org/2000/svg" width="100" height="100" viewBox="0 0 50 50">
  ...
</svg>
```

Example SVG tag, can be either as a seperate file or included in an html file.

**version:** version 1.1 is the most supported, use it.

**xmlns:** this stands for XML NameSpace. This is what tells the browser how to interpret the content (almost like a file type). It might look like it is a url but it is just a string. Namespace only needs to be decalred in the root element as it says that the ```<svg>``` tag and all decendants belong to the SVG dialect of XML.

**height & width:** sets the size of the SVG canvas. Together they set the viewport size of the svg. 

**viewBox:** defines which parts of the svg to show. 

### XLink

Sometimes you will need to declare the XLink namespace prefix if you are linking to assests within or external to the SVG. More on this later.

```svg
<svg ... xmlns:xlink="http://www.w3.org/1999/xlink">
  ... 
</svg>
```
[More on Namespaces](https://developer.mozilla.org/en/docs/Web/SVG/Namespaces_Crash_Course)

### Viewbox

To come.

## Elements

So how do you actually draw anything with an SVG? With elements like ```<path>``` and ```<circle>```, for full details see [SVG elements reference](https://developer.mozilla.org/en-US/docs/Web/SVG/Element). 

* ```<path>``` - genertic element that can be used to form many shapes and curves (including bezier curves and archs)
* ```<circle>``` - used to create a circle using a centre point and radius
* ```<line>``` - used to create a line between two points
* ```<polyline>``` - used to create a series of stright lines connecting several points
* ```<rect>``` - used to create a rectangle using the position of a corner and their width and height
* ```<ellipse>``` - used to create an ellipse
* ```<polygon>``` - used to create a closed shape consisting of a set of connected straigh lines
* ```<image>``` - allows a raster image to be included in the SVG
* ```<use>``` - clone other elements already in use

```svg
<path d="M10 10 C 10 40, 180 40, 180 10" stroke="black" fill="transparent" />

<circle cx="10" cy="10" r="2" fill="red"/>

<line x1="40" x2="140" y1="40" y2="40" stroke="black" stroke-width="20" />

<polyline points="40 60 80 20 120 60" stroke="black" stroke-width="20" />

<rect width="100%" height="100%" fill="green" />
  
<ellipse cx="60" cy="60" rx="50" ry="25"/>

<polygon points="60,20 100,40 100,80 60,100 20,80 20,40"/>

<image xlink:href="/img/exampleImage.png" x="0" y="0" height="100" width="100" />

<!-- Use -->
<svg width="100%" height="100%" 
  xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
  <style>
    .classA { fill:red }
  </style> 
  <defs>
    <g id="Port">
      <circle style="fill:inherit" r="10"/>
    </g>
  </defs>
 
  <text y="15">black</text>
  <use x="50" y="10" xlink:href="#Port" />
  
  <text y="35">red</text>
  <use x="50" y="30" xlink:href="#Port" class="classA"/>
  
  <text y="55">blue</text>
  <use x="50" y="50" xlink:href="#Port" style="fill:blue"/>
</svg>

```

### Other Elements

* ```<g>``` - like a div element in html, used to group objects. Transformations applied to the g are performed on all of its children and attributes are inherited by its children. 
* ```<defs>``` - like head element in html, used to create elements that don't appear in the SVG directly but are used by other element, for example gradients or styles. 

```svg
<svg ... >
  <g fill="red">
    <rect x="0" y="0" width="10" height="10" />
    <rect x="20" y="0" width="10" height="10" />
  </g>
</svg>

<svg ... >
  <defs>
    <style type="text/css"><![CDATA[
      #ExampleRect
    ]]>
  </defs>
  <rect ... id="ExampleRect"/>
</svg>
```

*Not sure why styles need to be wrapped in CDATA but I have seen it more than once so will do myself.*

## Fills and Strokes

The most basic colouring of elements is done via the fill and stroke attributes. Fill sets the colour inside the object and stroke sets the colour of the line drawn around the object. They can be set on the node or vis CSS.

```svg
<rect ... fill="red" stroke="red" />
```

```svg
#ExampleRect {
  fill="red";
  stroke="black"
  ...
  <rect ... id="ExampleRect" />
```  

## Gradients

There are two types of gradient, linear and radial. You **must** give the gradient an ```id```. Gradients are defined in ```defs``` section as opposed to on a shape itself to promote reusability. 

### Linear Gradient

The stops tell the gradient what colour it should be at certain positions. The stops can also be assigned by CSS and stops can also have opacity. 

```svg
<defs>
  <linearGradient id="Gradient1">
    <stop offset="0%" stop-color="red"/>
    <stop offset="50%" stop-color="black" stop-opacity="0.5"/>
    <stop offset="100%" stop-color="blue"/>
  </linearGradient>
</defs>
<rect x="10" y="10" width="100" height="100" fill="url(#Gradient1)" />
```

### Radial Gradient

Similar to liniear but a gradient radiated from a point. 

```svg
<defs>
    <radialGradient id="Gradient1">
      <stop offset="0%" stop-color="red"/>
      <stop offset="100%" stop-color="blue"/>
    </radialGradient>
</defs>
<rect x="10" y="10" rx="15" ry="15" width="100" height="100" fill="url(#Gradient1)"/> 
```

#### Spread Method

Spread method controls what happens when the gradient reaches its end but isnt filled yet:

```svg
<radialGradient spreadMethod="pad" ... />
<radialGradient spreadMethod="repeat" ... />
<radialGradient spreadMethod="reflect" ... />
```

## Patterns

Declare the pattern in the def and reference from the pattern element.

```svg
<defs>
  <pattern id="Pattern" x="0" y="0" width=".25" height=".25">
      <rect x="0" y="0" width="50" height="50" fill="skyblue"/>
      <rect x="0" y="0" width="25" height="25" fill="red"/>
      <circle cx="25" cy="25" r="20" fill="yellow" fill-opacity="0.5"/>
    </pattern>
</defs>
<rect fill="url(#Pattern)" stroke="black" x="0" y="0" width="200" height="200"/>
```

Patterns can be quite difficult to use so check the [MDN for full description](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Patterns), especialy on how sizing works. 

## Text

Simple text:

```svg
<text x="10" y="10">Hello World!</text>
```

Using the ```tspan``` element. Like html ```span``` element. Must be inside ```text``` element.

```svg
<text>
  <tspan font-weight="bold" fill="red">This is bold and red</tspan>
</text>
```

### Other Text Elements

* **x**: Set a new absolute x coordinate for the containing text.
* **dx**: Start drawing the text with a horizontal offset from the defult current position.
* **rotate**: roates all characters by this degree
* **textLength**: used to fine-tune the rendering position of the glyphs.
* **tref**: reference already defined text and copying it, can use ```xlink:href``` attribute.

```svg
<text id="example">This is an example text.</text>

<text>
    <tref xlink:href="#example" />
</text>
```

## Transformations

Transformations can be chained simpley by concaternating them, seperated by whitespace. Applying transformations effects the coordinate system. 

### Translations

Move an element around.

```svg
<rect x="0" y="0" width="10" height="10" transform="translate(30,40)" />
```

### Rotation 

```svg
<rect x="20" y="20" width="20" height="20" transform="rotate(45)" />
```

### Skewing

```svg
<rect x="20" y="20" width="20" height="20" transform="skewX(10) skewY(20)" />
```

### Scaling

Takes two numbers for x and y, if the first is ommited it is assumed to be equal to the first. The x and y position as well as the width and height are scaled. A value of 0.5 will reduce by 50%.

```svg
<rect x="100" y="40" width="20" height="20" transform="scale(0.5)" />
```

### Embedding SVG in SVG

You can embed svg elements inside other svg elements. This allows you to create a new coordinates system.

```svg
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
  <svg width="100" height="100" viewBox="0 0 50 50">
    <rect width="50" height="50" />
  </svg>
</svg>
```

## Clipping and Masking

### Clipping

Removing parts of elements defined by other parts. Transparent effects not possible. Define the clip path in ```defs```.

```svg
<defs>
  <clipPath id="cut-off-bottom">
    <rect x="0" y="0" width="200" height="100" />
  </clipPath>
</defs>

<circle cx="100" cy="100" r="100" clip-path="url(#cut-off-bottom)" />
```

### Masking

Allows soft edges by taking transparency and grey values of the mask.

```svg
<defs>
  <mask id="Mask">
    <rect ... />
  </mask>
</defs>
<rect ... mask="url(#Mask)" />
```

## Embedding Raster Images

```svg
<image x="90" y="-65" width="128" height="146" transform="rotate(45)"
     xlink:href="https://developer.mozilla.org/media/img/mdn-logo.png"/>
```
