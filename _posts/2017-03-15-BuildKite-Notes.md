---
layout: post
title: BuildKite Notes
tags: 
category: Tech
---

# MacOS

Get builkite agent info 

~~~
brew info buildkite-agent
~~~

## Handling multiple ssh agent keys

[Read using multiple keys with ssh-agent](https://buildkite.com/docs/agent/ssh-keys)  

In Enviroment agent hook

~~~
 set -eu
 export SSH_AUTH_SOCK="~/.ssh/ssh-agent.sock"
~~~

To setup ssh-agent

In ~/.ssh/config make sure you have  

~~~
Host *
    AddKeysToAgent yes
    UseKeychain yes
~~~

Also, make sure ssh-add has been performed with the passphrase 

~~~
ssh-add -K
~~~
