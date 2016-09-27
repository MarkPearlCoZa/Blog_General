---
layout: post
title: Working with Nulls
tags: Code 
category: Misc
---

> Below are a set of pattern's I apply to C# code, these patterns may port to other languages but it is important to note they are context specific patterns and advice.

I would like to spend some time on nulls. Before you tackle nulls you should first understand the difference between reference type variables and value type variables. I'm going to assume you already have this understanding.

### Before there were nulls, there were magic numbers...

Before there were nulls, there were magic number variables. Magic number variables are variables that have a specific value that represents a contextual state. The first time I was introduced to magic number variables was back in my Visual Basic 6 days. 

Back then it was not uncommon for me to use magic numbers to represent a specific state. For example, if I had a variable 'age' and I wanted to represent it as 'unset' I would give 'age' a value of -1. This made perfect sense, when would you ever come across someone with a negative age?

The problem with magic numbers are that you begin to litter your code with if statements to handle the special states - very quickly this gets quite messy. In addition to it getting messy, every time you perform some sort of calculation on the value you first have to check if it is in one of your magic states. If you don't you can introduce subtle bugs - like the one below which is meant to give you a 50% discount if you are under the age of 20...

~~~
var discount = (age < 20) ? 0.5 : 1.0;  
// what happens if we don't check for age to be unset!!
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
SomeWork myObject = MethodThatReturnsAObject();
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

I've worked in several large code bases where we applied these two rules with great results. I would really recommend addopting these two practices.

### Avoid null on Calculation or Coordination Class Instances

Classes can be used in many different ways. Remember, a class is a template for an object and is a very general concept. Off hand I can think of several types of things I use classes and thus object for...

- Calculation Classes : These are classes that perform some sort of calculation and return a result.  
- Coordination Classes : These are classes that co-ordinate a workflow or a set of calculation classes.  
- Entity Classes : These are classes that hold information. 
- DTO Classes : Similar to entity classes, intended to carry information between services.   

I would recommend avoiding setting calcualtion or coordination classes to null. This avoids the noisy boiler plate null checking code I believe Clean Code was warning us against. I handle Entity & DTO classes slightly differently.

### Use null on Entity & DTO Properties

Instances of Entity or DTO classes hold some form of data. It is perfectly reasonable for some of this data to 'not be set' in which case I need some way to represent this. As already mentioned, I want to avoid using magic values to represent this. This for me is where setting a property of an instance to null is a perfectly acceptable.

For instance...  

~~~
class Person 
{
    public int? Age {get; set;}
}
~~~

In the above C# code for a Person Class I might need to create a Person object and not know the person's age. Having age nullable is useful. It avoids the problem of 'buggy' calculations. 

For instance if we take a variation of our age calculation bug first used to display the pitfalls of magic numbers...  

~~~
var person = new Person();
var discount = (person.Age < 20) ? 0.5 : 1.0;  
~~~

On the calculation of the discount, if age is set to NULL an exception is thrown. If I want to avoid an exception, I need to explictly check for the null value and react accordingly.

### Null Object Pattern

There are situations where you don't want to litter your code with explicit checks for Null and you know what outcome you want should a null reference occur. At times like this it can be appropriate to leverage the Null Object Pattern.

At it's essence the Null Object Pattern replaces a null reference with a null object. The null object implements the expected interface with the implementation doing 'nothing'.

This is probably best explained using an example. Let's use code previously used, but expand on it. Assume we had the following code...

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

We also define another class that acs as our Null Object Class, it looks as follows...

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
