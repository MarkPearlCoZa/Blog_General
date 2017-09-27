---
layout: post
title: tmux notes
tags: Linux 
category: Tech
---
  
#### Default Prefix Key  
  
C-b or control b, we represent this as P going forward  
  
#### Create sessions  

~~~  
tmux new -s basic  
~~~  

#### Detatching and Attatching to Sessions  

In Tmux to detatch  

~~~
P-d 
~~~
  
~~~
tmux ls                                 # lists tmux sessions
tmux attach                             # attaches to the session
tmux attach -t a_session_name           # attaches to the session called a_session_name
tmux kill-session -t _a_session_name    # kills a session called a_session_name
~~~

#### Creating windows in a session

~~~
P-c                                   # Creates a new window
P-n                                   # Moves to the next window
P-,                                   # Allows you to renames a windows
~~~

#### References  

[Basic tmux tutorial](https://www.youtube.com/watch?v=BHhA_ZKjyxo)  
[tmux man pages](http://man.openbsd.org/cgi-bin/man.cgi/OpenBSD-current/man1/tmux)  
