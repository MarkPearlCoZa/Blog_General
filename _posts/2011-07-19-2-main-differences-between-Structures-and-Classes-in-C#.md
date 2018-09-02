---
layout: post
title: 2 main differences between Structures and Classes in C#
tags: 
category: General
---
I have always been slightly confused about the difference between classes and structures in C#. For many years, structures seemed identical to classes, but were simply not as extensible. Recently I had a relook at them and came up with two key identifying features that help me differentiate the two..

Where they are stored
Value and Reference values
So, the first main difference for me is that structure instances are stored on the stack and class instances are stored on the heap.

The second main difference is that structures are value types while classes are reference types. With this in mind it is interesting to see the differences between structures and classes in the following code snippet and output.

using System;

namespace DifferenceBetweenClassesAndStructures
{

    struct StrucutreExample
    {
        public int x;        
    }

    class ClassExample
    {
        public int x;        
    }

    class Program
    {
        static void Main(string[] args)
        {
            StrucutreExample st1 = new StrucutreExample(); // Not necessary, could have done StructureExample1 st1;
            StrucutreExample st2;

            ClassExample cl1 = new ClassExample();
            ClassExample cl2;                        

            cl1.x = 100;
            st1.x = 100;

            cl2 = cl1;
            st2 = st1;

            cl2.x = 50;
            st2.x = 50;

            Console.WriteLine("st1 - {0}, st2 - {1}", st1.x, st2.x);            
            Console.WriteLine("cl1 - {0}, cl2 - {1}", cl1.x, cl2.x);            
            Console.ReadLine();
        }
    }
}
 

As you can see form the above code, we have instantiated 2 instances of a structure and 2 instances of a classe identically, and then pointed the second instance of the structure and the class to the first instance of each. The output is different, while the second instance of the class is pointing via reference to the first instance of the class, with the structure the second instance makes an independent copy of the first structure and so when you change the 2nd structures value, it does not effect the first structures value.

So with that in mind, the output would be as follows…

2011-07-19 01-07-19 PM

 

And there you go, two major differences for me between structures and classes in C#