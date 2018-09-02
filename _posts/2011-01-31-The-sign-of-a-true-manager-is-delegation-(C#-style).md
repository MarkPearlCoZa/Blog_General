---
layout: post
title: The sign of a true manager is delegation (C# style)
tags: 
category: General
---
Today I thought I would write a bit about delegates in C#. Up till recently I have managed to side step any real understanding of what delegates do and why they are useful – I mean, I know roughly what they do and have used them a lot, but I have never really got down dirty with them and mucked about. Recently however with my renewed interest in Silverlight delegates came up again as a possible solution to a particular problem, and suddenly I found myself opening a bland little console application to just see exactly how far I could take delegates with my limited knowledge.

So, let’s first look at the MSDN definition of delegates…

A delegate declaration defines a reference type that can be used to encapsulate a method with a specific signature. A delegate instance encapsulates a static or an instance method. Delegates are roughly similar to function pointers in C++; however, delegates are type-safe and secure.

Well, don’t you love MSDN for such a useful definition. I must give it credit though… later on it really explains it a bit better by saying “A delegate lets you pass a function as a parameter. The type safety of delegates requires the function you pass as a delegate to have the same signature as the delegate declaration.”

A little more reading up on delegates mentions that delegates are similar to interfaces in that they enable the separation of specification and implementation. A delegate declares a single method, while an interface declares a group of methods.

So enough reading - lets look at some code and see a basic example of a delegate… Let’s assume we have a console application with a simple delegate declared called AdjustValue like below…

    class Program
    {
        private delegate int AdjustValue(int val);

        static void Main(string[] args)
        {
        }
    }
In a sense, all we have said is that we will be creating one or more methods that follow the same pattern as AdjustValue – i.e. they will take one input value of type int and return an integer. We could then expand our code to have various methods that match the structure of our delegate AdjustValue (remember the structure is int xxx (int xxx))

    class Program
    {
        private delegate int AdjustValue(int val);

        private static int Dbl(int val)
        {
            return val * 2;
        }

        private static int AlwaysOne(int val)
        {
            return 1;
        }

        static void Main(string[] args)
        {
        }
    }
 
Above I have expanded my project to have two methods, one called Dbl and the other AlwaysOne. Dbl always returns double the input val and AlwaysOne always returns 1. I could now declare a variable and assign it to be one of those functions, like the following…

    class Program
    {
        private delegate int AdjustValue(int val);

        private static int Dbl(int val)
        {
            return val * 2;
        }

        private static int AlwaysOne(int val)
        {
            return 1;
        }

        static void Main(string[] args)
        {
            AdjustValue myDelegate;
            myDelegate = Dbl;
            Console.WriteLine(myDelegate(1).ToString());
            Console.ReadLine();
        }
    }
In this instance I have declared an instance of the AdjustValue delegate called myDelegate; I have then told myDelegate to point to the method Dbl, and then called myDelegate(1). What would the result be? Yes, in this instance it would be exactly the same as me calling the following code…

        static void Main(string[] args)
        {            
            Console.WriteLine(Dbl(1).ToString());
            Console.ReadLine();
        }
 

So why all the extra work for delegates when we could just do what we did above and call the method directly? Well… that separation of specification to implementation comes to mind. So, this all seems pretty simple. Let’s take a slightly more complicated variation to the console application. Assume that my project is the same as the one previously except that my main method is adjusted as follows…

        static void Main(string[] args)
        {
            AdjustValue myDelegate;
            myDelegate = Dbl;
            myDelegate = AlwaysOne;
            Console.WriteLine(myDelegate(1).ToString());
            Console.ReadLine();
        }
What would happen in this scenario? Quite simply “1” would be written to the console, the reason being that myDelegate was last pointing to the AlwaysOne method before it was called. Make sense? In a way, the myDelegate is a variable method that can be swapped and changed when needed. Let’s make the code a little more confusing by using a delegate in the declaration of another delegate as shown below…

    class Program
    {
        private delegate int AdjustValue(InputValue val);
        private delegate int InputValue();

        private static int Dbl(InputValue val)
        {
            return val()*2;
        }

        private static int GetInputVal()
        {
            Console.WriteLine("Enter a whole number : ");
            return Convert.ToInt32(Console.ReadLine());
        }

        static void Main(string[] args)
        {
            AdjustValue myDelegate;                        
            myDelegate = Dbl;
            Console.WriteLine(myDelegate(GetInputVal).ToString());
            Console.ReadLine();
        }
    }
 

Now it gets really interesting because it looks like we have passed a method into a function in the main method by declaring…

Console.WriteLine(myDelegate(GetInputVal).ToString());

So, what it the output? Well, try take a guess on what will happen – then copy the code and see if you got it right.

Well that brings me to the end of this short explanation of Delegates. Hopefully it made sense!