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

#### Replace every word not matching a pattern ####

~~~
function rakeGarden(garden) {
  return garden.replace(/\w+/g,function(v){if(v!=='rock')v='gravel';return v;});
}
~~~


#### Make sure that every letter in a word is unique ####

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

#### Handling Pricing Combinations / Steps  ####

The cost of deliveries is:

$3.85 for 40 newspapers
$1.93 for 20
$0.97 for 10
$0.49 for 5
$0.10 for 1

Write a function that's passed an integer representing the amount of newspapers and returns the cheapest price. 

~~~
const cheapestQuote = newspapers => {
  let total = 0;
  
  total += Math.floor(newspapers/40) * 3.85;
  newspapers %= 40;
  
  total += Math.floor(newspapers/20) * 1.93;
  newspapers %= 20;
  
  total += Math.floor(newspapers/10) * 0.97;
  newspapers %= 10;
  
  total += Math.floor(newspapers/5) * 0.49;
  newspapers %= 5;
 
  total += newspapers * 0.1;

  return total;
};
~~~

#### Using Regex format numbers as follows

addCommas("$123",regex) should return "$123"
addCommas("$1234",regex) should return "$1,234"
addCommas("$12345",regex) should return "$12,345"
addCommas("$1234567",regex) should return "$1,234,567"
addCommas("$123456789",regex) should return "$123,456,789"

~~~
var regex=/\d(?=(\d{3})+$)/g

const addCommas = (money,reg) => {
  return money.replace(reg,x=>x+",")  //like this
}
~~~

#### Check to see if a string is a natural number

~~~
const isInteger = (txt) => (/^-?\d+$/).test(txt);
~~~

-------------------------------------------------------------------------------

### Ruby

#### Getting value from a hash?

~~~
def what_is(x)
    matches = {
        42 => 'everything',
        1  => 'one'
    }

    matches.default = 'nothing'
    matches[x]
end
~~~

#### Get the first alphabetical word from an array

~~~
def getFirstWord(words)
    words.min
end
~~~
