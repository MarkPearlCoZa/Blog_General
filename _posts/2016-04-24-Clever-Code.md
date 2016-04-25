---
layout: post
title: Clever Code
tags: Code
category: Misc
---

#### Get the last digit of a number ####

~~~
let number = 123
let lastDigit = number % 10; // return 3
let lastTwoDigits = number % 100 //return 23
~~~

#### Inserting dashes between odd and even numbers ####

~~~
function insertDashII(num) {
  return String(num)
    .replace(/([13579])(?=[13579])/g, "$1-")
    .replace(/([2468])(?=[2468])/g, "$1*")
}
~~~

