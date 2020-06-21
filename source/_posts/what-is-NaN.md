---
title: What is NaN, why do we need it, and when can it break the page?
date: 2017-09-16 13:23:37
tags:
---
**`NaN`** stands for *“not a number”* and it can break your table of numbers when it has an arithmetic operation that is not allowed. Here are some examples of how you can get **`NaN`**:

```js
Math.sqrt(-5);
Math.log(-1);
parseFloat("foo"); /* this is common: you get JSON from the server, convert some strings from JSON to a number and end up with NaN in your UI. */
```
**`NaN`** is not equal to any number, it’s not less or more than any number, also it's not equal to itself:

```js
NaN !== NaN
NaN < 2 // false
NaN > 2 // false
NaN === 2 // false
```

To check if the current value of the variable is **`NaN`**, you have to use the ***`isNaN`*** function. This is why we can often see NaN in the webpages: it requires special check which a lot of developers forget to do.