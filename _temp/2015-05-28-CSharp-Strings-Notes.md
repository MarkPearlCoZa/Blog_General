---
layout: post
title: CSharp Strings Notes
tags: Language
category: General
---

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
