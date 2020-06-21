---
title: Find the Longest Word in a String
date: 2018-08-03 11:20:26
tags:
---
***`In this problem we are going to return the length of the longest word in a string.`***

We provide **`Math.max`** with the length of each word as argument, and it will simply return the highest of all.

Let’s analyze everything inside the **`Math.max`** parenthesees to understand how we do that.

**`str.split(" ")`** splits the string into an array, taking spaces as separators. It returns this array: [“The”,"quick,“brown”,“fox”,“jumped”,“over”,“the”,“lazy”,“dog”].

Then, we will make another array, made from the lengths of each element of the **`str.split(" ")`** array with **`map()`**.

**`str.split(" ").map(word => word.length)`** returns [3, 5, 5, 3, 6, 4, 3, 4, 3]

Finally, we pass the array as argument for the **`Math.max`** function with the spread operator **`...`**
```js
function findLongestWordLength(str) {
  return Math.max(...str.split(" ").map(word => word.length));
}
```
or
We can do this by using the **'reduce()`** method also.
```js
function findLongestWordLength(s) {
  return s.split(' ')
    .reduce(function(x, y) {
      return Math.max(x, y.length)
    }, 0);
}
```