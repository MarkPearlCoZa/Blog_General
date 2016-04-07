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

## String

#### Strip out Non Number / Alphabetic Characters ####

~~~
string word = "!@# Original Text 123 !@#";
string strippedWord = new String(word.Where( c => char.IsDigit(c) || char.IsLetter(c)).ToArray());
Assert.That(strippedWord, Is.EqualTo("OriginalText123");
~~~

#### Split string with sub string ####

~~~
var text = "this<>is<>it<>";
var splitText = text.Split(new[] { "<>" }, StringSplitOptions.None);
~~~

#### Convert to Title Case ####

~~~
var value = "some text here";
var result = CultureInfo.CurrentCulture.TextInfo.ToTitleCase(value.ToLower());
~~~

#### Creating a string for an array of characters ####

Previously I would do the following:

~~~
var chars = new [] {'a', 'b', 'c'};
var text = new string(chars);
~~~

A possibly cleaner syntaxt is...

~~~
var chars = new [] {'a', 'b', 'c'};
var text = string.Concat(chars);
~~~

## DateTime

#### Parsing DateTime from String in a specific format ####

~~~
DateTime theDate = DateTime.ParseExact(dateText, "yyyyMMdd", CultureInfo.InvariantCulture);
~~~

## Linq

#### Simulate a for Loop ####

~~~

var n = 10;
var values = Enumerable.Range(0, n).Select(DoSomething)
 
Private static decimal DoSomething(int n)
{
                Return n * 0.1M;
}
~~~

#### Cartesian Product ####

Suppose you want to create the cartesian product of two lists (every possible combination between the two collections). This can be done as follows:

~~~
var listA = new List<int> { 1, 2, 3 };
var listB = new List<int> { 4, 5, 6 };
var cartesianLst = listA.SelectMany(a => listB.Select(b => new Tuple<int, int>(a, b)));
~~~
