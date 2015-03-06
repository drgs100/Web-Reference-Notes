# SVG Summary

Scalable vector graphics (SVG) is and XML-based vector image format. SVGs are XML tags that render shapes and graphics and these shapes and graphics can be interacted with and animated much like HTML elements can be. 

## Creation

SVGs are usually created in Illustrator but also possible to use Inkscape. Inkscape uses SVG as its native format but Illustrator does not so you will need to export as an SVG and then optimise the file. When exporting use the following parameters to begin with:

* SVG Profiles: SVG 1.1
* Type: Adobe CEF
* Subsetting: None (Use System Fonts)

Then optimise with the file: [SVG Optimiser](http://petercollingridge.appspot.com/svg_optimiser).

## Using SVGs

SVGs can be used for all vector graphics but the way you display an SVG on the page will depend on what you are using it for; an interactive chart using javascript will be different from a sprite. 

### Using SVG as an &lt;img&gt;

The simplest way to use SVGs is to use the &lt;img&gt; tag. Simply adding the source file as you would with any other image format.

```html
<img src="example-image.svg" alt="None existant example image">
```

**Browser Support:** all modern browsers, [lacks support in IE8 and down](http://caniuse.com/#feat=svg-img). For browser fall-backs see below.

### Using SVG as a background-image

With CSS you can set an SVG as a ```background-image```. 

```html
<div href="/" class="logo">
  Kiwi Corp
</div>
```
```css
.logo {
  display: block;
  text-indent: -9999px;
  width: 100px;
  height: 82px;
  background: url(example-image.svg);
  background-size: 100px 82px;
}
```

**Problem** inserting an SVG with either &lt;img&gt; or ```background-image``` means you cannot target the contents of the file with CSS or JavaScript.

**Browser Support:** again wide support [except for IE8 and down](http://caniuse.com/#feat=svg-css), see below for fallback options.

### Using 'inline' SVG

You can paste the text content of the SVG file directly into your web page. To prevent the page from becoming to bloated you can use server-side includes to insert the file. 

Inserting the file in this way will  allow you to control the image with both CSS and JavaScript. To do this successfully see below for the anatomy of the SVG format.

```html
<body>
  <h1>Example SVG</h1>
  
  <svg ...>
    <!-- contents of SVG -->
  </svg>
  ```
  
The output from Illustrator contains a DOCTYPE and a lot of other unnecessary junk, as mentioned before it is best to optimise the SVG before using it in the manner to help reduce the page size.  

### Other Options

It is also possible to include SVGs as &lt;object&gt; or as Data URIs but I'm not sure they are really relevant to us at the moment but you can read more on them with CSS Trick's [Using SVG](https://css-tricks.com/using-svg/).

## Fall-back Options

Because IE8 and below are still a reality we still need to provide a fall-back option for those users. The best way seems to use Modernizr to swap out SVGs for another image formate like PNG. 

### &lt;img&gt;

Using Modernizr

```javascript
if (!Modernizr.svg) {
  $(".logo img").attr("src", "images/logo.png");
}
```

Or with Javascript

```html
<img src="image.svg" onerror="this.onerror=null; this.src='image.png'">
```

### background-image

Using Modernizr, adds a 'no-svg' class to over-right the background image. If SVG is not supported then Modernizr will add the call ```.no-svg``` to the html element. 

```css
.main-header {
  background: url(logo.svg) no-repeat top left;
  background-size: contain;
}

.no-svg .main-header {
  background-image: url(logo.png);
}
```

### inline

Using Modernizr adds a fall-back div that is only displayed if SVG is not supported. The proviso is that the fall-back must be the size of the SVG it is replacing.

```html
<svg> ... </svg>
<div class="fallback"></div>
```

```css
.fallback { 
  display: none;
  /* Make sure it's the same size as the SVG takes up */
}
.no-svg .fallback { 
  background-image: url(logo.png); 
}
```

## Extending functionality

As SVGs are XML-based you can also open the file and see that they are written in text, using tags similar to html. Because of this it is possible to write and edit SVGs in a text editor but more importantly you can even target SVG elements, classes and IDs using CSS and JavaScript. To learn more about this see [anatomy of the SVG tag](anatomy-of-svg.md).
