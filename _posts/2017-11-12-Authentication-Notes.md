---
layout: post
title: Authentication Notes
tags: 
category: Tech
---

### Session based authentication

* You authenticate with a use name and password
* Each request HTTP doesn't know anything about what happened before
* We use session/cookie based authentication to avoid having to supply a un/pw for each request  
* This makes the authentication process statefull (authentication record needs to be kept both client & server side)  
* Server keeps track of which sessions are active  
* On the front end a cookie is created that holds a session identifier  

**This is the most common form of authentication**  

#### Problems  

* Every time a user is authenticated, the server needs to create a record somewhere on the server, this is usually in memory and can add load to the server  
* Since sessions are stored in-memory you have scaling complications

### Token based authentication  

* token based authetication is stateless, no info is stored on the server or in a session 
* user enters login credentials, server verifies and returns a signed token
* this signed token is stored client-side, most commonly in local storage  
* subsequent requests to the server include this token in the header  
* server decodes the "token", if the token is valid it processes the request  
* Once a user logs out the token is destroyed client-side, no interaction with the server is needed  

#### Benefits  

* Completely stateless, server doesn not need to store any record of the user token sessions  
* Each token is self contained  

### Passwordless authentication  

* Send a link to access the site to your email etc.

### Other methods  

* Single sign on  
* Social sign in  

#### References  

[How do you authenticate mate?](https://hackernoon.com/how-do-you-authenticate-mate-f2b70904cc3a)  
