---
layout: post
title: Cron Notes
tags: Linux
category: Tech
---
#### General Notes ####

Custom cron jobs are stored in /etc/crontab  
Cron jobs cannot run more frequently than every minute  

#### Editing Cron Jobs ####

To edit the crontab for the current user type...  

~~~
crontab -e
~~~

To edit the crontab for the root user type...  

~~~
sudo crontab -e
~~~

#### Format ####

**minute** **hour** **dom** **month** **dow** **user** **cmd**

**minute**	Minute of the hour the command will run on, and is between '0' and '59'  
**hour**	Hour the command will run on, and is specified in the 24 hour clock, values must be between 0 and 23 (0 is midnight)  
**dom**		Day of Month, that you want the command run on, e.g. to run a command on the 19th of each month, the dom would be 19.  
**month**	The month a specified command will run on, it may be specified numerically (0-12), or as the name of the month (e.g. May)  
**dow**		The Day of Week that you want a command to be run on, it can also be numeric (0-7) or as the name of the day (e.g. sun).  
**user**	The user who runs the command.  
**cmd**		The command that you want run. This field may contain multiple words or spaces.  

#### Run something every minute ####

~~~~
*/1 * * * * root echo "This command is run every minute"
~~~~

#### Run something every 5 minutes ####

~~~~
*/5 * * * * root echo "This command is run every 5 minutes"
~~~~


#### References ####

[Introduction to Cron](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)  

