---
title: Check if an object is an array or not
date: 2017-02-13 22:09:56
tags:
---
The best way to find whether an object is instance of a particular class or not using `toString` method from `Object.prototype`
```bash
let arrayList = [1 , 2, 3];
```
One of the best use cases of type checking of an object is when we do method overloading in JavaScript. To understand this, let's say we have a method called greet which can take a single string and also a list of strings. To make our greet method workable in both situation we need to know what kind of parameter is being passed: is it single value or list of values?
```bash
function greet(param) {
  if() {
    // here have to check whether param is array or not
  }
  else {
  }
}
```
However, in the above implementation it might not necessary to check the type of the array, we can check for single value string and put array logic code in else block, let see below code for the same.
```bash
 function greet(param) {
   if(typeof param === 'string') {
   }
   else {
     // If param is of type array then this block of code would execute
   }
 }
 ```

Now it's fine we can go with the previous two implementations, but when we have a situation like a parameter can be single value, array, and object type then we will be in trouble.

Coming back to checking the type of an object, As we mentioned that we can use `Object.prototype.toString`
```bash
if(Object.prototype.toString.call(arrayList) === '[object Array]') {
  console.log('Array!');
}
```
If you are using jQuery then you can also used jQuery isArray method:
```bash
if($.isArray(arrayList)) {
  console.log('Array');
} else {
  console.log('Not an array');
}
```
FYI jQuery uses `Object.prototype.toString.call` internally to check whether an object is an array or not.

In modern browser, you can also use:
```bash
Array.isArray(arrayList);
```
`Array.isArray` is supported by all the latest versions of Chrome, Firefox, IE, Opera and Safari.