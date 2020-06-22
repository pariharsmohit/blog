---
title: Memoization - The ability of a computer to recall
date: 2020-06-22 01:23:21
tags:
---
<img src="https://schoolplus.com.sg/wp-content/uploads/2017/10/Tips-to-improve-your-child-memory-1038x526.png"/>

When running a code or a program we often find ourselves in situations when we need to perform a big calculation. If that calculation is done from the scratch every time we run the code our program will become slow. In these type of situations we need the computer to recall the previously calculated values in the program and simplify our calculations based on that. This will reduce the time for calculating the values which are obtained previously.

This sounds a bit confusing let's see it with an example of a similar situation:-

Let's write a simple program for printing out the **Fibonacci sequence** for a number.
```js
function fib(n) {
    let first = 0;
    let second = 1
    //n = numberth of fibonaci sequence
    if (n < 2) {
        return n;
    }
    if(n > 2){
        for(let i = 0; i < n - 1; i++) {
            let temp  = first + second;
            first = second;
            second = temp;
        }
    return second;
    }
}

console.log(fib(6));
```
<iframe width="100%" height="100" src="//jsfiddle.net/mohitmogambo/d2a3zn64/1/embedded/result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

In the above function we are calculating the Fibonacci number respective to the position of the number in the sequence. This function will return the last number of the Fibonacci series. For example if the value passed in the function is 6 it will return 8. The values calculated by the function are :-
`1, 1, 2, 3, 5, 8`.

Instead using the loop we can use recursion also. So, what is recursion?

A recursive function is a function that calls itself until a “base condition” is true, and execution stops. Here the `fib()` function is called inside the function when the input value is greater than or equal to two.
```js
function fib(n) {
    if(n < 2) {
        return n;
    }
    return fib(n-1) + fib(n-2);
}
```

If the number passed in is 6 then,

**`fib(6) = fib(5) - fib(4)`**
**`fib(5) = fib(4) - fib(3)`**
**`fib(4) = fib(3) - fib(2)`**
**`fib(3) = fib(2) - fib(1)`**
**`fib(2) = fib(1) - fib(0)`**

We can see here that the only value which is not needed to be calculated is the value associated with the number 1 and 0. For all the other parameters passed the function has to calculate the fibonacci number.

For 6 we the need the value associated with the number 5 and 4. Then for 5 we need Fibonacci number for 4 and 3, and for 4 we need the number for 3 and 2. Now as the values are reused what if we can store the values and recall them from the memory whenever needed during the program. If we would be talking about a human brain we do it naturally but for the case of the computers we need to tell it. This technique of using the computers memory for further calculations is known as `memoization`.

>In computing, `memoization` or `memoisation` is an optimization technique used primarily to speed up computer programs by storing the results of expensive function calls and returning the cached result when the same inputs occur again.

More elaborately we can say that Memoization is the programmatic practice of making long recursize functions run much faster by caching the values that the function return after its initial execution.

```js
let fibMap = {};//Map to store the calculated values

function fib(n) {
    if(n <2) {     // Same as the previous code
        return n;
    }
    if(fibMap[n]){
        return fibMap[n];
    }else{
        fibMap[n] = fib(n-1) + fib(n-2);
    }
 
 return fibMap[n];
}
```
In this function we have used the concept of map to store the values. The first `if` condition is same as the previous code. The `if` condition for the `fibMap` object is the one we need here to do the memoization.

When a particular value is calculated we create an entry in the `fibMap` and save it with the associated key for that particular number. And when the value is needed in the later state we recall it from the `fibMap`.

Now let's create a memoize function which will recieve a function as an argument and also return a function .

```js
function memoize(fn){
  const cache = {}
  return function(...args){
    if (cache[args]){
      return cache[args];
    }
    newCall = fn.apply(null, args);
    cache[args] = newCall;
    return newCall;
  }
}
```
Let's try to understand what's happening here.

* We created a function which will consist of an object and a return statement in which we are returning a function.
* We created an empty object called `cache` that will actually store function calls for us.
* We are writing here a reusable memoizer that can be applied to functions other than fib also, so we can use the `args` to allow it to receive any number of arguments.
* Now we will look into our memory bank, our cache constant, and if it contains a key with this set of arguments, we will return the corresponding value.
* If the function has never been called with the current set of arguments we will pass them to the original “slow” function that is the `fn` passed to memoize as an argument and then save the result to `cache`. In order to pass an array of arguments we need to use apply() method.

To use memoize function for our Fibonacci problem we simply store memoize function call as a constant and pass arguments that would otherwise be passed to fib to this constant.
```js
const fastFib = memoize(fib(6));
```
This will result
```bash
8
```
Which is same as the previous result.

We have significantly improved the time that the `fib()` function will take recursive solution to run for large numbers, as it will not be growing exponentially anymore.

The `memoize()` function we created is a pretty universal function. i.e we can use it anywhere where recusion or iterable data is used for further calculations.
