---
layout: post
title: xcopy file, suppress “Does xxx specify a file name…” message
tags: 
category: Tech
---
Today we had an interesting problem with file copying. We wanted to use xcopy to copy a file from one location to another and rename the copied file but do this impersonating another user. Getting the impersonation to work was fairly simple, however we then had the challenge of getting xcopy to work. The problem was that xcopy kept prompting us with a prompt similar to the following…

Does file.xxx specify a file name or directory name on the target (F = file, D = directory)?

At which point we needed to press ‘Y’.

This seems to be a fairly common challenge with xcopy, as illustrated by the following stack overflow link…

One of the solutions was to do the following…

echo f | xcopy /f /y srcfile destfile

This is fine if you are running from the command prompt, but if you are triggering this from c# how could we daisy chain a bunch of commands….

The solution was fairly simple, we eventually ended up with the following method…

public void Copy(string initialFile, string targetFile)
        {            
            string xcopyExe = @"C:\windows\system32\xcopy.exe";
            string cmdExe = @"C:\windows\system32\cmd.exe";

            ProcessStartInfo p = new ProcessStartInfo();
            p.FileName = cmdExe;            
            p.Arguments = string.Format(@"/c echo f | {2} {0} {1} /Y", initialFile, targetFile, xcopyExe);
            Process.Start(p);            
        }
Where we wrapped the commands we wanted to chain as arguments and instead of calling xcopy directly, we called cmd.exe passing xcopy as an argument.