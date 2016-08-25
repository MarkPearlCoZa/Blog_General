---
layout: post
title: "CORS in Action by Monsur Hossain"
description: "Creating and consuming cross-origin APIs"
tags: Book Web
category: Media
---

### Chapter 3 - Handling CORS Requests

This chapter provided an overview of how CORS works from the server’s perspective. 

|         Server        | Origin                 | Same-origin request  |
|-----------------------|------------------------|----------------------|
| http://127.0.0.1:9999 | http://127.0.0.1:9999  | Yes                  |
| http://127.0.0.1:9999 | https://127.0.0.1:9999 | No, different schema |
| http://localhost:1111 | http://localhost:9999  | No, different ports  |
| http://localhost:9999 | http://127.0.0.1:9999  | No, different hosts  |


#### 3 key players 

The client, which initiates the cross-origin request
The browser, which manages the communication between the client and the server
The server, which serves data that the client wants

#### HTTP headers needed for a basic CORS request  

- The browser sends the Origin header to indicate where a request is coming from.
- An origin is defined as the scheme, host, and port portion of a URL.
- The server responds with the Access-Control-Allow-Origin header if the request is valid.

#### Access-Control-Allow-Origin header supports two values  

Setting the Access-Control-Allow-Origin header to * allows cross-origin requests from any client.
Setting the Access-Control-Allow-Origin header to a specific origin value only allows cross-origin requests from that specific client.

### More info on book 

[Buy from Amazon](https://www.amazon.com/CORS-Action-Creating-consuming-cross-origin/dp/161729182X)  
ISBN-13: 978-1617291821  
