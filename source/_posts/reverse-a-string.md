---
title: Reverse a string the JavaScript way
date: 2018-05-07 22:26:42
tags:
---
We need to take the string and reverse it, so if it originally reads ‘hello’, it will now read ‘olleh’.
```js
function reverseString(str) {
  for (var reversedStr = "", i = str.length - 1; i >= 0; i--) {
    reversedStr += str[i];
  }
  return reversedStr;
}
```
* Starting at the last character of the string passed to the function, we build a new string reversedStr from str.

* During each iteration of the for loop, reversedStr gets concatenated with itself and the current character.

* Finally, we return the final value of reversedStr.

### We can do this finally by using the JavaScript functions like this-
```js
function reverseString(str) {
  return str
    .split("")
    .reverse()
    .join("");
}
```
for example:-
```js
reverseString("Greetings from Earth");
```
this will return
```js
"htraE morf sgniteerG"
```
* Our goal is to take the input, `str`, and return it in reverse. Our first step is to split the string by characters using `split('')`. Notice that we don’t leave anything in between the single quotes, this tells the function to split the string by each character.

* Using the `split()` function will turn our string into an array of characters, keep that in mind as we move forward.

* Next we chain the `reverse()` function, which takes our array of characters and reverses them.

* Finally, we chain `join('')` to put our characters back together into a string. Notice once again that we left no spaces in the argument for join, this makes sure that the array of characters is joined back together by each character.
