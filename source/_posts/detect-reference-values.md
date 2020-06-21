---
title: Detection of reference values in JavaScript
date: 2018-12-13 22:37:49
tags:
---
In Javascript Object are called as reference type, Any value other then primitive is definitely a reference type. There are several built-in reference type such as **Object, Array, Function, Date, null** and **Error**.

Detecting object using `typeof` operator
```bash
console.log(typeof {});           // object
console.log(typeof []);           // object
console.log(typeof new Array());  // object
console.log(typeof null);         // object 
console.log(typeof new RegExp()); // object
console.log(typeof new Date());   // object
```
But the downside of using typeof operator to detect an object is that typeof returns `object` for `null` (However this is fact that null is an object in JavaScript).

The best way to detect an object of specific reference type using `instanceof` operator.

>Syntax : value `instanceof` constructor

```bash
//Detecting an array
if(value instanceof Array){
	console.log("value is type of array");
}
```
```bash
// Employee constructor function
function Employee(name){
	this.name = name; // Public property
}

var emp1 = new Employee('John');

console.log(emp1 instanceof Employee); // true
```
`instanceof` not only check the constructor which is used to create an object but also check it's prototype chain see below example.
```bash
console.log(emp1 instanceof Object); // true
```