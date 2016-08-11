---
layout: post
title: Blue Green Deployment Notes
tags: Useful
category: Tech
---

In essence, you have two identical production environments called Blue & Green
 
At any one time only one server is live!  
The live server is called the Green server.  
Final stage of testing takes place in the environment that is not live, we call this the Blue server.  
Once test cases are passed, you switch the router so all incoming requests now go to the other server – that means the 'blue' server now becomes the 'breen' live server and vice versa   

#### References ####

[CloudFoundry Blue Green Explanation](https://docs.cloudfoundry.org/devguide/deploy-apps/blue-green.html)  
