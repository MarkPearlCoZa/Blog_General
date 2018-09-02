---
layout: post
title: Euler Problem 20
tags: 
category: General
---
This was probably one of the easiest ones to complete – a quick bash got me the following…

The Problem
n! means n × (n − 1) × ... × 3 × 2 × 1

For example, 10! = 10 × 9 × ... × 3 × 2 × 1 = 3628800, 
and the sum of the digits in the number 10! is 3 + 6 + 2 + 8 + 8 + 0 + 0 = 27.

Find the sum of the digits in the number 100!

The Solution
 

private static BigInteger Factorial(int num)
{            
    if (num > 1) return (BigInteger)num * Factorial(num - 1);
    else return 1;
}

private static BigInteger SumDigits(string digits)
{
    BigInteger result = 0;
    foreach (char number in digits)
    {                
        result += Convert.ToInt32(number)-48;
    }
    return result;
}
static void Main(string[] args)
{            
    Console.WriteLine(SumDigits(Factorial(100).ToString()));
    Console.ReadLine();
}