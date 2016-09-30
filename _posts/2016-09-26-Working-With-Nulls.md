---
layout: post
title: Working with Nulls
tags: Code 
category: Misc
---
I would like to spend some time on nulls. Before you tackle nulls you should first understand the difference between reference type variables and value type variables. I'm going to assume you already have this understanding - if you don't read [this](http://stackoverflow.com/questions/5057267/what-is-the-difference-between-a-reference-type-and-value-type-in-c).  

### Before there were nulls there were magic numbers

Before nulls there were magic number variables. Magic number variables are variables that have a specific value that represents a contextual state. The first time I was introduced to this concept was back in my Visual Basic 6 days. 

Back then it was not uncommon for me to use magic numbers to represent a specific state. For example, if I had a variable 'age' and I wanted to represent it as 'unset' I would give 'age' a value of -1. Back in the days this made perfect sense, when would you ever come across someone with a negative age?

The problem with magic numbers is you begin to litter your code with if statements. Also, every time you perform some sort of calculation on the value you first have to check if it is in one of your magic states. If you don't you can introduce subtle bugs - like the one below which is meant to give you a 50% discount if you are under the age of 20...

~~~
var discount = (age < 20) ? 0.5 : 1.0;  
// what happens if we don't check for age to be unset!!
~~~

Using magic numbers increases the opportunities for subtle errors and makes it difficult for the program to be adapted and extended in future. Things we want to avoid.

> The rule of thumb is avoid magic number values to represent unset variables if you can, rather set the variable to null

### Clean Code & Nulls

I'm a fan of the book [Clean Code](http://blog.markpearl.co.za/Clean-Code) - if you haven't read it I recommend you do. In Clean Code Uncle Bob suggests two things regarding nulls:

- Do not write methods that return null   
- Do not pass null values in to your methods   

#### Do not write methods that return null 

Why should methods not return null? The motivation for not writing methods that return nulls is that this avoid's unnecessary checks on nulls. For example...  

~~~
var myObject = MethodThatReturnsAObject();
if (myObject != null) 
{
    myObject.doSomething();
}
~~~

Can be written as...

~~~
var myObject = MethodThatReturnsAObject();
myObject.doSomething();
~~~

Which is substantially cleaner.

#### Do not pass null values in to your methods

Why should you not pass null values in to your methods? If you do not pass null to your methods, you avoid having unnecessary checks at the beginning of a method. For instance, you would avoid the following...

~~~
public decimal CalculateTax(TaxCalculator theTaxCalculator)
{
    if (theTaxCalculator == null) throw new ArgumentException();
    ...
} 
~~~

#### My own experience with Clean Code's advice

I've worked in several large code bases where we applied these two rules with great results. I would really recommend addopting these two patterns.

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

#### Don't be scared of exceptions

I've come across several code bases where there seemed to be a fear of throwing exceptions - in fact I've written many systems that had this fear as well. I can't speak for others, but for me, I think it stemmed back to my early days of learning to program at school where there was an expectation of validating user input via the console and recovering elegantly if invalid data was passed in. 

At some point this type of code bled into my domain logic which left me with a litany of code that escaped logic if a value being used in that logic was in a null state. It wasn't till it was explained to me that we throw exceptions when we have 'exceptional' circumstances - and data not being in a form we expect is exceptional. Since embracing this mindset I'm no longer scated of throwing exceptions when I have null values.

~~~
// service1 = null;
// service2 = null;

...

var total = 0;

if (service1 != null) 
{
    total = total + service1.performCalculation();
}

if (service2 != null) 
{
    total = total * service2.performCalculation();
}

return total;
~~~

I would replace the code above with something like the code below and have proper exception handling at a higher level...  

~~~
...

var total = 0;
total = total + service1.performCalculation();
total = total * service2.performCalculation();
return total;
~~~

### Null Object Pattern

There are times when you don't want to throw exceptions, and you still want to keep your code clean. Sometimes it may be appropriate to leverage the Null Object Pattern.



#### References

[Pluralsight Working with Nulls](https://app.pluralsight.com/library/courses/csharp-nulls-working)  
[Wiki on Magic Numbers](https://en.wikipedia.org/wiki/Magic_number_(programming)#Unnamed_numerical_constants)  
[Stack Overflow Clean Code & Nulls](http://stackoverflow.com/questions/6371956/confused-with-uncle-bob-explanation-on-handling-null-objects-in-book-clean-code)  
