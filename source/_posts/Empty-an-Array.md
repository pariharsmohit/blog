---
title: Empty an Array in JavaScript
date: 2017-02-06 20:53:56
tags:
---
***For instance:***
```bash
var arrayList =  ['a', 'b', 'c', 'd', 'e', 'f']
;
```
***How can we empty the array above?***

There are a couple of ways by which we can empty an array, So let's discuss all the possible way by which we can empty an array.

### Method 1
```bash
arrayList = [];
```
The code above will set the variable arrayList to a new empty array. This is recommended if you don't have references to the original array arrayList anywhere else because It will actually create a new empty array. You should be careful with this way of empty the array, because if you have referenced this array from another variable, then the original reference array will remain unchanged, Only use this way if you have only referenced the array by its original variable arrayList.

For instance:
```bash
var arrayList = ['a', 'b', 'c', 'd', 'e', 'f']; // Created array
var anotherArrayList = arrayList;  // Referenced arrayList by another variable
arrayList = []; // Empty the array
console.log(anotherArrayList); // Output ['a', 'b', 'c', 'd', 'e', 'f']
```
### Method 2
```bash
arrayList.length = 0;
```
The code above will clear the existing array by setting its length to 0. This way of emptying an array will also update all the reference variables that point to the original array.

For instance:
```bash
var arrayList = ['a', 'b', 'c', 'd', 'e', 'f']; // Created array
var anotherArrayList = arrayList;  // Referenced arrayList by another variable
arrayList.length = 0; // Empty the array by setting length to 0
console.log(anotherArrayList); // Output []
```
### Method 3
```bash
arrayList.splice(0, arrayList.length);
```
Above implementation will also work perfectly. This way of empty the array will also update all the references of the original array.

```bash
var arrayList = ['a', 'b', 'c', 'd', 'e', 'f']; // Created array
var anotherArrayList = arrayList;  // Referenced arrayList by another variable
arrayList.splice(0, arrayList.length); // Empty the array by setting length to 0
console.log(anotherArrayList); // Output []
```
### Method 4
```bash
while(arrayList.length) {
  arrayList.pop();
}
```
Above implementation can also empty the array. But not recommended to use often.