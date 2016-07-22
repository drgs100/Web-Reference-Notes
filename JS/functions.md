# Functions

## Defining functions

### Function declaration

Function delcared as a statement (use this most of the time).

```js
function square(number) {
  return number * number;
  }
```

(The ```return``` statement specifies the value returned by the function.) 


### Function expression

Function expression, below is anonymous.

```js
var square = function(number) {
  return number * number
};
```

Function expression with name and can be used inside the function to refer to itself.

```js
var factoral = function fac(n) {
  return n<2 ? 1 : n*fac(n-1) 
};

console.log(factoral(3));
```

Anonmous function.

```js
function(x) {
  return x;
}
```

## Calling Functions

Defeining a function does not execute it. 

```js
square(5);
```

Functions must be in scope when they are called, but the function declaration can be hoisted (appear below the call in the code

```js
console.log(square(5));
/* ... */
function square(n) { return n*n };
```

Function hoisting only works with function declration and not function expression.

```js
consle.log(square(5))
square = function (n) {
  return n * n;
}
```