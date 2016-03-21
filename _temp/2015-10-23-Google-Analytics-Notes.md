---
layout: post
title: Google Analytics Notes
tags: Marketing
category: Tech
---

####  Setting Measurable Goals ####

How many people who sign-up or purchase?  
How many visits to the site does it take before a purchase?  
What paths through your site lead to a sale?


You can create up to 20 goals per profile.

Focus on goals that have value!  

##### Goal Types #####

- URL Destination  
- Visit Duration  
- Page Visit  
- Event  

URL Destination types have additional unique values that other goals don't have. 
For instance, you can set a goal to have someone reach your signup page. A requirement might be that someone hits the main page and then finally ends at your signup page.

Tracking of funnell activity is best using the funnel visualization report.

#### Tracking Document Downloads ####

~~~
<a href=... onclick="_gaq.push(['_trackPageview', '/document/to/show/in/analytics.pdf']);"> ... </a>
~~~

#### Tracking Discrete Events - i.e. Download a file ####

Use event tracking to track these types of things...

~~~
_gaq.push('_trackEvent', 'category', 'action', 'label', 'value', 'isNonInteraction']);
~~~

Events are used in considering bounce rates. If a user visited a single page and triggered an event with isNonInteraction set to false, the page is not considered a bounce.  

Events ca ben used for Goals, but cannot be used to define funnels.  

#### E-commerce Tracking ####

~~~
_gaq.push(['_addTrans', 'orderID', 'storeName', 'total', 'tax', 'shipping']);  
~~~

TrackTrans should only be called once per order id.

### References ###

[Google Analytics IQ Test](http://www.googleanalyticstest.com)  
[Google Analytics Framework for .Net](https://developers.google.com/api-client-library/dotnet/apis/analytics/v3)  
