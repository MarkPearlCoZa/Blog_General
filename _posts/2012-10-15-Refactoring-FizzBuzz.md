---
layout: post
title: Refactoring FizzBuzz
tags: 
category: General
---
A few years ago I blogged about FizzBuzz, at the time the post was prompted by Scott Hanselman who had podcasted about how surprized he was that some programmers could not even solve the FizzBuzz problem within a reasonable period of time during a job interview.

Originally I thought I would give the problem a go in F# and sure enough the solution was fairly simple – I then also did a basic solution in C# but never posted it. Since then I have learned that being able to solve a problem and how you solve the problem are two totally different things. Today I decided to give the problem a retry and see if I had learnt anything new in the last year or so. Here is how my solution looked after refactoring…

Solution 1 – Cheap and Nasty
public class FizzBuzzCalculator
{

    public string NumberFormat(int number)
    {
        var numDivisibleBy3 = (number % 3) == 0;
        var numDivisibleBy5 = (number % 5) == 0;

        if (numDivisibleBy3 && numDivisibleBy5) return String.Format("{0} FizzBuz", number);
        else if (numDivisibleBy3) return String.Format("{0} Fizz", number);
        else if (numDivisibleBy5) return String.Format("{0} Buz", number);

        return number.ToString();
    }

}

class Program
{
    static void Main(string[] args)
    {
        var fizzBuzz = new FizzBuzzCalculator();

        for (int i = 0; i < 100; i++)
        {
            Console.WriteLine(fizzBuzz.NumberFormat(i));
        }        
    }
}
My first attempt I just looked at solving the problem – it works, and could be an acceptable solution but tonight I thought I would see how far  I could refactor it… The section I decided to focus on was the mass of if..else code in the NumberFormat method.

Solution 2 – Replacing If…Else with a Dictionary
public class FizzBuzzCalculator
{
    private readonly Dictionary<Tuple<bool, bool>, string> _mappings;

    public FizzBuzzCalculator(Dictionary<Tuple<bool, bool>, string> mappings)
    {
        _mappings = mappings;
    }

    public string NumberFormat(int number)
    {
        var numDivisibleBy3 = (number % 3) == 0;
        var numDivisibleBy5 = (number % 5) == 0;

        var mappedKey = new Tuple<bool, bool>(numDivisibleBy3, numDivisibleBy5);

        return String.Format("{0} {1}", number, _mappings[mappedKey]);
    }
}

class Program
{
    static void Main(string[] args)
    {
        var mappings = new Dictionary<Tuple<bool, bool>, string>
                {
                    { new Tuple<bool, bool>(true, true), "- FizzBuzz"},
                    { new Tuple<bool, bool>(true, false), "- Fizz"},
                    { new Tuple<bool, bool>(false, true), "- Buzz"},
                    { new Tuple<bool, bool>(false, false), ""}
                };

        var fizzBuzz = new FizzBuzzCalculator(mappings);

        for (int i = 0; i < 100; i++)
        {
            Console.WriteLine(fizzBuzz.NumberFormat(i));
        }

        Console.ReadLine();
    }
}
In my second attempt I looked at removing the if else in the NumberFormat method. A dictionary proved to be useful for this – I added a constructor to the class and injected the dictionary mapping. One could argue that this is totally overkill, but if I was going to use this code in a large system an approach like this makes it easy to put this data in a configuration file, which would up its OC (Open for extensibility, closed for modification principle).

I could of course take the OC principle even further – the check for divisibility by 3 and 5 is tightly coupled to this class. If I wanted to make it 4 instead of 3, I would need to adjust this class. This introduces my third refactoring.

Solution 3 – Introducing Delegates and Injecting them into the class
public delegate bool FizzBuzzComparison(int number);

public class FizzBuzzCalculator
{
    private readonly Dictionary<Tuple<bool, bool>, string> _mappings;
    private readonly FizzBuzzComparison _comparison1;
    private readonly FizzBuzzComparison _comparison2;

    public FizzBuzzCalculator(Dictionary<Tuple<bool, bool>, string> mappings, FizzBuzzComparison comparison1, FizzBuzzComparison comparison2)
    {
        _mappings = mappings;
        _comparison1 = comparison1;
        _comparison2 = comparison2;
    }

    public string NumberFormat(int number)
    {
        var mappedKey = new Tuple<bool, bool>(_comparison1(number), _comparison2(number));

        return String.Format("{0} {1}", number, _mappings[mappedKey]);
    }

}

class Program
{
    private static bool DivisibleByNum(int number, int divisor)
    {
        return number % divisor == 0;
    }

    public static bool Divisibleby3(int number)
    {
        return number % 3 == 0;
    }

    public static bool Divisibleby5(int number)
    {
        return number % 5 == 0;
    }

    static void Main(string[] args)
    {
        var mappings = new Dictionary<Tuple<bool, bool>, string>
                {
                    { new Tuple<bool, bool>(true, true), "- FizzBuzz"},
                    { new Tuple<bool, bool>(true, false), "- Fizz"},
                    { new Tuple<bool, bool>(false, true), "- Buzz"},
                    { new Tuple<bool, bool>(false, false), ""}
                };

        var fizzBuzz = new FizzBuzzCalculator(mappings, Divisibleby3, Divisibleby5);

        for (int i = 0; i < 100; i++)
        {
            Console.WriteLine(fizzBuzz.NumberFormat(i));
        }

        Console.ReadLine();
    }
}
I have taken this one step further and introduced delegates that are injected into the FizzBuzz Calculator class, from an OC principle perspective it has probably made it more compliant than the previous Solution 2, but there seems to be a lot of noise. Anonymous Delegates increase the readability level, which is what I have done in Solution 4.

Solution 4 – Anon Delegates
    public delegate bool FizzBuzzComparison(int number);

    public class FizzBuzzCalculator
    {
        private readonly Dictionary<Tuple<bool, bool>, string> _mappings;
        private readonly FizzBuzzComparison _comparison1;
        private readonly FizzBuzzComparison _comparison2;

        public FizzBuzzCalculator(Dictionary<Tuple<bool, bool>, string> mappings, FizzBuzzComparison comparison1, FizzBuzzComparison comparison2)
        {
            _mappings = mappings;
            _comparison1 = comparison1;
            _comparison2 = comparison2;
        }

        public string NumberFormat(int number)
        {
            var mappedKey = new Tuple<bool, bool>(_comparison1(number), _comparison2(number));
            return String.Format("{0} {1}", number, _mappings[mappedKey]);
        }

    }

    class Program
    {
        static void Main(string[] args)
        {
            var mappings = new Dictionary<Tuple<bool, bool>, string>
                {
                    { new Tuple<bool, bool>(true, true), "- FizzBuzz"},
                    { new Tuple<bool, bool>(true, false), "- Fizz"},
                    { new Tuple<bool, bool>(false, true), "- Buzz"},
                    { new Tuple<bool, bool>(false, false), ""}
                };

            var fizzBuzz = new FizzBuzzCalculator(mappings, (n) => n % 3 == 0, (n) => n % 5 == 0);

            for (int i = 0; i < 100; i++)
            {
                Console.WriteLine(fizzBuzz.NumberFormat(i));
            }

            Console.ReadLine();
        }
    }
 

Using the anonymous delegates I think the noise level has now been reduced. This is where I am going to end this post, I have gone through 4 iterations of the code from the initial solution using If..Else to delegates and dictionaries. I think each approach would have it’s pro’s and con’s and depending on the intention of where the code would be used would be a large determining factor. If you can think of an alternative way to do FizzBuzz, add a comment!