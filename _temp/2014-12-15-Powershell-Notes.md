---
layout: post
title: Powershell Notes
tags: Powershell
category: General
---
#### Enable running PowerShell Scripts ####

- Start Windows PowerShell with "Run as Administrator"  
- Execute the code below to allow for scripts to run  

~~~
set-executionpolicy remotesigned
~~~

#### Run PowerShell Script from Command Line ####

~~~
powershell ./'PowerShell File.ps1'
~~~

----------------------------------------------------------------------------------------

#### Making absolute path referencing ####

~~~
$solutionRoot = Split-Path $script:MyInvocation.MyCommand.Path
~~~

#### Basic Files Commands ####

##### Creating a Folder and Child Folders #####

~~~
New-Item -ItemType Directory -Force -Path C:\Path\That\May\Or\May\Not\Exist
~~~

##### Delete a Folder with all Children #####

~~~
Remove-Item -Recurse -Force C:\Path\
~~~

##### Delete a Folder with all Children if it does not exist #####

~~~
$FolderName="c:\temp\"

If (Test-Path $FolderName){
	Remove-Item  -Recurse -Force $FolderName
}
~~~

##### Copy Files from one location to another #####

~~~
Copy-Item -Path C:\MyFolder -Destination \\Server\MyFolder -recurse -Force
~~~

##### RegSvr32 #####

~~~
iex "regsvr32 /s file.dll"
~~~

##### Commenting out a line of code #####

~~~
# This is a comment in Powershell
~~~

----------------------------------------------------------------------------------------

#### Open PowerShell CLI on remote machine ####

~~~
Enter-PSSession -ComputerName {MachineNameHere} -Credential {CredentialsHere}
~~~

----------------------------------------------------------------------------------------

#### Unit Testing in Powershell ####

Look at Pester as a possible Powershell Unit Testing Framework

#### References ####
[Testing in Powershell](https://www.simple-talk.com/sysadmin/powershell/practical-powershell-unit-testing-checking-program-flow/?utm_source=simpletalk&utm_medium=email-main&utm_content=practicalps3-20141208&utm_campaign=sysadmin)

