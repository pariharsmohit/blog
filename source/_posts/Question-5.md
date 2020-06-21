---
title: Simple Example of Nested Functions
date: 2017-01-29 09:53:56
tags:
---
## A **`mul`** function which will work properly when invoked with following syntax.
```bash
console.log(mul(2)(3)(4)); // output : 24
console.log(mul(4)(3)(4)); // output : 48
```
Below is the code followed by the explanation of how it works:
```bash
function mul (x) {
  return function (y) { // anonymous function
    return function (z) { // anonymous function
      return x * y * z;
    };
  };
}
```
Here the `mul` function accepts the first argument and returns the anonymous function which takes the second parameter and returns the anonymous function which takes the third parameter and returns the multiplication of arguments which is being passed in successive

In Javascript function defined inside has access to outer function variable and function is the first class object so it can be returned by the function as well and passed as an argument in another function.

* A function is an instance of the Object type
* A function can have properties and has a link back to its constructor method
* A function can be stored as variable
* A function can be pass as a parameter to another function
* A function can be returned from another function