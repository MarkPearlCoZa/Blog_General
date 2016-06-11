---
layout: post
title: Clever Code
tags: Code
category: Misc
---

### Javascript ###

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

#### Replace every word not matching a pattern using Regex and JS ####

~~~
function rakeGarden(garden) {
  return garden.replace(/\w+/g,function(v){if(v!=='rock')v='gravel';return v;});
}
~~~


#### Make sure that every letter in a word is unique using Regex and JS ####

~~~
function isIsogram(str){ 
  return !/(\w).*\1/i.test(str)
}
~~~

#### Checking for Palindrome ####

~~~
const isPalindrome = (str) => str === reverse(str);
 
const reverse = (str) => str.toString().split('').reverse().join('');
~~~

### C# ###
