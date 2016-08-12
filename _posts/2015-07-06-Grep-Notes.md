---
layout: post
title: Grep Notes
tags: Linux
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

#### Move files that match a grep search

~~~
grep -l 'Search Statement' . | while read f; do mv "$f" targetDir; done
~~~

#### References ####

[Drew's grep tutorial](http://www.uccs.edu/~ahitchco/grep/)  
