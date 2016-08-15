---
layout: post
title: Ninject Notes
tags: 
category: Tech
---

#### General ####

**Self** bindings declare a binding of a certain type to itself. Self bindings are not needed for types which have a parameterless constructor. Ninject can instantiate these types on its own. If you declare a self binding.  t is only possible to do a Get<Sword>. For example Get<ISword> would throw an ActivationException.

For example you can do the following:

~~~
Bind<Sword>().ToSelf(); 
~~~

**Method** bindings allow you to specify a method which is responsible to create an instance of the binded type. 

For example you can do the following: 

~~~
Bind<ISword>().ToMethod(() => new Sword(strength = 12)); 
~~~

#### References #### 

[The Mother Ship](http://www.ninject.org/)  
[S/O Question](http://stackoverflow.com/questions/11218830/ninject-basics-with-example-please)  
