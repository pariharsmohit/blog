---
title: Tower of Hanoi
date: 2020-03-29 15:01:47
tags:
---
The Tower of Hanoi is a mathematical game or puzzle. It consists of three rods and a number of disks of different sizes, which can slide onto any rod. The puzzle starts with the disks in a neat stack in ascending order of size on one rod, the smallest at the top, thus making a conical shape.
<img src="https://upload.wikimedia.org/wikipedia/commons/0/07/Tower_of_Hanoi.jpeg?download" style="float:center; margin: 0 auto;" />
The objective of the puzzle is to move the entire stack to another rod, obeying the following simple rules:

* Only one disk can be moved at a time.
* Each move consists of taking the upper disk from one of the stacks and placing it on top of another stack or on an empty rod.
* No larger disk may be placed on top of a smaller disk.

With 3 disks, the puzzle can be solved in 7 moves. The minimal number of moves required to solve a Tower of Hanoi puzzle is 2^n − 1, where n is the number of disks.

<img src="https://upload.wikimedia.org/wikipedia/commons/6/60/Tower_of_Hanoi_4.gif?download" style="float:center; margin: 0 auto;" />

For solving this we can consider each tower or rod as an array. Each disk can be represented as an array element and movement of the items is only provided from the end of the array hence making it behave like a stack.
```js
let A = [5,4,3,2,1]
let B = [];
let C = [];

function toh(s,t,h,n){
	if(!n) {
  	n = s.length;
  	}
	if( n > 2) {
  	toh(s,h,t,n-1);
    t.push(s.pop());
    toh(h,t,s,n-1);
  	} else {
  	h.push(s.pop());
  	t.push(s.pop());
  	t.push(h.pop());
  	} 
}

toh(A,B,C);

console.log(' A : ' + A);
console.log(' B : ' + B);
console.log(' C : ' + C);
```
output of this will be-
```bash
A : 
B : 5,4,3,2,1
C : 
```
In this code we can see that the logic for shifting two items from an array to other has been repeated again an again irrespective of the number of items in the array. So we can call the method to shift two items recursively.