---
layout: post
title: Getting Jenkins to ignore the exit code if failure
tags: 
category: General
---
Today I had an issue with Jenkins where I wanted it to perform a set of tasks, but not worry about the exit code of any of the tasks…. In my instance I was using Jenkins to run DotCover to check the code coverage of a solution and then run a custom application to make sure the coverage was sufficient….The challenge I was facing that for DotCover to generate coverage statistics, it would need to run NUnit. If a test in NUnit failed for some reason, regardless of the the total coverage of the tests Jenkins would fail the job.

In my scenario, I wanted Jenkins to ignore whether the tests passed or failed and just examine the code coverage as I had other jobs doing this and wanted this job in Jenkins to be focused on one item. After some time I finally came up with a configuration that worked.

We were executing the tasks through a windows batch command, to suppress the exit code of nunit, I added an exit command to the end of the batch file and set manually overrode the exit code… This worked, life goes on.

So, using EXIT /B 0 was the solution

Test Config [Jenkins] - Dashboard [Jenkins]_2011-12-15_14-00-10