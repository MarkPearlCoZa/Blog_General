---
layout: post
title: C# Lambda and Predicate Basics
tags: 
category: General
---
Okay… don’t judge me… I have been coding in C# for a few years now and up till the point that I got into F# I never used lambda’s. This last week I realized just how much I am using the lambda expression in F# and thought it was about time I exposed myself to it in C#…

So first of all, the lambda expression in C# is symbolized by the =>. From what I understand it is really syntactical sugar over the C# language to anonymous delegates, which have been in the language for sometime. I am not going to go over anon delegates, but maybe look them up if you have not used them already…

The first scenario that I see the lambda expression being useful in is when designing methods that need to be flexible. For instance you develop some objects, and you want to perform all sorts of comparisons between instances of the objects. Up to recently I would do this by defining individual methods for each comparison.

For instance, see my contrived example to illustrate the point below…

Assume I had a secret number that wasn’t exposed to the developer and somehow I wanted to do all sorts of comparisons to it. Up till now I would have individual methods for all the comparisons…

class Program
   {
       private const int MySecretNumber = 100;

       private static bool CompareSecretNumberLessThanX(int x)
       {
           if (MySecretNumber < x)
           {
               return true;
           }
           return false;
       }

       private static bool CompareSecretNumberEqualToX(int x)
       {
           if (MySecretNumber == x)
           {
               return true;
           }
           return false;
       }        

       static void Main(string[] args)
       {
           CompareSecretNumberLessThanX(10);
           CompareSecretNumberEqualToX(100);            
           Console.ReadLine();
       }
   }
 

Now instead of taking this approach, we could rehash the code with the lambda expression and predicate type. Simply put, we would code a method that “compared” two things without knowing exactly what sort of comparison would be called. Then with the lambda expression we could explicitly state the type of compariosn.

class Program
{
    private const int MySecretNumber = 100;       

    private static bool CompareToSecretNumber(Predicate<int> aDelegate)
    {
        return aDelegate.Invoke(MySecretNumber);
    }


    static void Main(string[] args)
    {            
        CompareToSecretNumber(x => x < 10);
        CompareToSecretNumber(x => x == 100);
        Console.ReadLine();
    }
}

 

In effect what we have achieved here is to condense the CompareSecretNumberEqualToX & CompareSecretNumberLessThanX into one method, and also actually allowed for additional comparisons to be added without bloating the code at all.

So… while this post really hasn’t gone into to much detail or specifics I hope it at least shows one benefit of the lambda expression and the benefits of it.
