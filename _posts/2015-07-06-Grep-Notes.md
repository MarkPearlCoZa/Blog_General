---
layout: post
title: Grep Notes
tags: Useful
category: Tech
---

#### Search for text in all files in sub-directories ####

Search all files for matching text - show positions in files...

~~~
grep -r "TextToSearch" .
~~~

Search all files for matching text - show just the file name with the match...

~~~
grep -rl "StuffToSearch" .
~~~

Or...

~~~
grep -rl "StuffToSearch" .
~~~

~~~
grep -rli "StuffToSearch" *
~~~

#### References ####

[Drew's grep tutorial](http://www.uccs.edu/~ahitchco/grep/)  
