---
layout: post
title: Working with Nulls in C#
tags: Code 
category: Misc
---

> Below are a set of pattern's I apply when considering nulls in C#, these patterns may port to other languages or they may not.

I would like to spend some time on nulls. Before you tackle nulls you should first understand the difference between reference type variables and value type variables. I'm going to assume you already have this understanding.

### Before there were nulls, there were magic numbers...

Before there were nulls, there were magic number variables. Magic number variables are variables that have a specific value that represents a contextual state. The first time I was introduced to magic number variables was back in my Visual Basic 6 days. 

Back then it was not uncommon for me to use magic numbers to represent a specific state. For example, if I had a variable 'age' and I wanted to represent it in an  'unset' state I would give it a value of -1. This made perfect sense, when would you ever come across someone with a negative age?

The problem with magic numbers are that you begin to litter your code with if statements to handle the special states - very quickly this gets noisy. In addition you increase the opportunity for subtle bugs. For instance, take the following code...  

~~~
var person = MethodThatReturnsAPerson();
var discount = (person.Age < 20) ? 0.5 : 1.0;  
~~~

What happens if we forget to check for magic numbers values for age and we happen to be using -1 to represent an unset age? We introduce a subtle bug because the calculation still executes and returns a value. Ultimately using magic numbers in this way lends itself to buggy code - something we want to avoid!  

> The rule of thumb is avoid magic number values to represent unset variables if you can, rather set the variable to null which will throw an exception if you try use it in a calculation.

### Passing and returning nulls

I'm a fan of the book [Clean Code](http://blog.markpearl.co.za/Clean-Code) - if you haven't read it I recommend you do. In Clean Code the author suggests two things regarding nulls:

- Do not write methods that return null   
- Do not pass null values in to your methods   

#### Do not write methods that return null 

Why should methods not return null? Simply, if you don't return null you avoid having to check for null after the method call. For example...  

~~~
SomeWork myObject = MethodThatReturnsAObject()
if (myObject != null) 
{
    myObject.doSomething();
}
~~~

Can be confidently written as...

~~~
SomeWork myObject = MethodThatReturnsAObject();
myObject.doSomething();
~~~

Which is substantially cleaner.

#### Do not pass null values in to your methods

Similarly, if you do not pass null values in to your methods you avoid having checks at the beginning of a method for nulls. For instance, you would avoid the following series of null checks...

~~~
public decimal CalculateTax(TaxCalculator theTaxCalculator, Person thePerson)
{
    if (theTaxCalculator == null) throw new ArgumentException();
    if (thePerson == null) throw new ArgumentException();
    ...
} 
~~~

### Whatever you do, be intentional about it

I've worked in several large code bases where we have tried to avoid unnecessary null checks. Fundamentally I agree with what Clean Code is saying - avoiding passing nulls in and out of methods leads to cleaner code. 

That said, I'm conscious that a class is a very general concept and can be used in many different ways. There are times when setting an instance of a class to null is useful and something I do. 

Looking at it, I find there are two main groups I can put classes into in this regard. The first group I rarely set instances of to null - I call these types of classes my "C" classes. The second group I occasionally set instances of to null - I call these types of classes my "D" classes (I'm sure there must be a better name than "C" and "D", I just can't think of one).

#### Calculation & Coordination Classes

"C" classes are calculation or coordination classes. These are classes that either perform some sort of calculation and return a result, or coordinate a set of calculation classes. I rarely set instances of "C" classes to null. 

On saying this, I'm cognisant that I rarely pass these types of classes into normal methods through the method signature. Typically if my code needs to make use of a "C" class, I inject it via the constructor. 

So my previous code example for calculating tax applying this approach would look more like this...  

~~~
Class PersonTaxCalculator

    private readonly TaxCalculator _taxCalculator;

    public PersonTaxCalcuator(TaxCalculator theTaxCalculator) {
        _taxCalculator = theTraxCalculator;
    }

    public decimal CacluateTaxFor(Person thePerson) {
        if (thePerson == null) throw new ArgumentException();
        ...
    }

    ...
}
~~~

#### Data Classes  

"D" classes are data classes. Typically these go by the name of Data Transfer Object or Entities or something along those lines. They hold values, instead of performing or coordinating actions. Instances of classes like these I often set to null because they are doing the same thing my magic variables were doing back in my vb6 days - representing missing values with one added advantage - they throw exceptions when I try and include them in calculations where their values have not been set.  

