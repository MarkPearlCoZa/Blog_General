---
layout: post
title: CSharp Notes
tags: Language
category: Tech
---

#### Null-Coalescing (??) Operator #### 

~~~
string something = null;
string another = something ?? "Is currently null";

// another = Is currently null
~~~

#### Ternary (?) Operator 

~~~
string name1 = "1234";
string name2 = "123456";
var valueLessThanFive = name1.Length < 5 ? name1 : name2;

// valueLessThanFive = 1234
~~~
