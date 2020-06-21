---
title: Copy text to clipboard
date: 2019-04-13 18:42:26
tags:
---
We are going to copy the text from the text input in the HTML page and we want to do that on the click of a button.

```js
<input type="text" value="Hello World" id="myInput">

<button onclick="myFunction()">Copy text</button>
```
Now the function definition will look like this:-
```js
function myFunction() {
  let copyText = document.getElementById("myInput");
  copyText.select();
  document.execCommand("copy");
  alert("Copied the text: " + copyText.value);
}
```
We can test this code here
<iframe width="100%" height="100" src="//jsfiddle.net/mohitmogambo/5pf6ec1u/4/embedded/result/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="1"></iframe>