---
layout: post
title: C# double and nary for loops
tags: 
category: General
---
Something that I wasn’t aware was possible in C# was double for loops… they have the following format.

for (int x = 0, y = 0; x < 10; x++, y=x*2)
{
    Console.Write("{0} ", y);
}                  
Console.ReadLine();
This would give you the following output…

0 2 4 6 8 10 12 14 16 18

In fact you can use as many variables as you want, the following would also be valid…

for (int x = 0, y = 0, z = 10; x < 10; x++, y=x*2)
{
    Console.Write("{0} ", z);
}                  
Console.ReadLine();