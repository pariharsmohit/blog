---
title: Calculate the length of associative array
date: 2017-04-30 19:10:33
tags:
---
```js
var counterArray = {
  A : 3,
  B : 4
};
counterArray["C"] = 1;
```
First of all, in case of JavaScript an associative array is the same as an object. Secondly, even though is no built-in function or property available to calculate the length/size an object, we can write such function ourselves.

### Method 1
`Object` has `keys` method which can we used to calculate the length of object.

```js
Object.keys(counterArray).length; // Output 3
```
### Method 2
We can also calculate the length of object by iterating through the object and by doing a count of own property of object. This way we will ignore the properties that came from the object's prototype chain:
```js
function getLength(object) {
  var count = 0;
  for(key in object) {
    // hasOwnProperty method check own property of object
    if(object.hasOwnProperty(key)) count++;
  }
  return count;
}
```
### Method 3
All modern browsers (including IE9+) support the `getOwnPropertyNames` method, so we can calculate the length using the following code:
```js
Object.getOwnPropertyNames(counterArray).length; // Output 3
```
### Method 4
Underscore and lodash libraries have the method `size` dedicated to calculate the object length. We don't recommend to include one of these libraries just to use the `size` method, but if it's already used in your project - why not?
```js
_.size({one: 1, two: 2, three: 3});
=> 3
```