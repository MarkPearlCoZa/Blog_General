---
layout: post
title: From Platform Manifesto to Platform Principles  
tags: Design
category: NA
---
At my current company we have dominated our industry for decades with our desktop software. We were the leaders, offering great products with great support. When the web emerged we missed it. This opened the door for other companies who solved the same problems we were, but who leveraged the web and got all the benefits associated with it. We had to adapt to stay relevant.

When any company makes any major transformation mindsets and approaches need to change. Running a desktop product company is very different from running a online platform company. Not only do we have to change what we make, we also need to change how we make it, how we sell it, how we market it and how we support it.

Since I'm involved in how we make it, I'm going to share some of the experiences and learnings we have gained in making this transition.

### The Platform Manifesto

To help change our mindset in how we made software as a development organization we adopted a platform manifesto. The platform manifesto went as follows:

~~~
- Medium term thinking over short term thinking  
- Existing experiences over different variations  
- Capabilities as services over monolith extensions  
- Existing assets over new development  
- Nurture the platform over feature delivery  
- Automation over manual repetition  
- Asynchronous interactions over synchronous coupling  
- Stable technologies over the unproven  
- The greater good over individual objectives
~~~

#### What's great about a manifesto

The great thing about a manifesto is that it is a public declaration about our how we do things as software engineers. 
It was a step in the right direction.

#### The problems 

Having a platform manifesto was a step forward in the right direction. It helped highlight what mindsets and approaches we needed to change.

### Our Goal

- Provide resuable functionality to other consuming products and services (Be unique, independent & resilient of others)  
- Accessible via a consistent manner by our products, services & clients 
- Built to be secure, to scale and to be easily operated by ourselves  
- Built for todays use, however designed for future evolutionary needs  
- Be proliferated though our products and services via reuse, rarely rebuilt or duplicated
- Supported by base core platform services and third-party supplier products  



### Principles 

- Always build functionality as independent re-usable services, accessible via an API
- Always re-use or consume services via their API's  
- Always design services to support asynchronous interactions  
- Everything that is repeated is automated  
- Everything must be build secure  
- Everything must be tested  
- Everything is built to be centrally monitored and audited  
- Everything is logged to a central service  


