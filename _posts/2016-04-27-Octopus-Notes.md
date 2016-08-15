---
layout: post
title: Octopus Deploy  Notes
tags: Automation
category: Tech
---

#### Building a Project ####

Place build.bat, build.ps1 & build.sh in the same folder as the solution file.

The contents of the build.ps1 should be as follows:

~~~
param([string] $buildEnvironment = "Debug", [string] $packageForDeploy = "true", [string] $packageVersion = "0.0.0.0")

### Parameters:
# $buildEnvironment                 : The environment to build for eg. (Debug / Live).
# $packageForDeploy                 : Whether to package output for deployment.
# $packageVersion                   : The version number to use for the package.

### Other:
# OctoPackEnforceAddingFiles        : Set to true to enable packaging all build output files in addition to filespec in nuspec file.
# OctoPackPublishPackagesToTeamCity : Set to false to prevent OctoPack from publishing any packages to the build in TeamCity package feed.

$solutionPath = Join-Path $PsScriptRoot ".\KeyBlade.SupportPortal.sln"
msbuild $solutionPath /p:Configuration=$buildEnvironment /p:RunOctoPack=$packageForDeploy /p:OctoPackPackageVersion=$packageVersion /p:OctoPackEnforceAddingFiles=true /p:OctoPackPublishPackagesToTeamCity=false
if($LastExitCode -ne 0) {
    throw "MSBuild failed. See output for errors."
}
~~~

build.bat and build.sh merely point to the powershell file that then builds the project.

#### Generating Nuget Package to be consumed by Octopus ####

Make sure you have a nuspec file in the same folder of the project file (.csproj)

The contents of the file should look something like the following:

~~~
<?xml version="1.0"?>
<package xmlns="http://schemas.microsoft.com/packaging/2010/07/nuspec.xsd">
  <metadata>
    <id>Project ID</id>
    <title>Project Name</title>
    <version>1.0.0</version>
    <authors>Authors</authors>
    <owners>Owners</owners>
    <projectUrl>Project URL</projectUrl>
    <requireLicenseAcceptance>false</requireLicenseAcceptance>
    <description>Project Description</description>
    <releaseNotes>...state release changes here...</releaseNotes>
  </metadata>
</package>
~~~

Add a line entry to the csproj file of the project you want to package so that it generates the nupkg file.

It should look something like the following:

~~~
  <Import Project="..\..\..\Packages\OctoPack.3.0.39\tools\OctoPack.targets" Condition="Exists('..\..\..\Packages\OctoPack.3.0.39\tools\OctoPack.targets')" />
  <Target Name="EnsureOctoPackImported" BeforeTargets="BeforeBuild" Condition="'$(OctoPackImported)' == ''">
    <Error Condition="!Exists('..\..\..\Packages\OctoPack.3.0.39\tools\OctoPack.targets') And ('$(RunOctoPack)' != '' And $(RunOctoPack))" Text="You are trying to build with OctoPack, but the NuGet targets file that OctoPack depends on is not available on this computer. This is probably because the OctoPack package has not been committed to source control, or NuGet Package Restore is not enabled. Please enable NuGet Package Restore to download them. For more information, see http://go.microsoft.com/fwlink/?LinkID=317567." HelpKeyword="BCLBWebLD2001" />
    <Error Condition="Exists('..\..\..\Packages\OctoPack.3.0.39\tools\OctoPack.targets') And ('$(RunOctoPack)' != '' And $(RunOctoPack))" Text="OctoPack cannot be run because NuGet packages were restored prior to the build running, and the targets file was unavailable when the build started. Please build the project again to include these packages in the build. You may also need to make sure that your build server does not delete packages prior to each build. For more information, see http://go.microsoft.com/fwlink/?LinkID=317568." HelpKeyword="BCLBWebLD2002" />
  </Target>
~~~

This should be inserted near the end of the csproj file, typically just before "Enusre"NugetPackageBuildImports" target section.

#### References #### 

