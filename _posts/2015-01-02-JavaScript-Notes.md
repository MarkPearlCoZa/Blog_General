---
layout: post
title: JavaScript Notes
tags: Web
category: Tech
---
## Contents  

- [Collections](#collections)  
  - [Arrays](#arrays)  
  - [Sets](#sets)  
- [Nulls](#nulls)  
- [Strings](#strings)  
- [Numbers](#numbers)  
- [Closures](#closures)  
- [Regex](#regex)  
- [Object Oriented JavaScript](#object-oriented-javascript)  
- [Json Objects](#json-objects)  
- [Scope](#scope)  
- [Misc](#misc)  

## Collections 

### Array's 

#### Creating Arrays

**Creating an Array Seeded with a Value**

~~~
let size = 10;
let initialValue = "blah";
new Array(size).join(initialValue);
~~~

Another approach for creating an array and populating it with values 1 to 10...

~~~
Array.from({length:n}, (_,i)=>i+1)
~~~

Or...

~~~
[...Array(n)].map((_, i) => i+1);
~~~

Some other ways to generate prepopulated arrays...

~~~
let pipeFix = nums => Array.from({ length: nums.pop() - nums[0] + 1 }, (v, i) => i + nums[0]);
~~~

~~~
[...Array(max - min + 1)].map((v, i) => i + min);
~~~

~~~
((min,max) => Array.from(Array(max-min+1),(_,i) => min + i))(Math.min(...nums), Math.max(...nums))
~~~

**Creating Arrays from strings**  

Using split operator...

~~~
let a = 'this is a string';
a.split('').map(c=> console.log(c));
~~~

Using spread operator...

~~~
let a = 'this is a string';
[...a].map(c => console.log(c));
~~~

**Creating Array with unique values**

~~~
let a = [1, 2, 3, 2, 2, 1, 3];
let uniqueA = [...new Set(a)];
~~~

#### Maniuplating Arrays

 unshift -> array <- push  
   shift <- array -> pop  

#### Sorting Arrays

An example of sorting values/numbers in an array

~~~
function isTriangle(a,b,c)
{
  [a, b, c] = [a, b, c].sort((x, y) => x-y);
  
  return a+b > c;
}
~~~

#### Validating Arrays

**Checking if all elements in an array match a criteria**

Checks if all elements are numbers  

~~~
  if (arr.some(x => typeof x != "number")) return "Not all numbers";
~~~

-------------------------------------------------------------------------------------------

### Sets

The Set object lets you store unique values of any type.

~~~
let unique = new Set(['a','a','b','b','c','c']); // a, b, c
~~~

Getting values from a set...

~~~
console.log(set.Values());
~~~

[More info on Sets](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Set)  

-------------------------------------------------------------------------------------------

### Nulls 

#### Checking for Null Values ####

Use the || to return a default value if the first value is null. **Remember null is falsey.**

Falsey values: null, undefined, false, empty string or 0

~~~
const lowercaseCount = str => (str.match(/[a-z]/g) || []).length;
~~~

-------------------------------------------------------------------------------------------

### Strings ###

#### String Functions ####

[slice](http://www.w3schools.com/jsref/jsref_slice_array.asp)  
[split](http://www.w3schools.com/jsref/jsref_split.asp)  
[join](http://www.w3schools.com/jsref/jsref_join.asp)  
[substr](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substr)  

#### String Interpolation ####

~~~
let value = "Blah";
console.log(`Hello ${value}!`);
~~~

#### Checking for null, empty strings ####

Remember, an empty string is falsey.  
Remember, !undefined is truthy.

So you can do something like this...

~~~
if (!a) {
  // is emtpy & not null
}
~~~

-------------------------------------------------------------------------------------------

### Numbers 

#### Check is number is odd

Using modula...  

~~~
let isOdd = !(n % 2);
~~~

or using bitwise checking...  

~~~
let isOdd = (n & 1);
~~~

#### Check if a number is a whole number / integer  

~~~
function isWholeNumber(n){
    return Number(n) === n && n % 1 === 0;
}
~~~

#### Check if a value is a finite number ####

~~~
isFinite(testValue);
~~~

#### Squaring Number Syntax

The below code square c to the power of 2

~~~
c ** 2
~~~

#### Performant way to check if number is odd

~~~
let number = 123;
(number & 1)i ? console.log('is odd') : console.log('is even');
~~~

[Read more](http://stackoverflow.com/questions/6572670/other-ways-of-performing-modulo-operation)  

#### Fast Math.Floor

That ~~ is a double NOT bitwise operator.

It is used as a faster substitute for Math.floor().

#### Check if value is a number ####

~~~
function isANumber(value) {
  return (value instanceof Number||typeof value === 'number') && !isNaN(value);
}
~~~

#### Recognizing Integers 

~~~
Number.isInteger(n)
~~~

or 

~~~
if (data === parseInt(data, 10)) { ... }
~~~

#### Rounding 

Rounding to certain decimal places  

~~~
const roundTo = (n, decimal) => (Math.round(n * Math.pow(10,decimal)) * Math.pow(10,-decimal)).toFixed(decimal);
~~~

-------------------------------------------------------------------------------------------

### Map & Reduce 

[Explanation of Map/Reduce](https://hacks.mozilla.org/2015/01/from-mapreduce-to-javascript-functional-programming/)  

-------------------------------------------------------------------------------------------

### Closures 

Closures are functions that refer to independent (free) variables. In other words, the function defined in the closure 'remembers' the environment in which it was created.

Below is an example of a closures. A 

~~~
function buildFun(n){
  var result  = []

  for (let i = 0; i< n; i++) {
    var closure = function() {
      return i;               
    };
   
   result.push(closure);
  }
 
  return result;
}
~~~

[Read more](https://developer.mozilla.org/en/docs/Web/JavaScript/Closures)  

-------------------------------------------------------------------------------------------

### RegEx 


Using RegExp
 
~~~
"This is a string value".match(new RegExp(key,'gi'));
~~~

-------------------------------------------------------------------------------------------

### Object Oriented JavaScript ###

#### Class Declarations

~~~
class ExampleCalss {
  constructor(param1, param2) {
   this.someValue = param1;
   // ... do something
  }

  get propertyX() {
    return this.someValue;
  }  

  set propertyX(val) {
    this.someValue = val; 
  }
}
~~~

#### Duck Typing

Checking that an object has the following function methods on it...

- sayHoHoHo
- distributeGifts  
- goDownTheChimney  

~~~
function isSantaClausable(obj) {
  return ['sayHoHoHo', 'distributeGifts', 'goDownTheChimney'].every(function(methodName) {
    return typeof obj[methodName] == 'function';
  });
}
~~~

[Read more on Duck Typing in JavaScript](https://en.wikipedia.org/wiki/Duck_typing#In_JavaScript)  

#### Functions of Objects / Properties

Checking if a function is attached to an object

~~~
var megalomaniac = {
	mastermind: "James Wood",
	henchman: "Adam West",
	birthYear: 1970,
        theBomb: true
};


var functionThatExists = "theBomb" in megalomaniac; 		// Returns True
var functionThatDoesNotExist = "notTheBomb" in megalomaniac; 	// Returns False
~~~

Attaching a function to an existing object...  

~~~
var megalomaniac = { mastermind : "Agent Smith", henchman: "Agent Smith" };
expect("secretary" in megalomaniac).toBe(false);

megalomaniac.secretary = "Agent Smith";
expect("secretary" in megalomaniac).toBe(true);
~~~

Deleting a function from an object...  

~~~
var megalomaniac = { mastermind : "Agent Smith", henchman: "Agent Smith" };
expect("mastermind" in megalomaniac).toBe(true);

delete megalomaniac.mastermind;
expect("mastermind" in megalomaniac).toBe(false);
~~~

#### Inheritance

~~~
function Circle(radius)
{
	this.radius = radius;
}

var simpleCircle = new Circle(10);
var colouredCircle = new Circle(5);


Circle.prototype.describe = function () {
	return "This circle has a radius of: " + this.radius;
};
~~~

-------------------------------------------------------------------------------------------

### Json Objects

#### Check if key is in Json Object 

~~~
let person = { name : "Mark", surname : "Pearl"}

If ('propertyName' in person) ...
~~~

#### Parse through each key in Json Object 

~~~
for (let key in object) {
  console.log("key is " + key);
  console.log("value is " + object[key]);
}
~~~

-------------------------------------------------------------------------------------------

### Scope 

- Global Scope  
- Local Scope  
- Function Scope  
- Lexical Scope  
- Scope Chain  
- Closures  

[Everything you wanted to know about javascript scope](https://toddmotto.com/everything-you-wanted-to-know-about-javascript-scope/)  

-------------------------------------------------------------------------------------------

### Misc 

#### Easy way to Run JavaScript ####

Create a html file called program.html with the following content.

~~~
<html>
  <body>
    <pre>
      <script src="program.js">
      </script>
    </pre>
  </body>
</html>
~~~

Create a javacript file called program.js with the following content.

~~~
document.writeln("Hello World");
~~~

#### Resetting a prototype override ####

~~~
Array.prototype.join = Array.prototype._join;
~~~

#### Method Parameters ####

The following is allowed in method signatures...  

~~~
const lengthOfLine = ([[x1,y1],[x2,y2]]) => (x1 - x2) * (y1 - y2)
~~~

#### Iterators ####

[Read more on iterators](http://exploringjs.com/es6/ch_iteration.html)  

#### References ####

[Useful Methods for Strings]("http://www.impressivewebs.com/javascript-string-methods-reference/")  
[Special Characters and Escape Sequences]("http://www.javascriptkit.com/jsref/escapesequence.shtml")  
[File Organization with HTML, CSS, and JavaScript Files]("http://appcropolis.com/blog/web-technology/organize-html-css-javascript-files/")  
[Eloquent Javascript]("http://eloquentjavascript.net/")  
[Mozilla Development Network Javascript]("https://developer.mozilla.org/en-US/docs/Web/JavaScript")  
[JSFiddle]("http://jsfiddle.net/")  
[DailyJS]("http://dailyjs.com/")  


[Closures at the MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Closures)
[Prototypes at "Javascript, Javascript...](http://javascriptweblog.wordpress.com/2010/06/07/understanding-javascript-prototypes/)
[OOP at Eloquent Javascript](http://eloquentjavascript.net/chapter8.html)
