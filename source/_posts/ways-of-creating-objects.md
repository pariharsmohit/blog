---
title: Ways of creating objects in JavaScript
date: 2017-06-18 09:20:16
tags:
---
### Method 1: Function based
This method is useful if we want to create several similar objects. In the code sample below, we wrote the function `Employee` and used it as a constructor by calling it with the `new` operator.
```js
  function Employee(fName, lName, age, salary){
  	this.firstName = fName;
  	this.lastName = lName;
  	this.age = age;
  	this.salary = salary;
  }

  // Creating multiple object which have similar property but diff value assigned to object property.
  var employee1 = new Employee('John', 'Moto', 24, '5000$');
  var employee2 = new Employee('Ryan', 'Jor', 26, '3000$');
  var employee3 = new Employee('Andre', 'Salt', 26, '4000$');
  ```
### Method 2: Object Literal
Object Literal is best way to create an object and this is used frequently. Below is code sample for create employee object which contains property as well as method.
```js
var employee = {
	name : 'Nishant',
	salary : 245678,
	getName : function(){
		return this.name;
	}
}
```
The code sample below is Nested Object Literal, Here address is an object inside employee object.
```js
var employee = {
	name : 'Nishant',
	salary : 245678,
	address : {
		addressLine1 : 'BITS Pilani',
		addressLine2 : 'Vidya Vihar'.
		phoneNumber: {
		  workPhone: 7098889765,
		  homePhone: 1234567898
		}
	}
}
```
### Method 3: From `Object` using `new` keyword
In the code below, a sample object has been created using `Object`'s constructor function.
```js
var employee = new Object(); // Created employee object using new keywords and Object()
employee.name = 'Nishant';
employee.getName = function(){
	return this.name;
}
```
### Method 4: Using `Object.create`

`Object.create(obj)` will create a new object and set the `obj` as its prototype. It’s a modern way to create objects that inherit properties from other objects. `Object.create` function doesn’t run the constructor. You can use `Object.create(null)` when you don’t want your object to inherit the properties of `Object`.