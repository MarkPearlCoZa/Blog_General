---
layout: post
title: Coupling Complexity Quadrants
tags: Design
category: Misc
---
#### What is Coupling?  

Just because two elements interact, does not mean that they are coupled.

Two elements are coupled if a **change to one element implies a change to another element**.  

Coupling is important to software design becuase the costs of changing software are dominated by rippling changes (which means one section of code is coupled to another section). 

**The exponetially rippling changes kills you in software design.**

Reducing coupling takes effort. The more you try to reduce coupling, the more expensive it gets. There is a trade off curve between effort and coupling.  

#### Coupling vs Complexity  

![Coupling Complexity Quadrants]({{ site.url }}/assets/images/CouplingComplexityQuadrants.png)

#### References ####

[Normal Accidents: Living with High-Risk Technologies](http://www.amazon.com/Normal-Accidents-Living-High-Risk-Technologies/dp/0691004129)  
[Software Design - Why, When & How](http://blog.markpearl.co.za/Software-Design-Why-When-How)  
