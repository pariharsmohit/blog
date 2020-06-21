---
title: Test string as a literal and as an object
date: 2018-03-06 18:42:26
tags: #string, #literal, #string as a literal
---
For example: We can create string using string literal and using String constructor function.
```bash
 // using string literal
 var ltrlStr = "Hi I am string literal";
 // using String constructor function 
 var objStr = new String("Hi I am string object");
 ```
We can use `typeof` operator to test string literal and `instanceof` operator to test String object.
```bash
 function isString(str) {
 	return typeof(str) == 'string' || str instanceof String;
 }
 
 var ltrlStr = "Hi I am string literal";
 var objStr = new String("Hi I am string object");
 console.log(isString(ltrlStr)); // true
 console.log(isString(objStr)); // true
 ```