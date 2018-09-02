---
layout: post
title: Project Euler Problem 14
tags: 
category: General
---
 

The Problem
The following iterative sequence is defined for the set of positive integers:

n → n/2 (n is even) 
n → 3n + 1 (n is odd)

Using the rule above and starting with 13, we generate the following sequence:

13 → 40 → 20 → 10 → 5 → 16 → 8 → 4 → 2 → 1

It can be seen that this sequence (starting at 13 and finishing at 1) contains 10 terms. Although it has not been proved yet (Collatz Problem), it is thought that all starting numbers finish at 1.

Which starting number, under one million, produces the longest chain?

NOTE: Once the chain starts the terms are allowed to go above one million.

The Solution
 

public static long NextResultOdd(long n)
{
    return (3 * n) + 1;
}

public static long NextResultEven(long n)
{
    return n / 2;
}

public static long TraverseSequence(long n)
{
    long x = n;
    long count = 1;
    while (x > 1)
    {
        if (x % 2 == 0) x = NextResultEven(x); else x = NextResultOdd(x);
        count++;
    }
    return count;
}


static void Main(string[] args)
{
    long largest = 0;
    long pos = 0;

    for (long i = 1000000; i > 1; i--)
    {
        long temp = TraverseSequence(i);
        if (temp > largest)
        {
            largest = temp;
            pos = i;
        }
    }
    Console.WriteLine("{0} - {1}", pos, largest);
    Console.ReadLine();
}