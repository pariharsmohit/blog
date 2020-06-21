---
title: IIFE (Immediately Invoked Function Expression)
date: 2017-05-27 13:33:39
tags:
---
***`IIFE` is a function that runs as soon as it's defined.*** Usually it's anonymous (doesn't have a function name), but it also can be named.
Here's an example of IIFE:
``` js
(function() {
  console.log("Hi, I'm IIFE!");
})();
// outputs "Hi, I'm IIFE!"
```
### Explanation
So, here's how it works. Remember the difference between function statements`(function a () {})` and function expressions `(var a = function() {})`? So, IIFE is a function expression. To make it an expression we surround our function declaration into the parens. We do it to explicitly tell the parser that it's an expression, not a statement (JS doesn't allow statements in parens).

After the function you can see the two `()` braces, this is how we run the function we just declared.

That's it. The rest is details.

* The function inside IIFE doesn't have to be anonymous. This one will work perfectly fine and will help to detect your function in a stacktrace during debugging:
    ```js
    (function myIIFEFunc() {
    console.log("Hi, I'm IIFE!");
    })();
    // outputs "Hi, I'm IIFE!"
    ```
* It can take some parameters:
    ```js
    (function myIIFEFunc(param1) {
    console.log("Hi, I'm IIFE, " + param1);
    })("Yuri");
    // outputs "Hi, I'm IIFE, Yuri!"
    ```
    Here there value "Yuri" is passed to the param1 of the function.

* It can return a value:
    ```js
    var result = (function myIIFEFunc(param1) {
    console.log("Hi, I'm IIFE, " + param1);
    return 1;
    })("Yuri");
    // outputs "Hi, I'm IIFE, Yuri!"
    // result variable will contain 1
    ```
* You don't have to surround the function declaration into parens, although it's the most common way to define IIFE. Instead you can use any of the following forms:

    * `~function(){console.log("hi I'm IIFE")}()`
    * `!function(){console.log("hi I'm IIFE")}()`
    * `+function(){console.log("hi I'm IIFE")}()`
    * `-function(){console.log("hi I'm IIFE")}()`
    * `(function(){console.log("hi I'm IIFE")}());`
    * `var i = function(){console.log("hi I'm IIFE")}();`
    * `true && function(){ console.log("hi I'm IIFE") }();`
    * `0, function(){ console.log("hi I'm IIFE") }();`
    * `new function(){ console.log("hi I'm IIFE") }`
    * `new function(){ console.log("hi I'm IIFE") }()`

    Please don't use all these forms to impress colleagues, but be prepared that you can encounter them in someone's code.

### Applications and usefulness
Variables and functions that you declare inside an IIFE are not visible to the outside world, so you can:

* Use the IIFE for isolating parts of the code to hide details of implementation.
* Specify the input interface of your code by passing commonly used global objects (window, document, jQuery, etc.) IIFE’s parameters, and then reference these global objects within the IIFE via a local scope.
* Use it in closures, when you use closures in loops.
* IIFE is the basis of in the module pattern in ES5 code, it helps to prevent polluting the global scope and provide the module interface to the outside.