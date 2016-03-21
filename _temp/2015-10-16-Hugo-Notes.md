---
layout: post
title: Hugo Notes
tags: Hugo
category: General
---

#### Ubuntu ####

Install Hugo in Ubuntu
~~~
mkdir -p ~/opt/packages/hugo && cd $_

wget https://github.com/spf13/hugo/releases/download/v0.13/hugo_0.13_linux_amd64.tar.gz

gzip -dc hugo_0.13_linux_amd64.tar.gz | tar xf -

rm hugo_0.13_linux_amd64.tar.gz
~~~

Add hugo to your PATH
~~~
mkdir ~/bin

ln -s ~/opt/packages/hugo/hugo_0.13_linux_amd64/hugo_0.13_linux_amd64 ~/bin/hugo

source ~/.profile

which hugo

hugo version
~~~

#### References ####

[Installing Hugo in Ubuntu](http://exponential.io/blog/2015/02/25/install-hugo-on-ubuntu-linux/)  
