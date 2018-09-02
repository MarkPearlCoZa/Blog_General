---
layout: post
title: Git Revisited
tags: 
category: General
---
Having worked with TFS & SVN for a while now, I recently was put in a position where I had to get up to speed with Git. My only experience with Git up to now was attending a brief presentation on the subject and spending a few hours playing around with it – interesting at the time, but foreign enough for me not to hold any strong opinions on the matter.

For the last two weeks I have had to get exposure to Git, and after getting over the initial “uncomfortable” stage I must say that Git is seeming more and more like the way to go in certain scenarios. Below are some of the items that appealed to me.

Single Git file in root of Git Repository vs tracking changes on a file to file basis

With SVN I found irritating .svn folders in every sub directory of a SVN repo. This is fine 90% of the time until something breaks and you need to change the repo or do some fringe case fixing. with Git it places a single .get folder in the root of the repository and leaves all the sub directories clean. This is a lot easier to handle, especially if you copy files from one repo to another because you I do not have to worry about version control getting messed up because of conflicts of hidden sub folders – this was always a concern with SVN.

Branching on Local Machine

The idea of branching for each feature and then merging those branches back to the master branch once a feature is completed has some real benefits. I have been using the branch by feature approach (meaning every new feature that I develop I create a branch for) and I am absolutely enjoying it. If I totally mess things up on one of my features, no problem - simply drop the branch and start again. In my experience I found with SVN and TFS that branching wasn’t part of my day to day routine. With SVN in particular we were so scared of branching because once or twice we messed things up and had no clue what had gone wrong. With Git I am a lot more confident to branch.

Console Based Commands

So, I never thought I would be saying this. I am a windows guy by nature and like pointy clicky things, but with most of my exposure to Git being console based via Git Bash I am really enjoying the console approach. I found that when coding I am typically keyboard based. Because I can alt+tab into git and branch and alt-tab back without having to touch the mouse is really appealing. Another benefit of the console is that I can fast track some of the most common commands I have with scripts, streamlining the process even more. Having a console approach is not necessarily something specific to Git, but something I enjoy as a by product of getting exposure to the system.

Being able to Push Repositories between machines

I have a feature I have finished and I want a tester to check it and look for fringe cases. With Git the tester can easily pull my feature repository to her machine, do the tests and make changes without messing around with a central server repository. I have found this to be particularly useful. With TFS & SVN I would have to commit my changes to the server on a branch, then the tester would need to checkout the branch and make do her stuff. It just seems easier this way.

Conclusion

Still early days with Git. I do not profess to be an expert on SVC systems but as a novice user I definitely am enjoying a different approach in tackling what is a fundamental problem for software development.