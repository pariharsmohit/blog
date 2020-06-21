---
title: Reference error in function declaration
date: 2017-03-30 15:09:56
tags:
---

```bash
// NFE (Named Function Expression)
let foo = function bar() { return 12; };
typeof bar();
```
The output will be Reference Error. To fix the bug we can try to rewrite the code a little bit:

### Sample 1
```bash
let bar = function() { return 12; };
typeof bar();
```

### Sample 2
```bash
function bar() { return 12; };
typeof bar();
```
The function definition can have only one reference letiable as a function name, In sample 1 bar is reference letiable which is pointing to anonymous function and in sample 2 we have function statement and bar is the function name.
```bash
let foo = function bar() {
  // foo is visible here
  // bar is visible here
  console.log(typeof bar()); // Works here :)
};
// foo is visible here
// bar is undefined here
```