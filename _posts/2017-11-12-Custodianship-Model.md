---
layout: post
title: Custodianship Model
tags: 
category: General
---

Custodian model works along the principle that a team is a custodian for certain repositories. If a feature is needed and the team that is the "custodian" of the code does not have capacity to do the work, then the team requesting the work can make the changes / adjustments to the code base and make a pull request. The custodians of the code base review the pull request, make sure it is at the level that they would normally do and then merge it in.

## Lessons learn't so far...

If the first time the custodians hear about a request is via a pull request it is too late.

Custodianship takes work, the reason why the original team did not do the work was because they didn't have capacity however reviewing code takes capacity and may still impact the ability to deliver the work.

The custodian becomes the bottleneck. The team doing the contribution wants the code merged as quickly as possible to get feedback however to merge into mainline they need the custodian to review. Sometimes this can take several hours to get to, which leaves a team "waiting" and "frustrated".

Having code inspections to check naming conventions are followed is useful as those contributing are not necessarily familiar with the style in the team.

## Custodianship mindset

What attributes do we need to have in place to be custodian ready in the custodian model of supporting a system.

* Do the custodians have capacity for a member of the crew to pair with the contributing team for a day or two to help them get started  
* Do the custodians have capacity to review the code  
* Is there an example class that the contributors can use to check current naming conventions and code style  

**Will add more info in the coming days...**

#### References

[See custodianship of code repositories](http://blog.markpearl.co.za/Custodianship-of-code-repositories)  
