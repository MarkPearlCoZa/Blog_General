---
layout: post
title: C# If Else Shortcut
tags: 
category: General
---
 

Recently I participated in a local user group challenge which involved submitting a project that solved a problem with the fewest bytes. My end solution resulted in one long line of code that at first glance seemed like a series of symbols and letters. While I wouldn’t use such an approach in production code it was nice to go against everything I have been taught about naming and spacing.

One optimization that we used was to simplify the if..then..else statement.

In C# you could have the following code where foo is an integer…

if (foo > 5)
{
    foo = 6;
}
else
{
    foo = 4;
}
 
Of course this is to long, so instead you can use the if then else shorthand, which looks something like this…

foo = foo < 5 ? 6 : 4;
 

Pretty cool, what if you didn’t want the else part, so you wanted the shorthand to the following…

if (foo > 5)
{
    foo = 6;
}
 
You could do this…

foo = foo < 5 ?? 6;