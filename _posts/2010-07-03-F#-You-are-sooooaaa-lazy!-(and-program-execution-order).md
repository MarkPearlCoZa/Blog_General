---
layout: post
title: F# You are sooooaaa lazy! (and program execution order)
tags: 
category: General
---
So I have mentioned lazy functions before, in particular related to sequences, however I came across it again – but this time with lazy values and thought I would explore it a little bit more…

I used the following code snippet…

~~~
#light
open System

let lHelloWorld = lazy(printfn "Lazy Hello World"; 30+30)
let aHelloWorld = (printfn "Active Hello World"; 30+30)

printfn "lazy value is %d"  lHelloWorld.Value 
printfn "lazy value is %d"  lHelloWorld.Value
printfn "active value is %d"  aHelloWorld
printfn "active value is %d"  aHelloWorld

Console.ReadLine()
 

The output was as follows…

Active Hello World 
Lazy Hello World 
lazy value is 60 
lazy value is 60 
active value is 60 
active value is 60

Now humbly the following comments are going to show how little I know of F#, but at least I think I am learning more…

If this was C# code, in my mind I could describe it as 3 methods,

lHelloWorld Method
aHelloWorld Method
Some main method
Initially I thought the equivalent code would have looked something like this…

class Program
   {
       private static int aHelloWorld()
       {
           Console.WriteLine("Active Hello World");
           return 30 + 30;
       }

       private static int lHelloWorld()
       {
           Console.WriteLine("Lazy Hello World");
           return 30 + 30;
       }

       static void Main(string[] args)
       {
           Console.WriteLine("lazy value is " + lHelloWorld().ToString());
           Console.WriteLine("lazy value is " + lHelloWorld().ToString());
           Console.WriteLine("active value is " + aHelloWorld().ToString());
           Console.WriteLine("active value is " + aHelloWorld().ToString());
           Console.ReadLine();
       }
   }
 

The order of execution would have been just as simple… the lazy value would have been called twice, then the active value would have been called twice resulting in an expected output like…

Lazy Hello World 
lazy value is 60 
Lazy Hello World 
lazy value is 60 
Active Hello World 
active value is 60 
Active Hello World 
active value is 60 

However, the output is not this – so the initial paradigm that I had in my mind of how F# is executing must be wrong! Looking at the output again one can see a few things…

Firstly, the Hello World for both the Lazy and the Active functions is only shown once… and the Active Hello World is shown before the Lazy Hello World. That leads me to think that instead of looking at the LHelloWorld & AHelloWorld as method calls, in a way in my C# brain they are really instances of objects.

To try and translate this into a round C# equivalent I thought the code would look something like this…

class Program
{
    public class aHelloWorld
    {
        public aHelloWorld()
        {
            Console.WriteLine("Active Hello World");
        }

        public int Value 
        {
            get
            {
                return 30 + 30;
            }
        }
    }

    public class lHelloWorld
    {
        private static lHelloWorld instance = new lHelloWorld();

        private lHelloWorld()
        {                
            Console.WriteLine("Lazy Hello World");
        }

        public int Value
        {
            get
            {
                return 30 + 30;
            }
        }

        public static lHelloWorld Instance()
        {
            if (instance==null) 
            {
                instance = new lHelloWorld();
            }
            return instance;
        }
    }


    static void Main(string[] args)
    {
        aHelloWorld objA = new aHelloWorld();            

        Console.WriteLine("lazy value is " + lHelloWorld.Instance().Value.ToString());
        Console.WriteLine("lazy value is " + lHelloWorld.Instance().Value.ToString());
        Console.WriteLine("active value is " + objA.Value.ToString());
        Console.WriteLine("active value is " + objA.Value.ToString());
        Console.ReadLine();
    }
}
~~~

This gives a result like this…

Active Hello World 
Lazy Hello World 
lazy value is 60 
lazy value is 60 
active value is 60 
active value is 60

Which is identical to the F# result. Does this mean that the F# code snippet & C# code snippet are equivalent? Well… no… the output is equivalent, but I think there are some effects of this code that are not equivalent although I am battling to express them…

So, the end result of this post is as follows…

The paradigm in my mind of how F# code executes has changed, in addition instead of looking at functions in F# as some sort of equivalent method call in C#, there is obviously more to it than that!

Any feedback from the community to help me understand these basic principles would of course be much appreciated!
