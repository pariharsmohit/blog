---
title: Hoisting of function
date: 2017-04-12 18:09:56
tags:
---
Let's take the following function expression

``` bash
 var foo = function foo() {
     return 12;
 }
 ```

In JavaScript `var` -declared variables and functions are `hoisted` . Let's take function `hoisting` first. Basically, the JavaScript interpreter looks ahead to find all the variable declaration and hoists them to the top of the function where it's declared. For example:

``` bash
foo(); // Here foo is still undefined
var foo = function foo() {
  return 12;
};
```

The code above behind the scene look something like this:

``` bash
var foo = undefined;
foo(); // Here foo is undefined
foo = function foo() {
  // Some code stuff
}
```

``` bash
var foo = undefined;
foo = function foo() {
  // Some code stuff
}
foo(); // Now foo is defined here
```
