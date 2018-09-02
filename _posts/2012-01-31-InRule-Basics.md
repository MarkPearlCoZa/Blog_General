---
layout: post
title: InRule Basics
tags: 
category: Tech
---
I have been looking into InRule, a business rule management system (BRMS) from InRule Technology, recently and thought I would do an intro blog on it. I have worked with business rule engines before and from past experience have developed my own list of priorities on what I feel are the most important aspects. Here they are…

Priority 1 - Reduce the cost of change
For me, one of the primary reasons for implementing a business rules engine is because you are expecting change and want to reduce the cost of this change… In the systems that I work on, the primary cost is time (or what a developer charges per unit of work). The easiest way to reduce cost is to make it possible that someone less expensive be able to make the changes to the system. As I have blogged in the past, typically these changes are at a business rule level.

In the past I have made the mistake of implementing my own custom rule engine, and then painting myself in a corner because I or my developer friends were the only ones technically able to make changes to the rules (mainly due to complexity and the amount of effort it would require to simplify the engine so that an average person could use it) In hind sight I would probably have been better off doing the rules directly in code and scraping my custom rules engines.

This is where InRule really shines. The guys at InRule have put a ton of time into creating a powerful business rules engine that is still simple enough so that it doesn’t require developers to drive it the whole time.

Priority 2 - Low Technical Level Entry Point
So, the first thing I look is at what technical level I have to be to use the rules engine. With InRule the entry point is fairly low… if you are comfortable in a tool like excel and doing basic calculations, you should be able to do the basics of modifying rules in InRule. If you are looking at more complex scenarios, InRule is also more than able to cater for your needs.

Priority 3 - Easy hooks into your application
The other thing that plays a critical role in using a rules engine is how well it can integrate with the system that I am developing… again, five stars to the product. InRule has many hooks that you can tie in to with a full .Net SDK (we will see an example of this later in the post).

Priority 4 - Loosely coupled rules with your application
Finally, the last big one for me is how easy is it to change the rules in a loosely coupled way? Again what I liked about InRule is that they have several ways that you can store rules including saving them as external files which you application can load on the fly.

My InRule Start Up Example…
Let’s see how complex InRule actually is…

The goal is to write a basic application that asks me for my name, and then reacts to this message by displaying a message on the screen –

If the person happens to have the letter “a” in their name, then it will say – “You have an A in your name”.
If you have an “a” and an “m” it will also say “You also have a M in your name”
Else it will say “No special letters in your name”
Simple enough…

Step 1 – Make a class project and add a Person class
First I am going to set up a POCO object in Visual Studio as follows… I will be able to access the attributes from within InRule which is great.

namespace InRuleEntities
{
    public class Person 
    {        
        public string Name { get; set; }         
    }    
}
 

Step 2 – Make a console project and reference InRule
Next I am going to add my console application and reference the InRule SDK.

Pic1

The code in the console application is going to be really simple… Something like the following will do.

using System;
using InRuleEntities;

namespace InRuleApp
{
    class Program
    {
        static void Main(string[] args)
        {
            Person thePerson = new Person();
            Console.Write("Enter your name : ");
            thePerson.Name = Console.ReadLine();
            RunRulesFileAgainstPerson("MyRule.ruleapp", thePerson);
            Console.ReadLine();
        }


        public static void RunRulesFileAgainstPerson(string fileName, Person person)
        {
             var rulesapp = new InRule.Runtime.FileSystemRuleApp(fileName);

            using (var session = new InRule.Runtime.RuleSession(rulesapp))
            {
                session.CreateEntity("Person", person);
                session.ApplyRules();

                foreach (var s in session.State.GetActiveNotifications())
                {
                    Console.WriteLine(s.Message);
                }
            }
        }
    }
}
 

NB – this isn’t production ready code but an example. This is merely to display some of the features of InRule so don’t copy and paste it into your mission critical enterprise application.

Step 3 - Make a rules file
In this situation I am going to make a rule that can be loaded on the fly. I can do this through InRule’s authoring tool, irAuthor. First I need to setup a schema… 

Pic2

 

Once my schema is set up, InRule will recognize my Person class which I am going to work with. I now need to actually write the rule…


Pic3

 

An example of part of the rule is shown below…

Pic4

 

And that is about it… Save the rule file to my application folder and everything seems to work fine! 

Running my application will give the following results depending on the name… 

Pic5

 

Pic6

 

Pic7

 

Conclusion
In just a few minutes I was able to set up a rule, and execute it from my .Net application. The rule was loosely coupled to my solution as an external file – meaning I would not need to recompile my solution should the rules need changing.  It was easy as pie. 

This is just the tip of the iceberg.
So I was able to plugin to InRule and demonstrate a very simple If then else rule. But InRule is a lot more than this. There are a number of rules I could create based on the following combination of statements…

If.. Then
If.. Then.. Else
While
Decision Table
There are also a bunch of useful actions that I could perform including…

Setting values
Declaring variables
Firing Notifications
Executing Methods
Executing Workflows
Raising Events
And more… 
If you are looking for a business rules based engine, I would encourage going to InRule’s site and downloading their trial. There are a whole bunch of online tutorials that you will get access to during the trial period.

Do I think InRule has a low enough entry point?
Personally I think it does. Realistically I can think of a number of people round my office that are not developers that I would be confident are able to adjust rules.

I would think the ideal scenario would be to have someone more technical set up the initial rules and get everything working, and then when there are changes to some of the business rules simply getting a lower skilled person to implement the changes.