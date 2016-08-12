---
layout: post
title: XClip Notes
tags: Linux
category: Tech
---

## Basic Use ##

### Copy text to clipboard  

~~~
cat sometextfile.txt | xclip -selection c
~~~

### Paste text from clipboard

~~~
xclip -o > helloworld.txt
~~~

#### Misc 

Add the following to alias to default xclip to normal clipboard

~~~
alias xclip='xclip -selection c'
~~~

#### References 

[Man Page for XClip](http://linux.die.net/man/1/xclip)  
[XClip - Useful from the command line](https://elcasey.wordpress.com/2008/02/12/xclip-use-the-clipboard-from-the-command-line/)  
