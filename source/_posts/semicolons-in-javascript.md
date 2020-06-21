---
title: You don't need SEMICOLON in JAVASCRIPT 
date: 2020-04-03 22:47:01
tags:
---
***`Yes, It's true`***

### Because 

JavaScript **does not strictly require semicolons**. When there is a place where a semicolon was needed, it **adds it behind the scenes**.

### Automatic semicolon insertion

JavaScript parser will automatically **add a semicolon** when, during thr **parsing** of the source code, it finds these **particular situations** which are:-

1. when the next line starts with **code that breaks the current one**(code can spawn multiple lines)
2. when the **next line starts with a '}'**, closing the currenet block
3. when the **end** of the source code file is reached
4. when there is a **`return`** statement on its own line
5. when there is **`break`** statement on its own line
6. when there is a **`throw`** statement on its own line
7. when there is a **`continue`** statement on its own line.

### When not rely on this
**Consider the code**
```js
const a = 1
const b = 2
const c = a + b
(a + b).toString()
```
**OUTPUT:**
TypeError : b is not a function

JavaScript tries to interpret it as
```js
const a = 1
const b = 2
const c = a + b(a + b).toString()
```
**HENCE,**
b is understood as a function.

### SO, BE CAREFULL
- with **`return`** statements. If you return something, add it on the **same line** as the return(same for **`break, throw,continue`**)
- **never start a line with parentheses**, those might be concatenated with the previous line to form a function call, or array element reference.