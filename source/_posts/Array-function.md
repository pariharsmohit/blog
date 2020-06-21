---
title: Array.prototype.function()
date: 2019-10-17 11:08:33
tags:
---
## Function Syntax

A function in JavaScript comprises of three statements.

* The name of the function.
* A list of arguments to the function enclosed in parentheses and separated by commas.
* The JavaScript statements that define the function, enclosed

Function in Javascript is defined in a number of ways. the common function definition is
```js
function function_name(arg1,arg2,...) {
//operation to be carried out by the function
}
```

## Prototype

Prototypes are the mechanism by which JavaScript objects inherit features from one another.

JavaScript is often described as a prototype-based language — to provide inheritance, objects can have a prototype object, which acts as a template object that it inherits methods and properties from.

In JavaScript, a link is made between the object instance and its prototype, and the properties and methods are found by walking up the chain of prototypes.

## My forEach

The ***`myForEach()`*** method calls a provided callback function once for each element in an array in ascending order.

* **`callback`** - Function to execute on each element. It accepts between one and three arguments:
    * ***`currentValue`*** - The current element being processed in the array.
    * ***`index Optional`*** - The index currentValue in the array.
    * ***`array Optional`*** - The array myForEach() was called upon.

```js
Array.prototype.myForEach = function(f) {
for (let i = 0; i < this.length; i++) {
f(this[i], i ,this);
}
}
```
Example :-
```js
myArray = [1, 2, 3, 4];
myArray.myForEach((item,index,arr) => {
console.log(item, index, arr);
})
```
This results in -
```js
1 0 (4) [1, 2, 3, 4]
2 1 (4) [1, 2, 3, 4]
3 2 (4) [1, 2, 3, 4]
4 3 (4) [1, 2, 3, 4]
```

## My Map

The ***`myMap()`*** method creates a new array populated with the results of calling a provided function on every element in the calling array.

* ***`callback`*** - Function to execute on each element. It accepts between one and three arguments:
    * ***`currentValue`*** - The current element being processed in the array.
    * ***`index Optional`*** - The index currentValue in the array.
    * ***`array Optional`*** - The array myMap() was called upon.

```js
Array.prototype.myMap = function(f) {
let result = [];
for (let i = 0; i < this.length; i++) {
result.push(f(this[i], i, this));
}
return result;
}
```
Example :-
```js
let arr = [1, 2, 3, 4, 7, 14, 21]
console.log(arr.myMap(item => item % 7 === 0));
```
This reults in -
```js
[false, false, false, false, true, true, true,]
```

## My Some

The ***`mySome()`*** method tests whether at least one element in the array passes the test implemented by the provided function. It returns a Boolean value.

* ***`callback`*** - Function to execute on each element. It accepts between one and three arguments:
    * ***`currentValue`*** - The current element being processed in the array.
    * ***`index Optional`*** - The index currentValue in the array.
    * ***`array Optional`*** - The array mySome() was called upon.

```js
Array.prototype.mySome = function(f) {
let result = false;
for (let i = 0; i < this.length; i++) {
if(f(this[i], i, this)) {
result = true;
}
}
return result;
}
```
Example :-
```js
let arr = [1, 2, 3, 4, 7]
arr.mySome(item => item % 7 === 0);
```
This results in -
```js
true
```

## My Includes

The ***`myIncludes()`*** method determines whether an array includes a certain value among its entries, returning true or false as appropriate.

* ***`valueToFind`*** - The value to be looked for.
* ***`fromIndex`*** - The index currentValue in the array.

```js
Array.prototype.myIncludes = function(valueToFind, fromIndex = 0) {
let result = false;
for (let i = fromIndex; i < this.length; i++) {
if(this[i] === valueToFind) {
result = true;
}
}
return result;
}
```
Example :-
```js
console.log([1, 2, 3, 4].myIncludes(1));
//true
```
OR
```js
console.log([1,2,3,4].myIncludes(4,3));
//true
```

## My Filter
The ***`myFilter()`*** method creates a new array with all elements that pass the test implemented by the provided function.

* ***`callback`*** - Function to execute on each element. It accepts between one and three arguments:
    * ***`currentValue`*** - The current element being processed in the array.
    * ***`index Optional`*** - The index currentValue in the array.
    * ***`array Optional`*** - The array myFilter() was called upon.

```js
Array.prototype.myFilter = function(f) {
let result = [];
for (let i = 0; i < this.length; i++) {
if(f(this[i], i, this)) {
result.push(this[i]);
}
}
return result;
}
```
Example :-
```js
const cars = ['BMW', 'Suzuki', 'Mercedes', 'Honda', 'Mahindra', 'Tata'];

const result = cars.myFilter(item => item.length>5);
```
This results in-
```js
['Suzuki', 'Mercedes', 'Mahindra']
```

## My Reducer Function
The ***`myReduce()`*** method executes a reducer function (that you provide) on each element of the array, resulting in a single output value.

* ***`callback`*** - Function to execute on each element. It accepts two arguments
* ***`initialValue`*** - To be passed in to the callback function
    * ***`startValue`*** - The value to start from in the callback function.
    * ***`currentValue`*** - The value that is present in the loop.

```js
Array.prototype.myReduce = function(f, initialValue) {
let result = initialValue;
for (let i = 0; i < this.length; i++) {
result = f(result, this[i]);
}
return result;
}
```
Example :-
```js
let arr = [1, 2, 3, 4];
console.log(arr.myReduce((a,c) => a + c, 5));
```
This resullts in -
```js
15
/* initialValue = 5
function performs the function of adding all the array elements
result = 5 + 1 + 2 + 3 + 4 = 15 */
```