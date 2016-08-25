---
layout: post
title: "CORS in Action by Monsur Hossain"
description: "Creating and consuming cross-origin APIs"
tags: Book Web
category: Media
---

### Chapter 3 - Handling CORS Requests


Client origin

|         Server        | Origin                 | Same-origin request  |
|:---------------------:|------------------------|----------------------|
| http://127.0.0.1:9999 | http://127.0.0.1:9999  | Yes                  |
| http://127.0.0.1:9999 | https://127.0.0.1:9999 | No, different schema |
| http://localhost:1111 | http://localhost:9999  | No, different ports  |
| http://localhost:9999 | http://127.0.0.1:9999  | No, different hosts  |


### More info on book 

[Buy from Amazon](https://www.amazon.com/CORS-Action-Creating-consuming-cross-origin/dp/161729182X)  
ISBN-13: 978-1617291821  
