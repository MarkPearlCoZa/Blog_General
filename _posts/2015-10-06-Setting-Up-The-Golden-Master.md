---
layout: post
title: Setting up the Golden Master using ApprovalTests.Net
tags: Refactoring Testing Code
category: General
---

**The Golden Master is one of the approaches I use to make my life easier when refactoring legacy code. Today I would like to share the approach with you.**

### What is Legacy Code? ###

There are many definitions for legacy code. It's something that's easy to recognize and often hard to put in words. 

Michael Feathers, in his book on [Working Effectively with Legacy Code](http://bookreviews.markpearl.co.za/Working-Effectively-With-Legacy-Code/), said:

> To me, legacy code is simply code without tests.   
> ~ Michael Feathers  

While I like Michael's definition, my all time favorite definition for legacy code came from a work colleague, Werner Beytel. He said:

> Legacy code is code that I don't have confidence in!  
> ~ Werner Beytel  

In my career as a software developer I have had to work in many codebases that had legacy code - and to be honest, most of it I created!

### What happens when you have to change it? ###

So what do you do when you come across legacy code and you have to add to it or change it's functionality? 

Before I was introduced to the **Golden Master** approach this was a nerve-racking experience. Typically I would add my new feature while trying to change as little as possible to the existing code. If I came across a section that could clearly do with a bit of refactoring love, instead of applying the [Boy Scout Rule](http://programmer.97things.oreilly.com/wiki/index.php/The_Boy_Scout_Rule), I would quietly leave it and move on.

This is obviously not a good place to be. So what was causing this?

For me it was **Fear**. I had a very real fear that any unsafe refactoring would subtly change the legacy codes behavior without me knowing. Living in fear is not good. To remove this fear I needed a way to verify that I was preserving behavior while making structural changes. If I could get this type of feedback in an inexpensive way I could confidently refactor legacy code without fear.

Now, with new code I have a very easy way of verifying that I am preserving behavior - I call them acceptance tests. Acceptance tests are a set of automated tests that I write when developing a system that verify that the requirements are being met.

The problem is, the very nature of legacy code often means it is not clear what the existing behaviour is. You can try and discover the behavior by finding the requirements documentation, but you have a better chance of winning the lottery than those documents being up to date. You could also go through the code base line by line to uncover it's behaviour but most legacy code is so complex that it would take years to understand all the behavior without making refactorings as you go.

So what do you do?

### Characterization Tests and the Golden Master ###

In a situation like this the best thing to do is to write characterization tests. Characterization tests are tests that characterize the actual behavior of the code without worring about intent. In essence, instead of trying to uncover the behavior we simply assume that whatever is happening right now is exactly what should be happening and write tests that assert this.

In many ways I think of Characterization Tests as a type of [black box](https://en.wikipedia.org/wiki/Black-box_testing) test. We input a set of values and record a set of outputs - these outputs we call the **Golden Master** *(interestingly this word probably originated from the ['golden master'](https://en.wikipedia.org/wiki/Audio_mastering) generated for audio post-production master copies)*. 

Once we have generated a golden master we are ready to start refactoring. After each refactoring step we rerun our tests and compare the new generated output against our original golden master. If during a refactoring step there is a difference in the new output and the golden master we know we have **inadvertantly introduced a behavioural change**. Behavioral changes during a refactor are undesireable. Whenever we introduce behavioral changes during a refactoring step we revert the step back to a safe point where our test output and our golden master match and attempt the step again. 

After refactoring to a suitable level we reach a point where we have confidence in the code. It is at this point that we typically introduce acceptance tests and delete the characterization tests. Once we have done this we are at the same place we would be if we were working with new shinny code. We are now ready to change the feature or add the new feature that brought us to this code in the first place.

### Putting this in action in .Net ###

So it is great talking about it at a conceptual level, but let's put it into action. Today I am going to show you how to setup the infrastructure for a golden master test using ApprovalTests framework. I am targeting C# and .Net, but don't let that deter you, if you work in another platform or language there are many different ports of the [ApprovalTests framework for a range of languages](https://github.com/approvals) and once you get the gist of how it works you should easily be able to apply the principles to your langauge of choice.

The tools I am going to use are:  
- Visual Studio 2013 (this should work in 2012 & 2010)  
- [Resharper 9](https://www.jetbrains.com/resharper/) (Our refactoring tool of choice)  
- [NUnit](https://www.nuget.org/packages/NUnit/) (Underlying unit test framework)  
- [ApprovalTests.Net](https://www.nuget.org/packages/ApprovalTests/) (Used to verify our golden master with our generated output)  
- [Git](https://git-scm.com/downloads) (Helps us step back if we introduce behavioural changes)  

#### Step 1 - Get some legacy code ####

To practice the Golden Master technique we need some legacy code to work with. I am going to use the [Gilded Rose Kata](https://github.com/emilybache/GildedRose-Refactoring-Kata). This kata was designed specifically for refactoring exercises. It has a nice level of complexity that makes it a great candidate for practicing creating characterization tests.

To get the gilded rose kata go to the folder your want it to be under clone the git repository. In my instance I am using git bash and typed the following:  

~~~
git clone git@github.com:MarkPearl/Kata_GildedRose.git
~~~

Once you have cloned the Gilded Rose Kata, open up the Visual Studio solution which should be in the root of the cloned reporistory (GildedRoseKata.sln).  

#### Step 2 - Add NUnit and Approvals to the Test Project ####

Now that we have our legacy code, we need to add our test frameworks. In this instance we are going to use NUnit as our base test framework and the ApprovalTests framework to make working with a golden master easy. 

The easiest way to do this is to use the Nuget Package Manager Console inside of Visual Studio (Tools > NuGet Package Manager > NuGet Package Manager Console).  

In the package manager console type the following:

~~~
PM> Install-Package NUnit -Project GildedRoseKata.Tests
PM> Install-Package NUnit -Project GildedRoseKata.Tests
~~~

This will install the latest nuget packages for NUnit and ApprovalTests to your test project. You should now be at a point where your solution will build successfully. Check by building the solution.
  
#### Step 3 - Create a Golden Master ####

At a high level whenever the ApprovalTests is run it does the following:

- Capture the response of a test into a text file ending with the extension .received.txt  
- Compare the captured reponse with a file that has the same name but ends with the extension approved.txt
- Fail if the .received file is different from .approved file.  
- Pass if the .received file is identical to the .approved file.

In our cloned Gilded Rose Kata we have already setup the basics of an approval test in a method called 'ThirtyDays' in a class called 'ApprovalTests' (this can be found under the GildedRoseKata.Tests project).

Go into Windows Explorer and have a look at the contents of the GildedRoseKata.Tests folder. You should see the following 6 files:  
 
- ApprovalTest.cs  
- GildedRoseKata.Tests.csproj  
- GildedRoseKata.Tests.csproj.user  
- GildedRoseTest.cs  
- packages.config  
- TextTestFixture.cs  

Now run the test, it should fail with a message:

~~~
  Expected string length 0 but was 11710. Strings differ at index 0.
  Expected: <string.Empty>
  But was:  "OMGHAI!\r\n-------- day 0 --------\r\nname, sellIn, quality\r\n+5 D..."
  -----------^
~~~

It is failing because we have not yet created an approved file (our golden master). What has happened however is that the ApprovalTests library has generated a received file for this test. You can see this by examining the contents of the GildedRoseKata.Tests folder. There are now **7** files. The 7th file is ApprovalTest.ThirtyDays.received.txt  

- ApprovalTest.cs  
- GildedRoseKata.Tests.csproj  
- GildedRoseKata.Tests.csproj.user  
- GildedRoseTest.cs  
- packages.config  
- TextTestFixture.cs  
- **ApprovalTest.ThirtyDays.received.txt** 

If you open this file with a text editor your will notice that it has several lines of text in it. For now we are not going to worry about what this means. We are going to simply generate our approved (golden master) file.

To create the approved file, copy the ApprovalTest.ThirtyDays.received.txt and rename the copy to ApprovalTest.ThirtyDays.approved.txt

You should now have 8 files in the GildedRoseKata.Tests folder:

- ApprovalTest.cs  
- GildedRoseKata.Tests.csproj  
- GildedRoseKata.Tests.csproj.user  
- GildedRoseTest.cs  
- packages.config  
- TextTestFixture.cs  
- **ApprovalTest.ThirtyDays.received.txt**
- **ApprovalTest.ThirtyDays.approved.txt**

Rerun the 'ThirtyDays' test. It should now pass!

We have now created a golden master for the ThirtyDays test and it is checking our current test output against our golden master.

#### Step 4 - Verify that our Golden Master works ####

To double check that this test is indeed validating it's ouput against our golden master we are going to simulate a behavioral change. To do this we are going to edit he GildedRose.cs file.

Open the GildedRose.cs file (GildedRoseKata project). 

You should see the following code at line 21 to 24

~~~
if (Items[i].Name != "Sulfuras, Hand of Ragnaros")
{
    Items[i].Quality = Items[i].Quality - 1;
}
~~~

Comment out line 23.

~~~
if (Items[i].Name != "Sulfuras, Hand of Ragnaros")
{
    // Items[i].Quality = Items[i].Quality - 1;
}
~~~

Rerun the 'ThirtyDays' test. The test should fail!  
Uncomment  line 23 to get it back to what it was before.  
Run the test again and it should pass.  

If you are running a version control system, now is a good point to add your changes and commit!

~~~
git add -A
git commit -m "Golden master added for ThirtyDays"
~~~

And with that happy refactoring!

### So what have we achieved? ###

At this point we have a golden master setup for the 'ThirtyDays' test. 
We can now begin to refactor the GildedRose.cs file. In refactoring we want to do small steps with quick feedback. That could mean making minor changes, running the golden master test to make sure it is passing and then committing.

### What have we learn't? ###

- Characterization tests as useful when working with Legacy Code.  
- With characterization tests we don't have to understand what is going on, we just worry about the output.  
- Setting up a golden master with ApprovalTests is fairly trivial

#### References ####

[Refactoring Legacy Code: Part 1 - The Golden Master](http://code.tutsplus.com/tutorials/refactoring-legacy-code-part-1-the-golden-master--cms-20331)  
[Gold Master Testing - Automatically Validating Millions of Data Points](http://blog.codeclimate.com/blog/2014/02/20/gold-master-testing/)  
[Golden Master Testing: Refactor Complicated Views](http://www.sitepoint.com/golden-master-testing-refactor-complicated-views/)  
[Wiki: Audio Mastering](https://en.wikipedia.org/wiki/Audio_mastering)  
[Wiki: Software release life cycle](https://en.wikipedia.org/wiki/Software_release_life_cycle)  
[TechTerms: Golden Master](http://techterms.com/definition/goldenmaster)  

[NUnit Nuget](https://www.nuget.org/packages/NUnit/)  
[ApprovalTests Nuget](https://www.nuget.org/packages/ApprovalTests/)  
[ApprovalTests.Net Project Site](https://github.com/approvals/ApprovalTests.Net)  
[ApprovalTests for all Languages Project Site](https://github.com/approvals)  
[PluralSight Tutorial on Approval Tests for .Net](http://www.pluralsight.com/courses/approval-tests-dotnet)  

[Resharper Product Site](https://www.jetbrains.com/resharper/)  

[Working Effectively with Legacy Code by Michael C. Feathers](http://bookreviews.markpearl.co.za/Working-Effectively-With-Legacy-Code/)  

[Gilded Rose Kata for all Languages](https://github.com/emilybache/GildedRose-Refactoring-Kata)  
[Gilded Rose Kata for C# Visual Studio 2013](https://github.com/MarkPearl/Kata_GildedRose)  
