---
layout: post
title: Couch Db Notes
tags: Databases
category: Tech
---

#### Installation ####

#### Make Futon Accessible From External Ip's ####

Edit local.ini stored under /etc/couchdb  

In the file uncomment the bind_address. If you want any ip to have access to it, it should read...   

~~~
bind_address = 0.0.0.0
~~~

#### Restarting the Service ####

~~~
curl -X POST http://localhost:5984/_restart -H"Content-Type: application/json"
~~~

[see documentation](http://docs.couchdb.org/en/1.6.1/api/server/common.html#post--_restart)


#### References ####

