---
layout: post
title: TDD – Static Methods
tags: 
category: General
---
So I am new to TDD and have been enjoying the ride of learning a new approach – today I came across an interesting situation that I thought I would blog about. I was writing a class that had all sorts of string manipulation in it. I needed some helper methods that would extend my string manipulation abilities. I had read somewhere that I should avoid static methods when doing TDD so I wrote the initial helper class to look something like this…

    public class StringHelper
    {
        public string ReverseStringEx1(string value)
        {
            char[] charArray = value.ToCharArray();
            Array.Reverse(charArray);
            return new string(charArray);
        }        
    }
 
This just didn’t feel right to me… In my calling code a call would have looked like the following…

    class Program
    {
        static void Main(string[] args)
        {                        
            Console.WriteLine(new StringHelper().ReverseStringEx1("123"));            
            Console.ReadLine();
        }
    }
 

After speaking to some of the fellow developers and asking them why static methods were avoided in TDD, the main motivation was that they are hard to replace / mock out and so prohibit testing methods that use them. In my instance I don’t really think this is a concern. The methods that I was writing were self contained and had no state propagating outside the actual method. SO I refactored my helper class to look like the following…

    public class StringHelper
    {        
        public static string ReverseStringEx2(string value)
        {
            char[] charArray = value.ToCharArray();
            Array.Reverse(charArray);
            return new string(charArray);
        }        
    }
This meant when referencing the helper method in code it would look something like this…

    class Program
    {
        static void Main(string[] args)
        {                                    
            Console.WriteLine(StringHelper.ReverseStringEx2("123"));            
            Console.ReadLine();
        }
    }
That seemed cleaner that what I had been doing before, but then extension methods came to mind and so I did one final refactor which ended up with my helper class looking as follows…

    public static class StringHelperExtensions
    {
        public static string ReverseStringEx3(this string value)
        {
            char[] charArray = value.ToCharArray();
            Array.Reverse(charArray);
            return new string(charArray);
        }
    }
 

Which meant the use of the helper would look something like the following…

    class Program
    {
        static void Main(string[] args)
        {                                                
            Console.WriteLine("123".ReverseStringEx3());
            Console.ReadLine();
        }
    }
 

I think from a readability point of view this is probably the easiest, my concern here is have I done something that is going to bite me in the butt down the road. Right now my mindset is as long as I focus on any helper methods being small and not containing any state then I should be okay. I can exercise the methods in unit tests and I would not see why I would want to mock these types of methods out… any comments  / advice would be much appreciated.