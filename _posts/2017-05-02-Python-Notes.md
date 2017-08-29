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

#### Classes

~~~
class ClassName:

    def __init__(self, name):
        self.name = name


anObject = ClassName("this object")
print(anObject.name)
~~~
