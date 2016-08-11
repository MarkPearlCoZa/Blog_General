---
layout: post
title: Blue Green Deployment Notes
tags: Useful
category: Tech
---

In essence, you have two identical production environments called Blue & Green
 
At any one time only one server is live!  
The live server is always called the Green server.  
The 'not' live server is always called the Blue server.
At the final stage of testing, testing takes place on the current 'blue' server - the environment that is not live.  
Once test cases are passed, you switch the router so that the blue and green server are swapped.  
All incoming requests now go to the server that was previously not live.  
That means the 'blue' server becomes the 'green' live server and vice versa.   

#### References ####

[CloudFoundry Blue Green Explanation](https://docs.cloudfoundry.org/devguide/deploy-apps/blue-green.html)  
