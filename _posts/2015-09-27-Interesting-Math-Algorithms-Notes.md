---
layout: post
title: Interesting Math Algorithm for Programming Notes
tags: Useful
category: Misc
---

I recently have been spending a fair amount of time on [CodeWars](http://www.CodeWars.com)  

I doing many of the katas on the site I'm coming across interesing math problems. My mathematic skills are not great, so in an attempt to remember some of these things, I have collected the problems and solutions below:  

-------------------------------------------------------------------------------------------------

### Pronic Numbers ###

Pronic Number -A pronic number, oblong number, rectangular number or heteromecic number, is a number which is the product of two consecutive integers, that is, n(n + 1).

~~~
public class Kata
{
  public static bool IsPronic(int n)
  {
    return Math.Sqrt(1 + 4 * n) % 1 == 0;
  }
}
~~~

-------------------------------------------------------------------------------------------------

### Triangular, Polygonal Numbers ###

A Triangular number is the term for a factorial type operation, but with summation instead of products?

~~~
var triangular = (n*(n+1)) / 2;
~~~

[Triangular Numbers](https://en.wikipedia.org/wiki/Triangular_number)  
[Polygonal Numbers](https://en.wikipedia.org/wiki/Polygonal_number)  

-------------------------------------------------------------------------------------------------

### Triangle Inequality Theorem ###

Triangle Inequality Theorem, which states that the sum of two side lengths of a triangle is always greater than the third side. If this is true for all three combinations of added side lengths, then you will have a triangle.

-------------------------------------------------------------------------------------------------

### Permutations vs Combinations ###

Combinations if order DOES NOT matter.  
Permutations if order DOES matter.  

#### Permutations ####

2 Types:  
- Repetition is allowed (n^r times)    
- Repetition is NOT allowed (n! / (n - r)!)   

n^r  

Imagine you have a lock with 10 numbers on it from 0..9 and you have to choose 3 of them.  
10^3 = 1000 permutations  

n! / (n - r)!   

What order could 16 pool balls be in?  
- Our first choice has 16 possibilities.  
- Our second choice has 15 possibilities.  
- Our third choice has 14 possibilities.  
- etc.  

#### Combinations ####

2 Types:  
- Repetition is allowed  
- Repetition is NOT allowed  

##### When repetition is allowed: #####

(n + r - 1)! / r! (n - 1)! 

where n is the number of things to choose from, and we choose r of them.

##### When repetition is NOT allowed: #####

n! / (r! * (n - r)!)

where n is the number of things to choose from, and we choose r of them.

[Combinations and Permutations](https://www.mathsisfun.com/combinatorics/combinations-permutations.html)  
[Combination Calculator](https://www.mathsisfun.com/combinatorics/combinations-permutations-calculator.html)  

### Factorial ###

Calculating factorial can be done as follows in JavaScript...

~~~
const fact = (n) => {
   if (n === 0) return 1;
   if (n < 0 ) return undefined;
   for(var i = n; --i; ) {
       n *= i;
   }
   return n;
}
~~~

Or...

~~~
function factorial(n) {
  return n>=0 ? n ? n*factorial(n-1) : 1 : null;
}
~~~

### Sum of multiples ###

Sn = (n/2) * (a1 + an) 

Sn = the sum of the n terms in the sequence.
n = number of terms in the sequence
a1 = the first term in the sequence.
an = the nth term in the sequence. 

### Calculating the nth root of a number  ###

Get the nth root of a number using JavaScript  

Use the following: 

~~~
Math.pow(n, 1/root);
~~~

e.g.

~~~
Math.pow(25, 1/2) == 5
~~~

[StackOverflow Discussion](http://stackoverflow.com/questions/7308627/javascript-calculate-the-nth-root-of-a-number)  

-------------------------------------------------------------------------------------------------

### Calculating Prime ###

When calculating primes you do not need to traverse every single number. You only need to check up to the sqrt of a number.

~~~
function isPrime(x) {
  let xSqrt = Math.sqrt(x);
  if (x < 2) return false;
  if (x === 2) return true;

  for(let i = 3; i <= xSqrt; i++) {
    if(x % i === 0) return false;
  }

  return true;
}
~~~

-------------------------------------------------------------------------------------------------

#### Lowest Common Denominator / Greatest Common Denominator ####

~~~
var gcd = function(a, b) {
    if ( ! b) {
        return a;
    }
 
    return gcd(b, a % b);
};
~~~

------------------------------------------------------------------------------------------------

#### Calculate Square Root ####

Using Newton's Formula - [see more](https://en.wikipedia.org/wiki/Newton%27s_method#Square_root_of_a_number)  

~~~
function squareRoot(n) {
	let curSqrtApprox = guess(n);
  
  do {
    let prevSqrtApprox = curSqrtApprox;
		curSqrtApprox = newtonApprox(curSqrtApprox, n);  	
    if (curSqrtApprox === prevSqrtApprox) return curSqrtApprox;
    
  } while (0 !== 1)
}

const adjustPrecision = (x) => Number(x.toFixed(5));
const newtonApprox = (x, ori) => adjustPrecision(x - (sqrfun(x, ori) / derivative(x)));
const sqrfun = (x, ori) => (x * x) - ori;
const derivative = (x) => 2 * x;
const guess = (x) => x / 2;
~~~

Another approach...

~~~
const squareRoot = x => +((Math.cos(Math.asin((((x+1)/2)-1)/((x+1)/2)))*((x+1)/2)).toFixed(5))
~~~
