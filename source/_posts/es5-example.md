---
title: ES5 Example
date: 2017-09-31 22:37:49
tags:
---
```bash
var arr = [10, 32, 65, 2];
for (var i = 0; i < arr.length; i++) {
  setTimeout(function() {
    console.log('The index of this number is: ' + i);
  }, 3000);
}
```
For ES6, you can just replace `var i` with `let i`.

For ES5, you need to create a function scope like here:

```bash
var arr = [10, 32, 65, 2];
for (var i = 0; i < arr.length; i++) {
  setTimeout(function(j) {
    return function () {
      console.log('The index of this number is: ' + j)
    };
  }(i), 3000);
}
```
This can also achieve by forEach (allows you to keep that variable within the forEach’s scope)

```bash
var arr = [10, 32, 65, 2];
arr.forEach(function(i) {
  setTimeout(function() {
    console.log('The index of this number is: ' + i);
  }, 3000);
})
```