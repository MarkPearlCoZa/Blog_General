---  
layout: post  
title: The Art of Naming
tags: Learning  
category: General  
---  

The art of software prose...

#### Why Name things well

“There’s an important point to emphasize in this definition — code readability depends on who’s reading it, which means it’s subjective. It’s not an objective measure or score you can use to evaluate code.”

#### Useful questions

2 useful questions to ask when naming things…
 
1) What it is  
2) What it’s for  

#### Choose long names for long scopes and short names for short scopes

Originally from clean code book

#### Different things

- Data collections
- Processing / actions a system performs

#### Find a commong name

Having a universally accepted name for things is useful.

http://schema.org/

#### Meaningless is better than misleading

A name that has no meaning is better than a name that is misleading. Calling something blah is better than parseFile if parseFile actually doesn't parse file but does more or different behavior.

#### Common Names to look out for ####

Helper - 
Stuff -
Manager - 
Things - 
Collaborator - 
Processor -

#### Naming Progressions

Moving from Amount => Total

#### Names to consider ####

Consumer  
Command  
Factory  
Server  
Client  
Parser  
Cache  
Reader  
Writer  
Request  
Response  
Streams – like channels where data can flow through  
Readable  
Read  
Emitter – emit events  
Chunk  
Buffer  
Echo – repeating something we heard  
Pipe – streams the output of one operation to the input of the next one  
Request handlers -  
Payload -  
Filter - 
Transformer -  
Encoding - Decoding

Parse vs. Compose

Name the responsibility, not the thing. For example, if you think in terms of responsibilities, names of classes should describe behaviour, not things.

Patterns provide a base for names. For technical level solutions use well known pattern names if they match with what you are using. These are the ubiquotous names for the industry.


#### References ####

- [15 Words you need to eliminate from your Vocabulary](http://time.com/3851004/bad-vocabulary-eliminate/)  
- [Good naming is a progress not a single step](http://arlobelshee.com/good-naming-is-a-process-not-a-single-step)  
- Excerpt From: The Pragmatic Bookshelf. “PragPub 2016-09: Issue #87.” The Pragmatic Bookshelf, LLC, 2016-09-01. iBooks.  
