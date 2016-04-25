---
layout: post
title: JavaScript Notes
tags: Web
category: Tech
---
#### Resetting a prototype override ####

~~~
Array.prototype.join = Array.prototype._join;
~~~

#### Check if value is a number ####

~~~
function isANumber(value) {
  return (value instanceof Number||typeof value === 'number') && !isNaN(value);
}
~~~

#### Creating an array of a size with a certain value ####

~~~
let size = 10;
let initialValue = "blah";

new Array(size).join(initialValue);
~~~

#### Checking for Null Values ####

Use the || to return a default value if the first value is null.
Remember null is falsey.

Falsey values: null, undefined, false, empty string or 0

~~~
const lowercaseCount = str => (str.match(/[a-z]/g) || []).length;
~~~

#### Checking for empty strings ####

Remember, an empty string is falsey - so you can do something like this...

~~~
if (!a) {
  // is emtpy
}
~~~

#### Generating Collections ####

Some ways to generate prepopulated collections...

~~~
let pipeFix = nums => Array.from({ length: nums.pop() - nums[0] + 1 }, (v, i) => i + nums[0]);
~~~

~~~
[...Array(max - min + 1)].map((v, i) => i + min);
~~~

~~~
((min,max) => Array.from(Array(max-min+1),(_,i) => min + i))(Math.min(...nums), Math.max(...nums))
~~~

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

Create a javacrip file called program.js with the following content.

~~~
document.writeln("Hello World");
~~~

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

#### Map & Reduce ####

[Explanation of Map/Reduce](https://hacks.mozilla.org/2015/01/from-mapreduce-to-javascript-functional-programming/)  

#### Recognizing Integers #### 

~~~
Number.isInteger(n)
~~~

or 

~~~
if (data === parseInt(data, 10)) { ... }
~~~

#### Closures ####

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

#### Check if key is in Json Object ####

~~~
let person = { name : "Mark", surname : "Pearl"}

If ('propertyName' in person) ...
~~~

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
