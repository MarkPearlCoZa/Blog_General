---
layout: post
title: Regex Notes
tags: Useful
category: Programming
---
### Two parts of a regex ###

1) Subject string (the text beig parsed)  
2) Regex (group of characters that represent rules for matching / searching text)  

### Check if the first occurance is followed by a pattern ###

For example: check if first occurance of x is followed by 2 x`s

~~~
^[^x]*xxx
~~~

#### Matching Any and No Characters ####

This is a bit of a hack because of special characters...   

[\S\s] == any character

### Operators ###

#### Or Operator ####

| is the or operator, in the example below it would return true if your input has the numbers 407 OR 321 in the subject string.  

~~~
/407|321/
~~~

In CSharp, the following would happen...

~~~
var result1 = Regex.IsMatch("1240756", "407|321"); // return true  
var result2 = Regex.IsMatch("5555555", "407|321"); // return false  
var result2 = Regex.IsMatch("0000321", "407|321"); // return true  
~~~

#### + Operator ####

Repeat the character one or more times until it is no longer matched

~~~
/ar+/
~~~

The above matches on ar, arr, arrr, arrr... etc.

### Anchors ###

$ End of line  
^ Start of Line
\b Word boundary (useful for matching whole words only)   

### Character Sets ###

Use a [] to represent a character set, for example matching all letters in the alphabet could be achieved as follows:

~~~
[a-z]
~~~

Note:
- A range only works in a character set.  
- A character set represents 1 character in our subject text.  

~~~
[a-z\s] - matches characters and white space
[0-9] - matches on numbers
[a-z0-9\s] - matches small letters, numbers and whitespace
\d - represents a number meta character and is equivalent to [0-9]  
\w - represents the word meta character and is equivalent to [a-zA-Z0-9]
\s - represents white space
~~~

You can use the ^ symbol to repsent negating the preceeding pattern.

~~~
[^\d]
~~~

It can sometimes be confusing on what the ^ represents because it has different meanings depending on its location.

[^\d] == \D (match every character except numbers  
[^\s] == \S (match every character except white space  
[^\w] == \W (match every character except words  

#### Matching a specific number of times with internal expressions ####

~~~
[a-z]{2}
~~~

The above matches two characters.

~~~
[a-z]{1,3}
~~~

The above matches 1-3 characters.

~~~
[a-z]{3,}
~~~

The above matches a minimum of 3 characters and more

#### Matching multiple characters ####

You can use the + operator after a character set to represent that it must match one or more characters

~~~
[a-z]+
~~~

You can use the * operate after a character set to represent that it must match zero or more characters

~~~
[a-z]*
~~~

#### Modifiers ####

\i - ignore case modifier
\m - multi line modifier (changes the anchors so that ^ anchors to the beginning of every line and $ anchors to the end of every line


#### Matching Case ####

~~~
[a-zA-Z]
~~~

Alternative... 

[a-z]\i

The above uses the ignore case modifier. Modifiers are language specific, so check documents to make sure you have the correct modifier for a specific language (e.g. ruby, c#, etc).

Or

~~~
(?i)word1|word2|word3
~~~

#### Wildcard ####

\ represents ...
? represents an optional pattern that will match the pattern 0 to 1 times, matching as few times as possible
. representes a wildcard metacharacter that will match any character except the newline character  

To use the '.' in as a character you need to escape it

~~~
\.
~~~


Characters that have a special meaning can be escaped with a backslash to use their literal meaning.

#### Groups ####

Use prenthesis to create groups.

~~~
/\w+@\w+\.(com|net|org|edu)/
~~~

The () section indicates that any one of these can be in the space.

##### Non-capturing Groups #####

?: - is known as a non-capturing group and can be used to cause a match without returning it.

~~~
(?:street|lane)
~~~

Another example would be below where it finds a match for http or ftp but does not include it in a match.

~~~
(?:http|ftp)
~~~

#### Capturing Groups #####

Use a group (), to return a capture group

~~~
\b(/gold)\b
~~~

Returns only whole words matching gold from the sentence below (in this case 3 golds)

gold metal golden wood gold plastic metal stone rubber gold

### Whitespace ###

\s represents spaces, tabs, new lines

~~~
/Captain\shook/
~~~

### Useful Examples ###

Add a word egg after certain letters (bcd) with a word.  

~~~
word.replace(/[bcd]/ig, "$&egg")
~~~

### Misc ###

[] Ranges  
{} Multipliers  

### Tools ###

[Regex 101](https://regex101.com/) - general regex tool  
[Verbal Expressions](https://github.com/VerbalExpressions/JSVerbalExpressions) - a js library that helps you construct difficult regex expressions  
[Regex Query Analyzer](http://www.regexr.com/)  
[Rubular](http://rubular.com/) - ruby regex tool  
[LearnPython.org Regular Expressions](http://www.learnpython.org/en/Regular_Expressions) - python regex resources  
[Ruby Regular Expressions](http://doc.infosnel.nl/ruby_regular_expressions.html) - ruby regular expression resources  
[Oracle Regex Pocket Reference](https://www.safaribooksonline.com/library/view/oracle-regular-expressions/0596006012/) - regex for DB's  
[Regular Expression Part VI](http://www.lunametrics.com/blog/2006/10/04/regular-expressions-part-vi-or/)  

### Books ###

[Learn RegEx the Hard Way](http://regex.learncodethehardway.org/book/)  
[Regular Expression for Javascript](http://eloquentjavascript.net/09_regexp.html)  
