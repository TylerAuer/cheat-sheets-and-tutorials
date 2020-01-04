# Key Ideas in JavaScript

**Important Note**: Much of the writing in this document is a direct quotation from [MDN](https://developer.mozilla.org/en-US/), [W3Schools](https://www.w3schools.com/), or other resources. While the work of organizing, selecting, and formating information is my own, I did not write a large majority of this information.

## Table of Contents

* [Arrow Functions](#Arrow-Functions)
* [array.map](#array.map())

## Arrow Functions

An arrow function expression is a syntactically compact alternative to a regular function expression, although without its own bindings to the this, arguments, super, or new.target keywords. Arrow function expressions are ill suited as methods, and they cannot be used as constructors.

There is one subtle difference in behavior between ordinary function functions and arrow functions. Arrow functions do not have their own this value. The value of this inside an arrow function is always inherited from the enclosing scope.

### Examples

```JavaScript
// job is the input and the restult of job.isSelected() is returned
var selected = allJobs.filter(job => job.isSelected());

// a and b are the parameters passed to the unnamed function that adds them
var total = values.reduce((a, b) => a + b, 0);

// can be used to execute a few defined functions
$("#confetti-btn").click(event => {
  playTrumpet();
  fireConfettiCannon();
});

// when using arrow functions to create plain objects. Always wrap the object in parentheses
var chewToys = puppies.map(puppy => {});   // BUG!
var chewToys = puppies.map(puppy => ({})); // ok
```

When you just need a simple function with one argument, the new arrow function syntax is simply `Identifier => Expression`. You get to skip typing function and return, as well as some parentheses, braces, and a semicolon.

### Arrow Function Resources

* [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
* [Hacks.mozilla](https://hacks.mozilla.org/2015/06/es6-in-depth-arrow-functions/)

## `array.map()`

Takes a array and calls a function for each element in the array. The outputs are placed in a new array.

`array.map(function(currentValue, index, arr), thisValue)`

* `function(currentValue, index, arr)` - **Required**: A function to be run for each element in the array.
Function arguments:
  * `currentValue` - **Required**: The value of the current element
  * `index` - **Optional**: The array index of the current element
  * `arr` - **Optional**: The array object the current element belongs to
* `thisValue` - **Optional.** A value to be passed to the function to be used as its "this" value. If this parameter is empty, the value "undefined" will be passed as its "this" value

### Example

```JavaScript
const materials = [
  'Hydrogen',
  'Helium',
  'Lithium',
  'Beryllium'
];

console.log(materials.map(material => material.length));
// expected output: Array [8, 6, 7, 9]
```

### `map()` Resources

* [W3Schools](https://www.w3schools.com/jsref/jsref_map.asp)
* [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
