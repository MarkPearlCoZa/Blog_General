---
layout: post
title: MsBuild Notes
tags: MsBuild, Windows
category: Tech
---
MSBuild [msdn reference](http://msdn.microsoft.com/en-us/library/0k6kkbsd.aspx)  
  
Script everything but complie with MsBuild  
File extension .build  

#### Empty Build Script ####

~~~
<?xml version="1.0" encoding="utf-8"?>  
<project xmlns="http://schemas.microsoft.com/developers/msbuild/2003"  
	ToolsVersion="4.0">  
</project> 
~~~

#### Setting the default target ####

~~~
<?xml version="1.0" encoding="utf-8"?>  
<project xmlns="http://schemas.microsoft.com/developers/msbuild/2003"  
	ToolsVersion="4.0" 
	DefaultTargets="TargetName">  
</project>
~~~

Add a DefaultsTargets attribute to the project element with the TargetName being the name of the target.

#### Dependencies ####

~~~
  <Target Name="Clean">  
    <RemoveDir Directories=".\buildartifacts"/>  
  </Target>  

  <Target Name="Init" DependsOnTargets="Clean">  
    <MakeDir Directories=".\buildartifacts"/>  
  </Target>  
~~~

#### Compiling a VS Project ####

~~~
<Target Name="Compile">  
  <MSBuild Projects=".\HelloCI.sln" Targets="Rebuild" Properties="OutDir=C:\temp\"/>  
</Target>  
~~~

*Important note that the outdir cannot be a relative path, it has to be an absolute path with a trailing /

#### Properties ####

~~~~
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
~~~~

Reference a the above property by using the following syntax : $(BuildDir)  
  
You can have properties based off other properties.

~~~~
<PropertyGroup>
    <BuildDir>Build</BuildDir>
    <BuildFile>$(BuildDir)FileName.txt</BuildFile>
</PropertyGroup>
~~~~

#### Debugging ####

You can show values of parameters by using the Message Text

~~~
<Target Name="ShowReservedProperties">  
    <Message Text=" MSBuildProjectDirectory  = $(MSBuildProjectDirectory)" />   
    <Message Text=" MSBuildProjectFile  = $(MSBuildProjectFile)" />     
    <Message Text=" MSBuildProjectExtension  = $(MSBuildProjectExtension)" />   
    <Message Text=" MSBuildProjectFullPath  = $(MSBuildProjectFullPath)" />     
    <Message Text=" MSBuildProjectName  = $(MSBuildProjectName)" />     
    <Message Text=" MSBuildBinPath  = $(MSBuildBinPath)" />     
    <Message Text=" MSBuildProjectDefaultTargets  = $(MSBuildProjectDefaultTargets)" />     
    <Message Text=" MSBuildExtensionsPath  = $(MSBuildExtensionsPath)" />   
    <Message Text=" MSBuildStartupDirectory  = $(MSBuildStartupDirectory)" />
</Target>
~~~

#### Copying Files with Directory Structure ####

~~~
<ItemGroup>
  <out_files Include='output_dir/**/*'/>
</ItemGroup>

<Target Name='copy_files'>
  <Copy SourceFiles='@(out_files)' DestinationFolder='deployment_dir/%(out_files.RecursiveDir)'/>
</Target>
~~~

#### Moving Files ####

~~~
<Target Name="MoveSomeFiles">
    <Move
        SourceFiles="c:\Temp\File1.txt"
        DestinationFolder="@(TargetDirectory)"
    />
</Target>
~~~

#### Moving Files with Wildcards ####

You cannot use regular expression directly in task parameters. You need to create an item containing list of files to move and pass its content to the task:

~~~
<ItemGroup>
    <FilesToMove Include="c:\source\App_Web_*.dll"/>
</ItermGroup>
~~~

~~~
<Target Name="Build">
    <Move
        SourceFiles="@(FilesToMove)"
        DestinationFolder="C:\target"
    />
</Target>
~~~

Note the @ symbol is used to reference to item group compared to the $ to access properties.   
[see stack overflow for more info](http://stackoverflow.com/questions/12744826/how-do-i-move-a-bunch-of-files-using-a-move-msbuild-task-and-a-wildcard)

#### Exlcuding Files with WildCards ####

~~~
<ItemGroup>
    <ReportFiles Include="MaxCut.Reports.*.dll" Exclude="*.Interfaces.*;*.Tests.*"/>
</ItemGroup>
~~~

**Be aware of when the files of created that you are including in your Item Group - if they are being created dynamically, place the ItemGroup as a child element to the element that is generating the files [Read here for a further explanation](http://jon.netdork.net/2008/10/26/msbuild-and-evaluating-itemgroups/)

#### Overriding Parameters ####

There is a bug/feature in MSBuild which means that if you call CreateProperty and CallTarget in the same Target, your new property will not be [globally available to other targets](http://weblogs.asp.net/bhouse/440648).

~~~
<PropertyGroup>
   <DeployPath_TEST>\\test-server-path\websites\mysite</DeployPath_TEST>
   <DeployPath_LIVE>\\live-server-path\websites\mysite</DeployPath_LIVE>
   <DeployPath></DeployPath>
</PropertyGroup>

<Target Name="SetDeployPath-TEST">
  <CreateProperty Value="$(DeployPath_TEST)">
    <Output TaskParameter="Value" PropertyName="DeployPath"/>
  </CreateProperty>
</Target>

<Target Name="Deploy-TEST">
   <CallTarget Targets="SetDeployPath-TEST"/>
   <CallTarget Targets="Deploy-Sub"/>
</Target>
~~~

[See the stack overflow notes](http://stackoverflow.com/questions/1366840/overwrite-properties-with-msbuild)

#### Including Sub Files ####

~~~
<Import Project=".\Base.targets" />
~~~

Imports a base project, if you do imports multiple times of the same file you will get a warning, to avoid this do the following:

~~~
<Import Project=".\Base.targets"  Condition=" '$(BaseImported)' == '' "/>
~~~

And then in the base file add a property that is recognized

~~~
<PropertyGroup>
	<BaseImported>true</BaseImported>
</PropertyGroup>
~~~

[For more info on this see](http://stackoverflow.com/questions/2544926/how-to-get-import-custom-tasks-more-than-once-without-warning-message)


#### Executing a Build Script ####

Assume we had a build script called HelloCI.build with a target inside it called compile.  
To execute this specific target you would use the following command:  

~~~~
msbuild HelloCI.build /target:Compile
~~~~

#### Conditionally evaluate ItemGroup in MSBuild file ####

~~~
 <ItemGroup Condition="'$(Configuration)' == 'Debug'">
    <Content Include="EnvironmentSettings\Settings.xml">
      <SubType>Designer</SubType>
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </Content>
  </ItemGroup>
~~~

[For more info](http://stackoverflow.com/questions/8115696/conditional-content-based-upon-configuration)  

#### Refactoring MsBuild Scripts ####

[Great article on refactoring here.](https://timothystall.sys-con.com/node/253420/mobile)
