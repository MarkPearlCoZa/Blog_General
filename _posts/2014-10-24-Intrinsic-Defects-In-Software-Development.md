---
layout: post
title: Embracing Intrinsic Defects of Development Work
tags: Agile
category: General
---

#### Intrinsic variability of development work ####

A few months ago a work colleague of mine pointed out that often we don't realize the intrinsic properties of the problem space we work in. That particular discussion led to some interesting insights regarding the intrinsic variability of software development work. As he put it, many developers don't recognize that variability is intrinsic in most business problems. By not embracing this, we fight it - we complain when requirements change and spend a lot of energy trying to set things in stone. If we embraced the intrinsic variability of our problem space then our approach and response to 'changing' business requirements would be different. 


#### Embracing intrinsic defects of development work ####

Today I would like to put forward another aspect I have found intrinsic in software development work - defects. As long as software is developed by humans, defects will be an intrinsic aspect of software development. Embracing the intrinsic nature of defects in software development does not mean that we intentionally insert defects into software. Quite the opposite - it means that inspite of our best intentions, we will produce systems that we think work that will have defects. Embracing this means we change the way we approach software development.

For instance, if we embrace that developers will unintentionally insert defects into their code, then we move the conversation away from preventing defects and towards detecting defects. Or put another way, instead of questioning the professionalism of a software developer when they unintentionally insert a bug, we focus at how they can adapt their development practices so that they can easily detect these bugs that we know they will create.

#### The effects of this mindshift ####

This has far reaching effects. One practical example to illustrate the point was with an organization that had not yet fully embraced the concept. Because they saw defects as a fault in the system they geared their process to penalize defect creation instead of embracing it. They physically separated their test team from their development team - with separate physical locations and line managers. Since testers should never detect a defect, detecting a defect became very expensive resulting in a simple defect taking many hours to communicate and handle. It also resulted in performance reviews on developers and reduced KPI's. Incredible tension was created between testers and developers which led to a very tense work environment.

Contrast this to another organization that embraced the intrinsic defects of software development. To reduce the impact of the defects they would unintentionally be creating, they co-located the testers with the developers. The idea being that since they would be creating defects - they wanted to make them really cheap to handle. Whenever a defect was detected, it took minutes to detect and communicate compared to hours and days of the other organization. This radically reduced the cost of defects - it also changed the mindset and emotional impact when a defect was detected.

In a similar vein, the development team realized that they were creating defects and invested time into practices that allowed them to easily detect defects - these included automated testing of critical systems, test driven development, peer review, etc. - all practices that lend themselves to defect detection.

#### Conclusion #####

Embracing that regardless of the professional level of the individuals in a team, they will produce defects and that this is part and parcel of software development is liberating. It encourages defect detection techniques instead of defect prevention techniques. Early detection in this case is often the best form of prevention.

#### References ####

- Donald Reinterston has written several books and articles exploring the [intrinsic nature of variability in development work](http://hbr.org/2012/05/six-myths-of-product-development/ar/1) which I would highly recommend reading. 
