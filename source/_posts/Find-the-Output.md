---
title: Find the Output
date: 2017-02-21 15:09:56
tags:
---
## What will be the output of the following code?
```js
var output = (function(x) {
  delete x; 
  return x; 
})(0); 

console.log(output); 
```
### Answer
The code above will output 0 as output. `delete` operator is used to delete a property from an object. Here x is not an object it's **`local variable`**. `delete` operator doesn't affect local variables.

## What will be the output of the following code?
```js
var x = 1; 
var output = (function() {
  delete x; 
  return x; 
})(); 

console.log(output); 
```
### Answer
The code above will output `1` as output. `delete` operator is used to delete a property from an object. Here `x` is not an object it's global variable of type `number`.

## What will be the output of the following code?
```js
var x = { foo : 1}; 
var output = (function() {
  delete x.foo; 
  return x.foo; 
})(); 

console.log(output); 
```
### Answer
The code above will output `undefined` as output. `delete` operator is used to delete a property from an object. Here `x` is an object which has foo as a property and from a self-invoking function, we are deleting the `foo` property of object `x` and after deletion, we are trying to reference deleted property `foo` which result `undefined`.

## What will be the output of the following code?
```js
var Employee = {
  company: 'xyz'
}
var emp1 = Object.create(Employee); 
delete emp1.company
console.log(emp1.company); 
```
### Answer
The code above will output xyz as output. Here emp1 object got company as prototype property. delete operator doesn't delete prototype property.

`emp1` object doesn't have company as its own property. you can test it `console.log(emp1.hasOwnProperty('company'));` `//output : false` However, we can delete company property directly from Employee object using delete Employee.company or we can also delete from emp1 object using `__proto__` property `delete emp1.__proto__.company.`