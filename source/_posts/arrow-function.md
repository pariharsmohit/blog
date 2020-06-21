---
title: Arrow Functions => When to use and when not to?
date: 2019-03-13 13:26:40
tags:
---
<img src="https://raw.githubusercontent.com/mohitsparihar/massets/master/arrow-function.svg" style="float:center; margin: 0 auto;" />

## ES6 Arrow Functions

Introduced as part of the ECMAScript 6, arrow functions went viral. The new syntax to declare functions is wonderful, saving us time and enhancing clarity in many situations, removing all the distracting, unnecessary, chunk that usually came with declaring a JS function.

Let’s take an example of a regular function declaration, and the same function using arrow functions:
```js
function welcome() {
  return "Welcome!"
}
```
And with ES6 Arrow Functions
```js
const welcome = () => "Welcome!"
```
Let’s look at another example:
```js
const f = list.map(function(item) { return item; })
```
vs
```js
const f = list.map((item) => item)
```
Ain’t that beautiful?

However, we need to be careful, as the differences between the 2 declarations are not just syntax, and thus it cannot be applied in every situation. Let’s now take a look at situations under which using Arrow Functions is not the right way.

## Object Methods
Take a look at the following example:
```js
const article = {
  claps: 0,
  clap: () => {
    this.claps++;
  }
}
```
In this example, it would be intuitive to think that every time we call `article.clap()` the attribute `article.claps` would increase by one, initially from 0 to 1. However, this is not the case, the value of claps will sadly remain the same and this article will never get to be popular.

>## As  MDN states:

>An arrow function expression is a syntactically compact alternative to a regular function expression, although without its own bindings to the this, arguments, super, or new.target keywords. Arrow function expressions are ill suited as methods, and they cannot be used as constructors.

meaning that in our case, the enclosed scope would be the **`window`** object. Invoking the method `clap()` would simply attempt to increment the property claps on the window object.

However, if instead, we use the traditional syntax:
```js
const article = {
  claps: 0,
  clap: function() {
    this.claps++;
  }
}
```
Live Example:
<iframe width="100%" height="300" src="//jsfiddle.net/mohitmogambo/5rb3q20y/3/embedded/result,js,html/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

## Object Prototype

Similar to the example above, object prototypes will evaluate this as the window object, like in the following example:
```js
class Article {
  constructor(title) {
    this.title = title;
    this.shared = false;
  }
};

Article.prototype.share = () => {
  return this.shared = true;
};
```
Similarly, to the previous case the method `share()` won’t work due to the enclosed scope to the window object. And again the solution will look familiar:
```js
Article.prototype.share2 = function() {
  return this.shared = true;
};
```
Live Example:
<iframe width="100%" height="300" src="//jsfiddle.net/mohitmogambo/5rb3q20y/1/embedded/result,js,html/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

## Callback functions with dynamic context

In the next example we will take a look at the dynamic context in callbacks, like those in events:
```js
var button = document.getElementById('press');
button.addEventListener('click', () => {
  this.classList.toggle('worked');
});
```
Again the similarities with previous examples are obvious, same as before the enclosed scope is affecting the meaning of this.

Live Example:
<iframe width="100%" height="300" src="//jsfiddle.net/mohitmogambo/5rb3q20y/6/embedded/result,js,html/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

A way to workaround a solution is to use an arrow function and use the event object to access the object in that function, however, this does not solve the enclosing of the scope, but it does work for this particular example
```js
var button = document.getElementById('press');
button.addEventListener('click', (e) => {
  e.target.classList.toggle('worked');
});
```
## Makes the code less readable

Sometimes the use of arrow functions will make the code unreadable, not very likely but can happen, don’t use them then. The idea behind it is to make our code clearer, so make sure it stays that way.