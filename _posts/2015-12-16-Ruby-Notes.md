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

### Working with Arrays

Basic declaration

~~~
values = [1, 2, 3]          # declares a simple array
maxValue = [1, 2, 3].max    # gets the largest value 
~~~

#### Filtering Arrays (Reduce)

~~~
[1, 2, 3, 4, 5].select {|n| n % 2 == 0}  # Should return [2, 4]
~~~

### Dividing Arrays into Groups (Partition)

~~~
[1, 2, 3, 4, 5].partition {|n| n % 2 == 0} # Should return [[2, 4],[1, 3, 5]]
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

### Classes

~~~
class TheClass
end
~~~

Class names start with a capital letter and use CamelCase

#### Initialization / Constructors

~~~
class TheClass
    def initialize(name, age)               # Equivalent to constructor
        @name = name
        @age = age
    end
end

instanceObject = TheClass.new("Mark", 36)   # Newing up an instance
~~~

#### Inheritance

Ruby can only have single inheritance, multiple inheritance is not supported. Inheritance is for reusing functionality, not enforcing interfaces.

~~~
class ParentClass
    def DoSomething()
    end
end

class InheritedClass < ParentClass
    def DoSomething()
        super.DoSomething()
    end
end

class AnotherInheritedClass < ParentClass
end
~~~

#### Class Methods 

~~~
class TheClass
    def self.methodToCall
        2
    end
end

TheClass.methodToCall

#### Class Variables

- denoted with @@  
- are not used often  
- class variables are shared across all inherited classes

class TheClass
    @@classVariable = 2
end
~~~

#### Class Instance Variables

class TheClass
   @classInstanceVariable = 2

    def self.classInstanceVariable
        @classInstanceVariable
    end 
end 

TheClass.classInstanceVariable

#### Method Visibility

~~~
class TheClass
    private def privateMethodName
    end
end
~~~

#### Open Classes

~~~
class TheClass
    def Method1
    end
end

class TheClass
    def Method2
    end
end
~~~

Is equivalent to...

~~~
class TheClass
    def Method1
    end
    
    def Method2
    end
end
~~~

#### Shallow copy of objects

~~~
b = a.clone
~~~

#### Instance Variables

~~~
class TheClass
    ...
    def method(variableParam)
        @instanceVariable = varialbeParam
        ...
    end
end
~~~

- Instance variables are private by default
- Instance methods are public by default

#### Accessors

~~~
class TheClass
    attr_accessor: instanceVariable
end
~~~

An accessor does the equivalent code

~~~
class TheClass
    def instanceVariable
        @instanceVariable
    end

    def instanceVariable=(new_value)
        @instanceVariable = new_value
    end
end
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

[Official Ruby Documentation](https://ruby-doc.org)  
