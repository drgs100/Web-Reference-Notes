# Javascript Notes

Reference notes for javascript (including jQuery).

## JQuery

```javascript
$(document).ready();
```

Document ready, basic jQuery. When page is fully loaded do what is in the parentheses.

```javascript
$(document).ready(function()
  {
  
  });
  ```
  
Creating an anonymous function declaration, which means an unnamed function that will run whatever code is inside the curly brackets ```{}```.
  
  ```javascript
$(document).ready(function () {

  $("#hoverImage").mouseenter(function () {
    console.log("enter")
  }).mouseleave(function () { 
    console.log("leave")
  });
  
});
```

The image with id ```hoverImage``` not has two events bound to it, ```mouseenter``` and ```mouseleave```. They are chained together here but could have been written out seperatly. 
