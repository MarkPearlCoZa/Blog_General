---
layout: post
title: Ruby Notes
tags: Languages
category: Tech
---
### The Basics

#### Converting Types

- to_s converts to string
- to_i converts to integer
- to_a converts to array

#### Working with Variables

Exlamation Points - methods may have exclamation points in their name, which just means to impact the current data rather than making a copy.  

#### Working with Arrays

Basic declaration

~~~
values = [1, 2, 3]          # declares a simple array
maxValue = [1, 2, 3].max    # gets the largest value 
~~~

#### Working with Dictionaries / Hashes

Pairs up a key with a value.  

Basic declaration  

~~~
object = {}                 # declares an empty hash
object = Hash.new(0)        # another way to declare a empty hash
object['key'] = :aValue     # adds a value with key with the symbol :aValue
~~~

#### Working with Symbols


#### Loops

~~~
hashExample = {}
hashExample['key1']=:value1
hashExample['key2']=:value2
hashExample.values.each { |value| newHash[value] += 'set value'}

hashExample # {:value1=>"set value", :value2="set value"}
~~~

### Installation

#### Updating Ruby in Ubuntu

rbenv is a tool for installing versions of ruby. To install rbenv use the following:

~~~
sudo apt-get install rbenv
~~~

To use rbenv here are some common commands:  

~~~
rbenv install 2.2.3
rbenv use 2.2.3
ruby -v
~~~

#### References ####

