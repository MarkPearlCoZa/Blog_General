---
layout: post
title: MSpec Notes
tags: Tests
category: Tech
---

#### Adding to Solution via NuGet ####

~~~
nuget install Machine.Specifications
nuget install Machine.Specifications.Should
~~~


#### Basics of MSpec ####

~~~~
public class ThisIsTheTest
{
	Establish context = () => x = 5;
	Because of = () => x = x + 1;
	It Should_Be_6 = () => x.ShouldEqual(6);
}
~~~~

#### Keywords ####

- Subject  
- Tags  
- Establish  
- Cleanup  
- Because  
- It  
- Ignore  
- Catch  

#### Resharper Templates ####

- **mse** Establish  
- **msb** Because  
- **msi** It  
- **msf** A failing It  

#### References ####

[The Mother Ship - MSpec GitHub](https://github.com/machine/machine.specifications)  
[Getting started with MSpec - Covers basic installation](http://novuscraft.com/blog/getting-started-with-mspec)  
[Basics for Settings Up Environment for MSpec](http://awkwardcoder.com/2010/04/13/how-to-mspec/)  
