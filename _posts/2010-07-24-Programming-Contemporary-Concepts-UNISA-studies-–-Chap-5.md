---
layout: post
title: Programming Contemporary Concepts UNISA studies – Chap 5
tags: 
category: University
--- 
Any ramblings and blog posts associated with the UNISA COS 2144 tag should be considered study notes for my lectures...

In this chapter they discuss the essentials of function declarations, prototypes, and signatures; overloading functions; function call resolution; default/optional arguments; temporary variables and when they’re created; reference parameters and return values; and inline functions…

Function Declarations

Each function has…

A name
A return type (which may be void)
A parameter list (which may be empty)
A body
The name, return type & parameter list form the functions interface.

The body forms the functions implementation.

A function must be declared before it is used for the first time. This is called a function prototype.

A function prototype is a declaration that must include…

The function return type
The functions name
An ordered, command separated list of the types of the function’s parameters.
Overloading Functions

The signature of a function consists of its name and its parameter list. Interestingly in c++ the return type is not part of the signature.

c++ permits overloading of function names. Overloading occurs when two or more functions within a given scope have the same name but different signatures.

Function call resolution is the process of determining which function is to be called, and the order of scope that the compiler checks to determine the call.

Optional Arguments


Function parameters can have default values, making them optional.

The default value for an optional argument can be a constant expression, or an expression that does not involve local variables.

Parameters with default arguments must be the right-most parameters in the parameter list.

Trailing arguments with default values can be left out of the function call. The corresponding parameters will then be initialized with the default values.

Because an optional argument specifier applies to a function’s interface, it belongs with declaration, not the definition of the function if the declaration is kept in a separate header file.

///
/// initialVal is an optional parameter and can
/// be left out when calling the function hello()
///
QString hello(QString initialVal = "123")
{
    return initialVal;    
}

int main(int argc, char *argv[])
{
    QApplication myapp(argc, argv);
    QWidget wid;
    //
    // hello can be called in either way...
    //
    qDebug() << hello() << hello("Howdy");
    QString message;
    QTextStream buf(&message);
    hello();
    
    buf << "test widget";
    qDebug() << message;
    
    QLabel label(message);
    label.show();
    return myapp.exec();
}

Declaring a function with n optional arguments can be thought of as an abbreviated way of declaring n+1 functions, one for each possible way of calling the function.

Operator Overloading

The word operator is used in c++ to define new meaning for an operator symbol such as +, –, * etc

It is possible to override the default meaning of an operator.

Situations where one might overload the operator would be in circumstances where it would be natural to read the operator as part of the code. For instance, adding complex numbers…

There are some limitations on operator overloading. Only built in operators can be overloaded – meaning you cannot make up your won operator symbols.

Once also cannot overload the precedence of the operators when expressed in equations, so BODMAS still applies, regardless of the overloading.

Parameter Passing by Value

By default c++ parameters are passed by value. When a function is called, a temporary local copy of each argument object is made and placed on the program stack.

A useful way to remember how call by value works is this… if a value is passed into a function using call by value, a temporary variables is created that copies the values of the original variable being passed through. No actual changes are done to the original variable within that scope, so once the function is exited, the original variable will not have changed in anyway.

Parameter Passing by Reference

If one were always passing variables by call by value, we would soon have circumstances where we could run very quickly out of memory. Especially if we were dealing with large values. It would also be expensive whenever making a function call because processing would occur to make copies of the the original value. This is where call by reference plays a role…

A reference parameter is simply a parameter that is an alias for something else. To declare a parameter to be call by reference, simply put a & before the parameter name.

Changes to a parameter using call by reference will result in changes to the original value – in essence you are working on the original value, not some temporary variable.

///
/// initialVal is being passed through as a call by refernce
///
QString hello(QString &initialVal)
{
    initialVal = "Changed";
    return initialVal;    
}

int main(int argc, char *argv[])
{
    QApplication myapp(argc, argv);        
    QString TestVariable = "Howdy";    
    return myapp.exec();
}
 

Reference to const

As mentioned in the above section, a value can be passed by reference, which removes many of the overheads of passing large objects between functions, however it also make the original variable vulnerable as it can be changed – to allow one to secure a variable, yet still pass it by reference, one can use the const keywarod.

///
/// initialVal is being passed through as a call by reference, but pass it using the const keyword,
/// the compiler bring up an error as we try to change the value within the function which is not
/// allowed when the const keyword is in the header of the parameter
///
QString hello(const QString &initialVal)
{
    initialVal = "Changed";
    return initialVal;    
}

Function Return Values

Some functions return a value when they have been called. This is done by using the “return” statement.

Returning References from Functions

Sometimes it can be useful to design a function so that it returns a reference. As with reference parameters. it is possible to protect a reference return by specifying that the object it aliases is const.

One needs to be careful though, when a function exits, all local variables are destroyed. One should not return a local variable reference as this will lead to buggy code… see the code example below…

//
// Bug, it is returning a reference that is being destroyed when the function exits.
//
int& max(int i, int j)
{
    int retval = i > j ? i : j;
    return retval;
}

Note, the compiler will pull this up as a warning, but not an error…

Warning 2 warning C4172: returning address of local variable or temporary c:\Users\Mark\Documents\Visual Studio 2008\Projects\HelloWorld\HelloWorld\main.cpp 26 HelloWorld 

Overloading on const-ness

const changes the signature of a member function. This means that functions can be overloaded on const-ness.

I am not exactly sure what this means… but this answer on Stack Overflow might help…

Inline Functions

To avoid the overhead associated with a function call, c++ permits you to declare functions to be in,ine.

Such a declaration is a request to the compiler that it replace each call to the function with the fully expanded code of the function.

Inlining functions can give a program a boost in performance, with the cost of the compiled code size to be larger. This will lead to more memory usage required to store the program in memory etc.

Inlining code does not necessarily mean a boost in performance either, as there are a number of factors including compiler settings, nature of the application, etc that will play a role in determining the overall performance.

An inline function is similar to a #define macro with one very important difference. The substitution process for a #define macro is handled by the pre-processor (which is in essence just a text editing). The substitution process for an inline function is handled by the compiler, which will perform the operation much more intelligently.

Inlining versus Macro Expansion

Macro expansion is a mechanism for placing code inline by means of the following pre-processor directive.

#define MACRO_ID expr

Macro expansion provides no type checking for arguments. it is essentially an editing operations. Each occurrence of MACRO_ID is replaced by expr.

Careful use of parenthesis in macros is necessary to avoid precedence errors.

Macro expansion is dangerous, as if the code is not correct it can lead to some very cryptic errors.
