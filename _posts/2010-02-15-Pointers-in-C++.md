---
layout: post
title: Pointers in C++
tags: 
category: General
---
This is a basic review of Pointers in c++

There are 3 main categories of data types in c++,

Simple  
Structured  
Pointer  

A one liner to describe a pointer is a variable whose content is a memory address - thus its name “pointer”. In essence a pointer “points” to another location in memory.

Declaring a Pointer (Specifying Variable Name & Size)

In the most simple case, a pointer “points” to where another variable value is stored in memory. In programming terms, if you were to think about memory as a massive array of bytes, and you wanted to easily get a value from this array using a pointer, you would need two things –starting point in the array, and the stopping point.

Likewise, for a pointer to know the bounds of the memory and to be really useful, you need to know the starting point and the stopping point of the memory that it is pointing to. Thus in the declaration of the pointer you follow the pattern below…

dataType *identifier;

(where the dataType allows the compiler to work out the “stop” part of the memory" – note that the whitespace between the * and the dataType / identifier is not important so int*p is equivalent to int      *      p).

A few examples of declaring pointers include…

int *p;
char *ch;
 

Specifying where a Pointer Points

So, so far if we were the compiler we would know two things

a name that we associate with a pointer data type,
the size of the pointer
We still need to know where the pointer points to.

At this point I get flashbacks to university exams where our examiner has a field day questioning us, his poor students, on various different syntaxes for assigning pointers.

The first way to achieve this is by assigning the “value” of the pointer to hold the value of the memory address of the other data type.

int *p;
int x = 10;    
p = &x;
 

The ampersand, &, called the address of operator, is a unary operator that returns the address of its operand. So basically ‘&’ means “give me the memory location” of the specified data types identifier (e.g. x).

Now assuming that you had applied the code above, and wanted to display the value in x to the console but you wanted to access the value by referring to it via the pointer p. There would need to be some way to specify “the value” that p points to and accessing that value easily! We already know by looking at the assignment of p = &x that the value in “p” is a memory address.

In c++ you have a dereferencing operator (*) aka indirection operator, that when used as a unary operator refers to the object to which the operand of the * points to.

So when in code you see *p, you could replace it with x.

int *p;
int x = 10;    
p = &x;
cout << *p << endl;
cout << x << endl;

In effect, the both cout’s in the code above would be equivalent.

One final thing to note on pointer declarations. When you declare a pointer such as int *p; the compiler allocates memory for p only, not for *p.


The Importance of Precedence

Assume the code below….

string *str;              // Declare str as a pointer 
str = new string;      // Allocate memory of type string 
*str = "Sunny Day";  // Store the string in the data

If we were to make a method call of…

cout << (*str).data() << endl;    
 

Everything would be hunky dory, because the ‘(*identifier)’ takes precedence over the ‘.’ and so the complier would recognize that the class string has a method called data.

However should we do something like…

cout << *str.data() << endl;    
 

we would have a problem because the . takes precedence over the *, and so the compiler would not be able to find a method called data attached to the pointer data type. This kind of syntax is prone to errors & typos, and so in c++ we have another syntax convention for achieving the same result, we use the –> operator.

cout << str->data() << endl;    
 

which is equivalent to…

cout << (*str).data() << endl;    
 

but less easier to make a mistake on.

For a detailed table of operator precedence click here.

Dynamic Memory and the Joys of Memory Leaks in c++ (Why I like Managed Code)

Up to now we have only shown how to use pointers to point to other variables. It is possible in c++ to tell a pointer to allocate some memory dynamically (at runtime), and then to un-allocate it when no longer used.

To allocate memory at runtime you would use the operator New. e.g.

    string *str;        // Declare str as a pointer
    str = new string;    // Allocate memory of type string

 

By using the new operator you have marked a segment of memory as being in use. While memory is in use, no other application should be able to access it. To de-allocate the memory and make it available for use by the rest of the world you can use the delete operator.

delete str;            // De-allocate the memory

The whole concept of leaving it up to a programmer to allocate and de-allocate memory scares me. True, in a program that is a few lines of code it is quite easy to see when and where these operations are needed, however in your typical LOB application that has thousands if not hundreds of thousands of lines of code, you will forget to de-allocate memory and thus have memory leaks.

This is where managed code shines, because you do not have to worry about de-allocating the memory (you leave that up to the garbage collector). The plus side of having control over the allocation and de-allocation of memory is that you have greater control over the performance of the application (which is necessary in critical applications i.e. a Nuclear power station – where you would not want the garbage collector to kick in during a mission critical process and cause a meltdown).

Another important aspect of manually managing the allocation and de-allocation of memory is dangling pointers. In a nutshell, when you call the delete operation, depending on the system, the memory address of where the pointer is pointing to may still be stored in the pointer. When a pointer is in this state, it is called a dangling pointer. The main danger to this is, the machine could have allocated this segment of memory to another process and thus you could potentially cause memory corruption if you were to access the value of the dangling pointer. One sure fire way to avoid this pitfall is to set the pointer value to NULL after calling the delete method. The code snippet below illustrates a potential dangling pointer.

string *str;                 // Declare str as a pointer
str = new string();          // Allocate memory of type string    
*str = "hello";    
delete str;                  // De-allocate the memory    
cout << str->data() << endl; // Reference the dangling pointer
 

Pointer Arithmetic

One can perform some basic arithmetic operations on pointers, for instance assume the following declaration:

int *p;

If the machine allocates 4 bytes to store the address of an int, then..

p++;

would increase the memory address of where p is pointing to by 4 bytes.

For me I would consider it dangerous to be doing such operations in a LOB application, but extremely useful if you are wanting to hack some memory of another program.
