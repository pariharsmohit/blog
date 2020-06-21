---
title: undefined x 1
date: 2017-02-29 15:09:56
tags:
---
```bash
var trees = ["redwood", "bay", "cedar", "oak", "maple"];
delete trees[3];
```
* When you run the code above and do `console.log(trees);` in chrome developer console then you will get `["redwood", "bay", "cedar", undefined × 1, "maple"]`.
* In the recent versions of Chrome you will see the word `empty` of `undefined x 1`.
* When you run the same code in Firefox browser console then you will get `["redwood", "bay", "cedar", undefined, "maple"]`

Clearly we can see that Chrome has its own way of displaying uninitialized index in arrays. However when you check `trees[3] === undefined`in any browser you will get similar output as `true`.

**Note**: Please remember that you need not check for the uninitialized index of the array in trees[3] === 'undefined × 1' it will give an error because 'undefined × 1' this is just way of displaying an uninitialized index of an array in chrome.