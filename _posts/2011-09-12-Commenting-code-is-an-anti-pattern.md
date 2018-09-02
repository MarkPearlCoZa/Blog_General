---
layout: post
title: Commenting code is an anti-pattern
tags: 
category: General
---
I have just gotten involved in a project that has been around for a while but developed with a different methodology to the one I am used to. One of the first things I noticed is that there were very little comments if any in the project. When bringing this up with one of the other developers on the team he defended the position of having no comments because as a team they felt that comments were an anti pattern. The motivation was as follows…

Motivation
1) We name our methods and parameters so that they have meaning…

    public class PersonWithComments
    {
        /// <summary>
        /// Makes a person class
        /// </summary>
        /// <param name="name">This needs to be the full name</param>
        public PersonWithComments(string name)
        {
            
        }
    }
 
In the above code snippet the parameter name actually requires the full name. By relying on the comment to get this information it is fairly easy for a developer to miss the meaning of what “name” requires. Compare this with the snippet below…
 
    public class PersonWithoutComments
    {        
        public PersonWithoutComments(string firstName, string lastName)
        {

        }
    }
 
Because there were no comments, the developer had to rely on the naming of the parameters to indicate their intent.
 
2) Comments are not easily viewed/updated when refactoring…

The team regularly refactored their code, often refactoring many many times in a session. When refactoring it was found that often the meaning of the method would be tweaked / changed and so the comments associated with the method would behind. This led other developers in the team to not always be confident on the validity of the comments. This added an element of doubt to the comments.

3) Commenting tests is not an anti-pattern

While the team found commenting production code to be of no real use, commenting tests were treated totally differently. In the tests they would explain certain business rules and why that particular test was necessary.

The heated debate this design decision made
What I found interesting was when these ideas were presented to a group of developers there was uproar in the room. The majority of the developers were from a statically typed world (C#) and I was surprized how passionate they felt about the necessity of putting comments in their code….

So, if someone had presented the idea that commenting code was an anti-pattern I think my initial response would be to defend the need of comments – I have had 20+ years of having comment your code drilled in my head for this to be a gut response however after being exposed to the concept for a while and having some time to think about it I am now leaning to the side that says I agree – commenting code (production code / NB not test code) is an anti-pattern.

My motivation is this…

I live in a strongly / statically typed world. I understand the benefits of this. If you considered your c# code as all being checked by the compiler, then one of the few things the compiler is going to ignore will be your comments… they fall under the radar. Since I use refactoring heavily the fact that my comments can fall behind my code worries me. In fact if I go through all the projects that I have done in the past, 90% of my comments are now no longer relevant – and the portion that is I could have easily extracted to tests.

What are your thoughts?