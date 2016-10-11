---
layout: post
title: Ruby Notes
tags: Languages
category: Tech
---
## The Basics

### Types

#### Regex Type

Basic use...

~~~
m = /.*/.match("some input text")
~~~

### Converting Types

- to_s converts to string
- to_i converts to integer
- to_a converts to array

### Working with Variables

Exlamation Points - methods may have exclamation points in their name, which just means to impact the current data rather than making a copy.  

## Operators

#### Tenary Operator 

() ? ... : ...

~~~
x = 1
(x == 1) ? "one" : "other"
~~~

Equivalent to...

~~~
x = 1
if (x == 1) then "one" else "other" end
~~~

#### Spaceship Operator 

... <=> ...

~~~
x = -50
y = 32
return x <=> y    # return -1
~~~

Instead of returning 1 (true) or 0 (false) depending on whether the arguments are equal or unequal, the spaceship operator will return 1, 0, or −1 depending on the value of the left argument relative to the right argument.

given 

~~~
a <=> b 
~~~

if a < b then return -1  
if a = b then return  0  
if a > b then return  1  
if a and b are not comparable then return nil  

### Working with Strings

#### Convert String to Array

~~~
text = "hello"
text.split("") # ['h','e','l','l','o']
~~~

alternatively...

~~~
text = "hello"
text.chars() # ['h','e','l','l','o']
~~~

#### Checking variable is an array

~~~
def doSomething(list)
    list.kind_of?(Array) ? "Is an Array" : "Is something else"
end
~~~

#### Substitute / Replace Regex Match

~~~
"some text".gsub(/text/,'foo') # returns some foo
~~~

-----------------------------------------------------------------------------------------------------------------------------

## Working with Arrays

- [Map, Select and other Enumerable Methods Explained](http://www.eriktrautman.com/posts/ruby-explained-map-select-and-other-enumerable-methods)  

#### Basic declaration

~~~
values = [1, 2, 3]          # declares a simple array
maxValue = [1, 2, 3].max    # gets the largest value 
~~~

### Enumerable Methods

#### Select 

~~~
[1, 2, 3, 4, 5].select {|n| n % 2 == 0}  # Should return [2, 4]
~~~

#### Each / Each_with_index

~~~
[1, 2, 3].each { |num| print "hello #{num}! "}
[1, 2, 3].each_with_index { |element, index| print "hello #{num}! "}
~~~

Does the funciton on each element in the array and then returns the ORIGINAL array

#### Collect / Map 

~~~
[1, 2, 3].collect { |num| num*num } # returns 1, 4, 9
[1, 2, 3].map { |num| num*num }     # returns 1, 4, 9
~~~

#### Inject / Reduce 

~~~
[1, 2, 3].reduce(0){|running_total, item| running_total + item} # returns 6
~~~

Alternatively...

~~~
[1, 2, 3].inject(0){|running_total, item| running_total + item} # returns 6
~~~

#### Dividing Arrays into Groups (Partition)

~~~
[1, 2, 3, 4, 5].partition {|n| n % 2 == 0} # Should return [[2, 4],[1, 3, 5]]
~~~

### Other

#### Colon-Plus, Colon-Star

Colon-Plus, Colon-Star are symbls

~~~
[1, 2, 3].inject(:+) # Equivalent to [1,2,3].inject(0){|total, num| total + num} 
[1, 2, 3].inject(:*) # Equivalent to [1,2,3].inject(0){|total, num| total * num} 
~~~

## Dictionaries / Hashes

Pairs up a key with a value.  

#### Basic declaration  

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

-----------------------------------------------------------------------------------------------------------------------------

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

#### Monkey Patching

Google it...

#### Equality

Custom equality on objects can be achieved using ==(other) syntax...  

~~~
class TheClass
    attr_reader :name

    def initialize(name)
        @name = name
    end

    def ==(other)
        name == other.name
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

-----------------------------------------------------------------------------------------------------------------------------

### Blocks

#### Multi Line Blocks

~~~
def blockName
    [1, 2, 3].each do 
    print "hello"
end
~~~

#### Single Line Blocks

~~~
[1, 2, 3].each { |element| print "hello" }
~~~

#### Executing passed blocks 

~~~
def count (list, &block)
	list.count(&block)
end

list = [0,1,2,3,5,8,13, 13]
count(list,{|item| item == 13})
~~~

#### Check if block is given

~~~
def compute(&block)
    if (block_given?)
        puts "defined"
    else
        puts "not defined"
    end
end
~~~

[Read blocks demystified](http://www.skorks.com/2013/04/ruby-ampersand-parameter-demystified/)  

-----------------------------------------------------------------------------------------------------------------------------

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
[Ruby Online Repl](https://repl.it/languages/ruby)  
