---
title: How to check if the value of a variable is an array?
date: 2017-11-21 22:37:49
tags:
---
We always encounter in such situation where we need to know whether value is type of array or not.

For instance : the code below perform some operation based value type
```bash
function(value){
	if("value is an array"){
		// Then perform some operation
	}else{
		// otherwise
	}
}
```
Let's discuss some way to detect an array in JavaScript.

### Method 1:

```bash
	function isArray(value){
		return Object.prototype.toString.call(value) === '[object Array]';
	}
```
This approach is most popular way to detecting a value of type array in JavaScript and recommended to use. This approach relies on the fact that, native toString() method on a given value produce a standard string in all browser.

### Method 2:

Duck typing test for array type detection
```bash
 // Duck typing arrays
 function isArray(value){
 	return typeof value.sort === 'function';
 }
 ````
As we can see above isArray method will return true if value object have sort method of type function. Now assume you have created a object with sort method
```bash
var bar = {
    sort: function(){
        // Some code 
    }
}
```
Now when you check **`isArray(bar)`** then it will return true because bar object has sort method, But the fact is bar is not an array.

So this method is not a best way to detect an array as you can see it's not handle the case when some object has sort method.

### Method 3:

ECMAScript 5 has introduced **Array.isArray()** method to detect an array type value. The sole purpose of this method is accurately detecting whether a value is an array or not.

In many JavaScript libraries you may see the code below for detecting an value of type array.
```bash
function(value){
   // ECMAScript 5 feature
	if(typeof Array.isArray === 'function'){
		return Array.isArray(value);
	}else{
	   return Object.prototype.toString.call(value) === '[object Array]';
	}
}
```
### Method 4:

You can query the constructor name:
```bash
function isArray(value) {
	return value.constructor.name === "Array";
}
```

### Method 5:

You check if a given value is an instanceof Array:
```bash
function isArray(value) {
	return value instanceof Array;
}
```