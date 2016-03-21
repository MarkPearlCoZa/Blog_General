---
layout: post
title: Interesting Math Algorithm Notes
tags: Useful
category: Notes
---

I recently have been spending a fair amount of time on [CodeWars](http://www.CodeWars.com)  

I doing many of the katas on the site I'm coming across interesing math problems. My mathematic skills are not great, so in an attempt to remember some of these things, I have collected the problems and solutions below:  

#### Pronic Numbers ####

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

#### Triangular, Polygonal Numbers ####

A Triangular number is the term for a factorial type operation, but with summation instead of products?

~~~
var triangular = (n*(n+1)) / 2;
~~~

[Triangular Numbers](https://en.wikipedia.org/wiki/Triangular_number)  
[Polygonal Numbers](https://en.wikipedia.org/wiki/Polygonal_number)  

#### Permutations vs Combinations ####

Combinations if order DOES NOT matter.  
Permutations if order DOES matter.  

##### Permutations #####

2 Types:
- Repetition is allowed (n^r times)    
- Repetition is NOT allowed (n! / (n - r)!)   

n^r =   
imagine you have a lock with 10 numbers on it from 0..9 and you have to choose 3 of them.  
10^3 = 1000 permutations  

n! / (n - r)! =  
what order could 16 pool balls be in?
Our first choice has 16 possibilities.  
our second choice has 15 possibilities.  
our third choice has 14 possibilities.
etc.

##### Combinations #####

[Combinations and Permutations](https://www.mathsisfun.com/combinatorics/combinations-permutations.html)  

#### Calculating the nth root of a number  ####

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

#### Calculating Prime ####

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

#### Lowest Common Denominator / Greatest Common Denominator ####

~~~
var gcd = function(a, b) {
    if ( ! b) {
        return a;
    }
 
    return gcd(b, a % b);
};
~~~
