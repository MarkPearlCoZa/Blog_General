---
layout: post
title: Python Notes
tags: 
category: Tech
---

Python is interpreted language
~~~
>>> means entering code into interpretor
~~~

Python is white space specific

#### Console

~~~
print("hello world")
age = input("Enter your age")
~~~

#### Numbers

Python has two types of numbers, ints and floats

Division returns a float

~~~
4 / 2 = 2.0
~~~

We can use integer division which requires a //

~~~
4 // 2 = 2
~~~

#### Variables

~~~
variable_name = 60 / 30
~~~

Naming rules: 
* no spaces and you cannot start a name with a special character
* we tend to use underscores to seperate names e.g. your_name

[See PEP 8 style guide](https://www.python.org/dev/peps/pep-0008/)  

#### Importing Modules

~~~
import math
math.ceil(1.23)
~~~

#### Strings

single or double quotes indicate a string

~~~
name = "Your Name"
print(name)
~~~

converting numbers to strings
~~~
name_and_age = "Mark Pearl" + str(35)
~~~

Strings are arrays

~~~
name = "hello_boy"
name[0]             # Returns the first element from the string - h
name[0:2]           # Slices name from 0 index to 2 index and returns he
name[:2]            # Shorthand for slicing from 0 to 2
name[2:]            # Shorthand for slicing from 2 to end of word
~~~

#### Conitionals

~~~
<       # Less than
<=      # Less or equal to
==      # Equal
>=      # Greater or equal
>       # Greater
!=      # Not equal to
~~~

If statements

~~~
num = 4

if num < 1:
    doSomething()
elif num < 5:
    doSomethingMore()
else:
    doSomethingElse()
~~~

#### Classes

~~~
class ClassName:

    def __init__(self, name):
        self.name = name


anObject = ClassName("this object")
print(anObject.name)
~~~

#### Lists 

~~~
mixed_list = ["one", 2 , "three"]       # one, 2, three
my_list = ["one", "two", "three"]
my_list.append("four")                  # one, two, three, four
my_list.delete("four")                  # one, two, three
del mylist(2)                           # one, two 
~~~

list equality requires each element in the list to be the same and the order to be the same

~~~
[1, 2, 3] == [3, 2, 1]      # return False
[1, 2, 3] == [1, 2, 3]      # return True
~~~

Getting the average of an list of numbers

~~~
def find_average(array):
    return sum(array) / len(array) if array else 0
~~~

#### Dictionaries

~~~
example_dict = {'key1':'value1', 'key2':'value2'}
print(example_dict['key1'])                         # prints value1

example_dict['key2'] = 'new value'                  
print(example_dict['key2'])                         # prints new value
del example_dict['key2']                            # deletes key value pair key2 from dictionary

result = example_dict['unknown key']                # result gets value None
if result:
    print(result)
else:
    print("key does not exist")


example_dict['new key'] = 'something new'           # adds a new key value pair to the dict
~~~

Dictionary equality requires each element in the dictionary to be the same but does not require the order to be the same

~~~
dict_1 = {1:1, 2:2, 3:3, 4:4}
dict_2 = {4:4, 3:3, 2:2, 1:1}
dict_1 == dict2                                 # return true
~~~

~~~
[1, 2, 3] == [3, 2, 1]      # return False
[1, 2, 3] == [1, 2, 3]      # return True
~~~

#### Conditionals

~~~
return "A" if x > 1 else "B"
~~~

#### For Loops

~~~
for n in range(50):
    ...
~~~

Looping through a dictionary

~~~
for key,item in dictionary.items():
    ...
~~~

#### While Loops

~~~
while x != 3:
    x = x + 1
~~~

or

~~~
while (True):
    if (x == 3): break
~~~

#### Functions

~~~
def function_name(param1):
  ...
  return ...
~~~

Main function - not required but a good pracice

~~~
def main():
    ...

main()
~~~

#### Object Orientation

#### Classes

Declaring a class with inheritance

~~~
class parent_class:
	pass
   
class child_class(parent_class): 
	pass
~~~

Instantiating a class

~~~
object = child_class()
~~~
