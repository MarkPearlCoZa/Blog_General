---
layout: post
title: Riak Notes
tags: Databases
category: Tech
---

### Ruby Stuff ###

#### Installing Gems ####

~~~
gem install riak-client json
~~~

#### Connecting ####

~~~
require 'riak'
client = Riak::Client.new(:host => "192.168.56.22", :pb_port => 10017)
client.ping()
~~~

#### Writing to a bucket ####

~~~
my_bucket = client.bucket("test")
obj1 = my_bucket.new('one')
obj1.data = 1
obj1.store()
~~~

#### References ####

[Connecting to Ruby](https://github.com/basho/riak-ruby-client/wiki/Connecting-to-Riak)
[The Little Riak Book](http://littleriakbook.com/)

