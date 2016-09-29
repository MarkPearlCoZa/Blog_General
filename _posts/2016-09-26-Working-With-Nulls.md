---
layout: post
title: Working with Nulls
tags: Code 
category: Misc
---

> Below are a set of pattern's I apply to C# code, these patterns may port to other languages or they may not.

I would like to spend some time on nulls. Before you tackle nulls you should first understand the difference between reference type variables and value type variables. I'm going to assume you already have this understanding.

### Before there were nulls, there were magic numbers...

Before there were nulls, there were magic number variables. Magic number variables are variables that have a specific value that represents a contextual state. The first time I was introduced to magic number variables was back in my Visual Basic 6 days. 

Back then it was not uncommon for me to use magic numbers to represent a specific state. For example, if I had a variable 'age' and I wanted to represent it as 'unset' I would give 'age' a value of -1. This made perfect sense, when would you ever come across someone with a negative age?

The problem with magic numbers are that you begin to litter your code with if statements to handle the special states - very quickly this gets quite messy. In addition to it getting messy, every time you perform some sort of calculation on the value you first have to check if it is in one of your magic states. If you don't you can introduce subtle bugs - like the one below which is meant to give you a 50% discount if you are under the age of 20...

~~~
var person = MethodThatReturnsAPerson();
var discount = (person.Age < 20) ? 0.5 : 1.0;  

// what happens if we don't check for magic numbers for age, and we are using -1 for an unset age??
~~~

Using magic numbers increases the opportunities for subtle errors and makes it difficult for the program to be adapted and extended down the road - things we want to avoid! 

> The rule of thumb is avoid magic number values to represent unset variables if you can, rather set the variable to null

### Passing and returning nulls

I'm a fan of the book [Clean Code](http://blog.markpearl.co.za/Clean-Code) - if you haven't read it I recommend you do. In Clean Code the author suggests two things regarding nulls:

- Do not write methods that return null   
- Do not pass null values in to your methods   

#### Do not write methods that return null 

Why should methods not return null? If your methods don't return nulls you avoid having to check for nulls after the method call. For example...  

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

Why should you not pass null values in to your methods? Similarly, if you do not pass null values in to your methods, you avoid having checks at the beginning of a method for nulls. For instance, you would avoid the following...

~~~
public decimal CalculateTax(TaxCalculator theTaxCalculator)
{
    if (theTaxCalculator == null) throw new ArgumentException();
    ...
} 
~~~

#### 

I've worked in several large code bases where we applied these two rules with great results. I would really recommend adopting these two practices.

### What to set as null

A class is a very general concept and can be used in many different ways. Were I to say that you should never set instances of classes to null I would be giving you bad advice. There are times when setting an instance of a class to null is extremely useful. Looking at my past experiences with null and the types of instances of classes I use it on I find that for one type of use I rarely set it to null while with another type quite often set to null.

The two types of uses of classes I've decided to call "C" classes vs "D" classes (I'm sure there must be a bettern name for these types, I just can't think of one).

"C" classes are calculation or coordination classes. These are classes that either perform some sort of calculation and return a result, or co-ordinate some sort of workflow or set of calculation classes. I rarely set instances of "C" classes to null.

"D" classes are data classes. Typically these go by the name of Data Transfer Object, or Entities, etc. They hold values, instead of performing actions. Instances of classes like these I often set to null because they are doing the same thing my magic variables were doing back in my vb6 days - representing missing values - except, they have the added advantage of throwing exceptions when I try and include their values in a calculation which makes 'buggy' calculations easier to detect.

For instance with the following 'D' class...  

~~~
class Person 
{
    public int? Age {get; set;}
}
~~~

Were I to take an instance of this class and use it in my original age calculation as follows...  

~~~
var person = new Person();
var discount = (person.Age < 20) ? 0.5 : 1.0;  
~~~

I would get an exception thrown if age was not set. If I want to avoid an exception, I need to explicitly check for the null value and react accordingly or leverage the null object pattern, either way I'm being explicit on my intent.

### Null Object Pattern

There are situations where you don't want to litter your code with explicit checks for null and you know what outcome you want if a value has not been set yet. At times like this Null Object Pattern can be really useful.

What is the Null Object Pattern? At it's essence the Null Object Pattern replaces a null reference with a null object. The null object implements the expected interface with the implementation doing 'nothing'.

It's easier to understand looking at an example. Let's use code previously used, but expand on it. Assume we had the following code...

~~~
SomeWork myObject = MethodThatReturnsAObject(true);
myObject.doSomething();
~~~

We have two classes that implement the SomeWork type, the first class "PrintWork" does the actual work we want. It looks as follows...

~~~
Class PrintWork : SomeWork
{
	public void doSomething() {
		Console.WriteLine("Some work is done");
	}
}
~~~

We also define another class that acts as our Null Object Class, it looks as follows...

~~~
Class DoNothingWork : SomeWork
{
	public void doSomething() {
		// .. do nothing ..
	}
}
~~~

In our method, MethodThatReturnsAObject we have the following factory code...

~~~
public SomeWork MethodThatReturnsAObject(bool doNothing = false) 
{
	return (doNothing) ?  new DoNothingWork() : new PrintWork();
}
~~~

Now, depending on whether we pass in a true or a false, MethodThatReturnsAObject will either return the class that does the actual work (Printing) or the class that does nothing (DoNothingWork).

This is a basic example of the Null Object Pattern. There are several variations.

#### References

[Pluralsight Working with Nulls](https://app.pluralsight.com/library/courses/csharp-nulls-working)  
[Wiki on Magic Numbers](https://en.wikipedia.org/wiki/Magic_number_(programming)#Unnamed_numerical_constants)  
[Stack Overflow Clean Code & Nulls](http://stackoverflow.com/questions/6371956/confused-with-uncle-bob-explanation-on-handling-null-objects-in-book-clean-code)  
[Wiki on Null Object Pattern](https://en.wikipedia.org/wiki/Null_Object_pattern)  
[Why Null is Bad](http://www.yegor256.com/2014/05/13/why-null-is-bad.html)  
