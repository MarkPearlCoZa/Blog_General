---
layout: post
title: GitHub Notes
tags: Web
category: Tech
---

#### Having GH-Pages A Subdirectory ####

Make sure you do not currently have a gh-pages branch

~~~
git subtree push --prefix docs origin gh-pages // Replace 'docs' by your folder name
~~~

[Orignally found here](http://gsferreira.com/archive/2014/06/update-github-pages-using-a-project-subfolder/)  

#### Querying Issues from PostMan

"https://api.github.com/repos/<repo-owner>/<repo-name>/issues"

If you have 2FA enabled, add the following header with your current 2FA code

X-GitHub-OTP

Increase number of items in page response

per_page=100000

#### References ####

