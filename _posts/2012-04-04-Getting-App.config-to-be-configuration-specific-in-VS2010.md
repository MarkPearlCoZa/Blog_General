---
layout: post
title: Getting App.config to be configuration specific in VS2010
tags: 
category: General
---
I recently wanted to have a console application that had configuration specific settings. For instance, if I had two configurations “Debug” and “Release”, depending on the currently selected configuration I wanted it to use a specific configuration file (either debug or config).

If you are wanting to do something similar, here is a potential solution that worked for me.

Setting up a demo app to illustrate the point
First, let’s set up an application that will demonstrate the most basic concept.

using System;
using System.Configuration;

namespace ConsoleSpecificConfiguration
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Config");
            Console.WriteLine(ConfigurationManager.AppSettings["Example Config"]);
            Console.ReadLine();
        }
    }        
}
 

This does a really simple thing. Display a config when run.

To do this, you also need a config file set up. My default looks as follows…

<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <add key="Example Config" value="Default"/>
  </appSettings>
</configuration>
 

Your entire solution will look as follows…

ConsoleSpecificConfiguration - Microsoft Visual Studio (Administrator)_2012-04-04_10-14-52

Running the project you will get the following amazing output…

Debug_2012-04-04_10-16-41

 

Let’s now say instead of having one config file we want depending on whether we are running in “Debug” or “Release” for the solution configuration we want different config settings to be propagated across you can do the following…

Step 1 – Create alternate config Files
First add additional config files to your solution.

You should have some form of naming convention for these config files, I have decided to follow a similar convention to the one used for web.config, so in my instance I am going to add a App.Debug.config and a App.Release.config file BUT you can follow any naming convention you want provided you wire up the rest of the approach to use this convention.

My files look as follows..

App.Debug.config

<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <add key="Example Config" value="Debug"/>
  </appSettings>
</configuration>
 

App.Release.config

<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <add key="Example Config" value="Release"/>
  </appSettings>
</configuration>
 

Your solution will now look as follows…

ConsoleSpecificConfiguration - Microsoft Visual Studio (Administrator)_2012-04-04_10-26-10

Step 2 – Create a bat file that will overwrite files
The next step is to create a bat file that will overwrite one file with another.

If you right click on the solution in the solution explorer there will be a menu option to add new items to the solution.

Create a text file called “copyifnewer.bat” which will be our copy script.

It’s contents should look as follows…

@echo off
echo Comparing two files: %1 with %2

if not exist %1 goto File1NotFound
if not exist %2 goto File2NotFound

fc %1 %2 /A
if %ERRORLEVEL%==0 GOTO NoCopy

echo Files are not the same.  Copying %1 over %2
copy %1 %2 /y & goto END

:NoCopy
echo Files are the same.  Did nothing
goto END

:File1NotFound
echo %1 not found.
goto END

:File2NotFound
copy %1 %2 /y
goto END

:END
echo Done.
Your solution should now look as follows…

ConsoleSpecificConfiguration - Microsoft Visual Studio (Administrator)_2012-04-04_10-30-57
 

Step 3 – Customize the Post Build event command line
We now need to wire up everything – which we will do using the post build event command line in VS2010.

Right click on your project and go to it’s properties

ConsoleSpecificConfiguration - Microsoft Visual Studio (Administrator)_2012-04-04_10-32-28

We are now going to wire up the script so that when we build our project it will overwrite the default App.config with whatever file we want.

The syntax goes as follows…

call "$(SolutionDir)copyifnewer.bat" "$(ProjectDir)App.$(ConfigurationName).config" "$(ProjectDir)$(OutDir)\$(TargetFileName).config"

ConsoleSpecificConfiguration - Microsoft Visual Studio (Administrator)_2012-04-04_10-34-13

Testing it
If I now change my project configuration to Release

ConsoleSpecificConfiguration - Microsoft Visual Studio (Administrator)_2012-04-04_10-35-46

 

And then run my application I get the following output…

fileCUsersMQQDocumentsVisual Studio 2010ProjectsConsoleApplication16_2012-04-04_10-36-29

Toggling between Release and Debug mode will show that the config file is changing each time.

And that is it!