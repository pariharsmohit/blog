---
title: Cloning an Object
date: 2019-05-11 23:25:50
tags:
---
Here we are going to create a function which will clone or copy an object to another object.

If the Object only contains primitive value such as **`strings`**, **`numbers`**, **`booleans`** etc. We can use the function ***`Object.assign()`***. 

***`Object.assign()`*** function takes two arguments -
1. new object which is going to be generated
2. source object from which the data is to be copied.

Example:- 
```js
let swift = {
    brand: 'Maruti',
    fuel: 'petrol',
    doors: 4,
    type: 'hatchback'
};

let baleno = {};

Object.assign(baleno, swift);

baleno.type = 'premium hatchback';

console.log(baleno, swift);
```
This results in:-
```js
{brand: "Maruti", fuel: "petrol", doors: 4, type: "hatchback"}
{brand: "Maruti", fuel: "petrol", doors: 4, type: "premium hatchback"}
```
This solution does not allows us to peform deep cloning. *Deep Cloning* stands for copying the object which contains objects inside it as its properties.
For that purpose we can use ***`JSON.parse(JSON.stringify(source_object))`***. This method first converts the whole `source-object` into a string and then parse(resolve into its component parts) it to another object.

Apart from doing the above two we can simply create our own function that will do the same using the recursion.
For Example:-
```js
let bmw = {
  model: 'x4',
  fuel: 'petrol',
  engine: {
  	type: 'v6'
  }
}

let car = {};

function clone(src){
    let result = {};
    let keys = Object.keys(src);
    //['model', 'fuel', 'engine'];
    keys.forEach(key => {
        if(typeof src[key] === "object") {
            result[key] = clone(src[key]);
        }else {
            result[key] = src[key];
        }
    })
  return result;
}

car = clone(bmw);

car.fuel = 'disel';
car.engine.type='v8';

console.log(car,bmw);
```
This results in-
```js
{model: "x4", fuel: "disel", engine: {type: "v8"}}
{model: "x4", fuel: "petrol", engine: {type: "v6"}}
```
In this we are providing an **`if statement`** which compares the keys inside the object and if the key returns value equal to the `object` we will call the same function again, but this time inside the conditional statement.