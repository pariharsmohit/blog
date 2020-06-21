---
title: What are promises and how they are useful?
date: 2017-07-10 17:44:14
tags:
---
***`A promise represents the value that is unknown now that may become known in future. In other words a asynchronous value.`***

We use promises for handling asynchronous interactions in a sequential manner. They are especially useful when we need to do an async operation and THEN do another async operation based on the results of the first one. For example, if you want to request the list of all flights and then for each flight you want to request some details about it. The promise represents the future value. It has an internal state (pending, fulfilled and rejected) and works like a state machine.

A promise object has then method, where you can specify what to do when the promise is fulfilled or rejected.

### How Promises Work

A promise is an object which can be returned synchronously from an asynchronous function. It will be in one of 3 possible states:

* Fulfilled: `onFulfilled()` will be called (e.g., `resolve()` was called)
* Rejected: `onRejected()` will be called (e.g., `reject()` was called)
* Pending: not yet fulfilled or rejected

A promise is **settled** if it’s not pending (it has been resolved or rejected). Sometimes people use *resolved* and *settled* to mean the same thing: *not pending*.

Once settled, a promise can not be resettled. Calling `resolve()` or `reject()` again will have no effect. The immutability of a settled promise is an important feature.

Native JavaScript promises don’t expose promise states. Instead, you’re expected to treat the promise as a black box. Only the function responsible for creating the promise will have knowledge of the promise status, or access to resolve or reject.

Here is a function that returns a promise which will resolve after a specified time delay:

```js
const wait = time => new Promise((resolve) => setTimeout(resolve, time));

wait(3000).then(() => console.log('Hello!')); //'Hello!'
```
Our `wait(3000)` call will wait 3000ms (3 seconds), and then log `'Hello!'`. All spec-compatible promises define a `.then()` method which you use to pass handlers which can take the resolved or rejected value.

The ES6 promise constructor takes a function. That function takes two parameters, `resolve()`, and `reject()`. In the example above, we’re only using `resolve()`, so I left `reject()` off the parameter list. Then we call `setTimeout()` to create the delay, and call `resolve()` when it’s finished.

You can optionally `resolve()` or `reject()` with values, which will be passed to the callback functions attached with `.then()`.

When I `reject()` with a value, I always pass an `Error` object. Generally I want two possible resolution states: the normal happy path, or an exception — anything that stops the normal happy path from happening. Passing an `Error` object makes that explicit.

You can chain `then()` blocks, thus avoiding the callback hell. You can handle errors in the `catch()` block. After a promise is set to fulfilled or rejected state, it becomes immutable.