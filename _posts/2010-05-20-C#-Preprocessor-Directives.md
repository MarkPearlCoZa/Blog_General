---
layout: post
title: C# Preprocessor Directives
tags: 
category: General
---
Going back to my old c++ days at university where we had all our code littered with preprocessor directives - I thought it made the code ugly and could never understand why it was useful. Today though I found a use in my C# application.

The scenario – I had made various security levels in my application and tied my XAML to the levels by set by static accessors in code. An example of my XAML code for a Combobox to be enabled would be as follows…

~~~
<ComboBox IsEnabled="{x:Static security:Security.SecurityCanEditDebtor}" />           
~~~
 

And then I would have a static method like this…

~~~
public static bool SecurityCanEditDebtorPostalAddress
        {
            get
            {
                if (SecurityCanEditDebtorPostalAddress)
                {
                    return true;
                }
                else
                {                    
                    return false;                    
                }
            }
        }
~~~

My only problem was that my XAML did not like the if statement – which meant that while my code worked during runtime, during design time in VS2010 it gave some horrible error like…

NullReferenceException was thrown on “StatiucExtension”: Exception has been thrown by the target of an invocation…

If however my C# method was changed to something like this…

~~~
public static bool SecurityCanEditDebtorPostalAddress
{
    get
    {
        return true;
    }
}
~~~
 

My XAML viewer would be happy. But of course this would bypass my security…

<Drum Roll>

Welcome preprocessor directives… what I wanted was during my design experience to totally remove the “if” code so that my accessor would return true and not have any if statements, but when I release my project to the big open world, I want the code to have the is statement.

With a bit of searching I found the relevant MSDN sample and my code now looks like this…

~~~
        public static bool SecurityCanEditDebtorPostalAddress
        {
            get
            {
#if DEBUG
                return true;
#else

                if (Settings.GetInstance().CurrentUser.SecurityCanEditDebtorPostalAddress)
                {
                    return true;
                }
                else
                {                    
                    return false;                    
                }
#endif
            }
        }
~~~
 

Not the prettiest beast, but it works. Basically what is being said here is that during my debug mode compile my code with just the code between the #if … #else block, but what I can now do is if I want to universally switch everything to the “if else” statement, I just go to my project properties –> Build and change the “Debug” flag as illustrated in the picture below.

2010-06-01 02-33-44 AM

Also note that you can define your own conditional compilation symbols, and if you even wanted to you could skip the whole properties page and define them in code using the #define & #undef directives.

So while I don’t like the way the code works and would like to look more into AOP and compare it to this method, it works for now.