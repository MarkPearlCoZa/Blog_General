---
layout: post
title: tmux notes
tags: Linux 
category: Tech
---

#### Config file locations

~~~
/etc/tmux.conf              # system wide configuration
~/.tmux.conf                # user configuration
~~~

#### Config Settings

~~~
setw -g pane-base-index 1           # sets the starting pane index to 1

# moving between panes with Prefix h,j,k,l
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R
~~~
  
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
P-?                                   # Tmux Command Help
P-c                                   # Creates a new window
P-n                                   # Moves to the next window
P-,                                   # Allows you to renames a windows
~~~

#### Working with pains

~~~
P-%                                 # Horizontal pane split
P-"                                 # Vertical pane split
P-Arrow Key                         # Move focus to pain
P-Space                             # Cycle through different pane arrangements
P-x                                 # Close a pane
~~~

### Tmuxinator

~~~
tmuxinator open development         # opens the default project configuration for tmuxinator
tmuxinator development              # starts tmux with the development environment
tmuxinator debug development        # displays the script that tmuxinator will use
tmuxinator list                     # Lists all current projects.
tmuxinator copy source destination  # Copies a project configuration.  
tmuxinator implode                  # Deletes all current projects.  
tmuxinator doctor                   # Looks for problems with the tmuxinator and system configuration.
tmuxinator delete [name]            # Deletes the specified project.
~~~

default config files for tmuxinator are located at ~/.tmuxinator



#### References  

[Basic tmux tutorial](https://www.youtube.com/watch?v=BHhA_ZKjyxo)  
[tmux man pages](http://man.openbsd.org/cgi-bin/man.cgi/OpenBSD-current/man1/tmux)  
