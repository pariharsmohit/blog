---
title: How to use constructor functions for inheritance in JavaScript?
date: 2017-11-29 16:37:39
tags:
---
Let's say we have `Person` class which has name, age, salary properties and **`incrementSalary()`** method.
```js
function Person(name, age, salary) {
  this.name = name;
  this.age = age;
  this.salary = salary;
  this.incrementSalary = function (byValue) {
    this.salary = this.salary + byValue;
  };
}
```
Now we wish to create Employee class which contains all the properties of Person class and wanted to add some additional properties into Employee class.
```js
function Employee(company){
	this.company = company;
}

//Prototypal Inheritance 
Employee.prototype = new Person("Nishant", 24,5000);
```
In the example above, **Employee** type inherits from **Person**. It does so by assigning a new instance of `Person` to `Employee` prototype. After that, every instance of `Employee` inherits its properties and methods from `Person`.
```js
//Prototypal Inheritance 
Employee.prototype = new Person("Nishant", 24,5000);

var emp1 = new Employee("Google");

console.log(emp1 instanceof Person); // true
console.log(emp1 instanceof Employee); // true
```
Let's understand Constructor inheritance
```js
//Defined Person class
function Person(name){
	this.name = name || "Nishant";
}

var obj = {};

// obj inherit Person class properties and method 
Person.call(obj); // constructor inheritance

console.log(obj); // Object {name: "Nishant"}
```
Here we saw calling **`Person.call(obj)`** define the name properties from `Person` to `obj`.
```js
console.log(name in obj); // true
```
Type-based inheritance is best used with developer defined constructor function rather than natively in JavaScript. In addition to this also allows flexibility in how we create similar type of object.