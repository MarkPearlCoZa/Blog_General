---
layout: post
title: F# – Depressingly simple text file access
tags: 
category: General
---
Today I was doing some work work and kept having to parse a log file. After a few hours of doing the same routine stuff I thought I might try and automate it using F#.

It was depressingly simple to achieve…

Example Extract of Text File

*ERROR*   : Drawing num {^BASE^2 }783, surface num 1 uses invalid real colour number 2 
_warning_ : The base file has 171 DLT types, the main file has 126. 
_warning_ : AutoPlan error: There are no base corner units with autoplan 30 (see theme 
*ERROR*   : Drawing num {^BASE^2 }790, surface num 1 uses invalid real colour number 5 
_warning_ : The base file has 171 DLT types, the main file has 126. 
_warning_ : AutoPlan error: There are no base corner units with autoplan 30 (see theme 
*ERROR*   : Drawing num {^BASE^10 }600401, surface num 1, is an alias that depends on a DLT type with no entries 
*ERROR*   : Drawing num {^BASE^10 }600405, surface num 1, is an alias that depends on a DLT type with no entries

So, what I wanted to achieve was to put all the Error entries together and then all the warning entries below it in a parse textfile..

The code looked something like this…

open System.IO
open System

let ParseFile = 
    let ParseFile = File.ReadAllLines("Z:\\HomeConcepts_07 Report.err")
    
    let ParseFileForErrors = 
        ParseFile
        |> Seq.filter(fun x -> if x.Contains("_warning_") then false else true)
    
    let ParseFileForWarnings = 
        ParseFile
        |> Seq.filter(fun x -> if x.Contains("_warning_") then true else false)

    let myFileSet = 
        let mySubFileSet = Seq.append ParseFileForErrors ParseFileForWarnings    
        let FileSummary = "Number of Entries : " + ParseFile.Length.ToString() + " Number of Errors : " + (ParseFileForErrors |> Seq.length).ToString()
        Seq.append ( FileSummary |> Seq.singleton) mySubFileSet
    
    File.WriteAllLines("Z:\\Test.txt", myFileSet)        

ParseFile
printfn "Done"

Explanation of Code

In ParseFile I create a sequence with each element as a line entry from the file.

I then filter the error elements, and generate a sequence, and do the same for the warning messages.

Finally in myFileSet I put all the sequences together and output them using the File.WriteAllLines