For instance with the following 'D' class...  

~~~
class Person 
{
    public int? Age {get; set;}
}
~~~

Were I to take an instance of this class and use it in my original age calculation as follows I would get an exception thrown if person or age was not set...  

~~~
var person = MethodThatReturnsAPerson();
var discount = (person.Age < 20) ? 0.5 : 1.0;  
~~~

If I want to avoid an exception, I need to explicitly check for the null value and react accordingly, or I could leverage the null object pattern. 

In older versions of C# were I to check for nulls my code would look as follows...  

~~~
var person = MethodThatReturnsAPerson();
if (person == null) ... // do something
if (person.age == null) ... // do something

var discount = (person.Age < 20) ? 0.5 : 1.0;
~~~

#### Null Coalescing Operator

I could use the null coalescing operator to make it a little cleaner...

~~~
var person = MethodThatReturnsAPerson();
if (person == null) ... // do something
var discount = (person.Age ?? 20 < 20) ? 0.5 : 1.0;
~~~

Unfortunately I still have to check to see if the person object is null, so while the noise of checking is reduced, it is still there. Luckily C# is still evolving which means we can reduce the noise further by leveraging the null conditional operator (introduced in C# 6)  

#### Null Conditional Operator

With the [null conditional operator](https://msdn.microsoft.com/en-nz/library/dn986595.aspx), we can further adapt the code to look as follows...

~~~
var person = MethodThatReturnsAPerson();
var discount = (person?.Age ?? 20 < 20) ? 0.5 : 1.0;
~~~

What the above code is doing is if person object or Age is set to null, it defaults you to an age of 20, otherwise it handles age in the calculation as normal.

Is this better? It's certainly terse. In some circumstances it might make you rethink the noise argument that clean code presented. Whether it is better largely depends on how comfortable the maintainers of this code base are with this sort of syntax and whether they feel it is clean and what problem they are solving.

Regardless the route you go, it is important is that you are explicit on your intent - balancing the tension between readable code and the noise of null checking code.

> Balance the tension between readable code and the noise of null checking code

### Null Object Pattern

There are situations where you don't want to litter your code with explicit checks for null and you know what outcome you want if a value has not been set yet. At times like this Null Object Pattern can be really useful.

What is the Null Object Pattern? At it's essence the Null Object Pattern replaces a null reference with a null object. The null object implements the expected interface with the implementation doing 'nothing'.

It's easier to understand looking at an example. Let's use code previously used, but expand on it. Assume we had the following code...

~~~
var person = MethodThatReturnsAPerson();
var discount = (person?.Age ?? 20 < 20) ? 0.5 : 1.0;
~~~

We have two classes that implement the IPerson type, the first class "Person" does holds real values. It looks as follows...

~~~
Class Person : IPerson
{
	public Age { get; set; }
}
~~~

We also define another class that acts as our Null Object Class, it looks as follows...

~~~
Class UnselectedPerson : IPerson
{
	public Age 
    { 
        get { return 0; }
        set { }
    }
}
~~~

In our method, MethodThatReturnsAObject we have the following factory code...

~~~
public IPerson MethodThatReturnsAPerson(bool doNothing = false) 
{
	return (doNothing) ?  new UnselectedPerson() : new Person();
}
~~~

Now, depending on whether we pass in a true or a false, MethodThatReturnsAPerson will either return the class that returns a person with valid values or the class that does nothing returns an instance of an UnsetPerson.

This is a basic example of the Null Object Pattern. There are several variations.

#### References

[Pluralsight Working with Nulls](https://app.pluralsight.com/library/courses/csharp-nulls-working)  
[Wiki on Magic Numbers](https://en.wikipedia.org/wiki/Magic_number_(programming)#Unnamed_numerical_constants)  
[Stack Overflow Clean Code & Nulls](http://stackoverflow.com/questions/6371956/confused-with-uncle-bob-explanation-on-handling-null-objects-in-book-clean-code)  
[Wiki on Null Object Pattern](https://en.wikipedia.org/wiki/Null_Object_pattern)  
[Why Null is Bad](http://www.yegor256.com/2014/05/13/why-null-is-bad.html)  
[Null-conditional Operators](https://msdn.microsoft.com/en-nz/library/dn986595.aspx)  
