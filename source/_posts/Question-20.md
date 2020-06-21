---
title: Difference between typeof and instanceof
date: 2017-04-25 10:05:33
tags:
---
`typeof` is an operator that returns a string with the type of whatever you pass.

The `typeof` operator checks if a value belongs to one of the seven basic types: `number`, `string`, `boolean`, `object`, `function`, `undefined` or `Symbol`.

`typeof(null)` will return `object`.

`instanceof` is much more intelligent: it works on the level of prototypes. In particular, it tests to see if the right operand appears anywhere in the prototype chain of the left. `instanceof` doesn’t work with primitive types. `instanceof` operator checks the current object and returns `true` if the object is of the specified type, for example:
```bash
var dog = new Animal();
dog instanceof Animal; // Output : true
```
Here dog instanceof Animal is true since dog inherits from Animal.prototype
```bash
var name = new String("xyz");
name instanceof String; // Output : true
```