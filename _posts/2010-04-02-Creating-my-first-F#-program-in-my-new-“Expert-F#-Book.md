---
layout: post
title: Creating my first F# program in my new “Expert F# Book
tags: 
category: General
---
 

So I have a brief hour or so that I can dedicate today to reading my F# book. It’s a public holiday and my wife’s birthday and I have a ton of assignments for UNISA that I need to complete – but I just had to try something in F#.

So I read chapter 1 – pretty much an introduction to the rest of the book – it looks good so far. Then I get to chapter 2, called “Getting Started with F# and .NET”. Great, there is a code sample on the first page of the chapter. So I open up VS2010 and create a new F# console project and type in the code which was meant to analyze a string for duplicate words…

~~~
#light

let wordCount text = 
    let words = Split [' '] text
    let wordset = Set.ofList words
    let nWords = words.Length
    let nDups = words.Length - wordSet.Count
    (nWords, nDups)

let showWordCount text =
    let nWords,nDups = wordCount text
    printfn "--> %d words in text" nWords
    printfn "--> %d duplicate words" nDups
~~~

So… bad start - VS does not like the “Split” method. It gives me an error message “The value constructor ‘Split’ is not defined”. It also doesn’t like wordSet.Count telling me that the “namespace or module ‘wordSet’ is not defined”.

??? So a bit of googling and it turns out that there was a bit of shuffling of libraries between the CTP of F# and the Beta 2 of F#. To have access to the Split function you need to download the F# PowerPack and hen reference it in your code…

I download and install the powerpack and then add the reference to FSharp.Core and FSharp.PowerPack in my project. Still no luck!

Some more googling and I get the suggestions I got were something like this…

#r "FSharp.PowerPack.dll";;
#r "FSharp.PowerPack.Compatibility.dll";;

So I add the code above to the top of my Program.fs file and still no joy… I now get an error message saying…

Error    1    #r directives may only occur in F# script files (extensions .fsx or .fsscript). Either move this code to a script file, add a '-r' compiler option for this reference or delimit the directive with '#if INTERACTIVE'/'#endif'.

So what does that mean? If I put the code straight into the F# interactive it works – but I want to be able to use it in a project. The C# equivalent I would think would be the “Using” keyword. The #r doesn’t seem like it should be in the FSharp code.

So I try what the compiler suggests by doing the following…

#if INTERACTIVE
#r "FSharp.PowerPack.dll";;
#r "FSharp.PowerPack.Compatibility.dll";;
#endif

No luck, the Split method is still not recognized. So wait a second, it mentioned something about FSharp.PowerPack.Compatibility.dll – I haven’t added this as a reference to my project so I add it and remove the two lines of #r code.

Partial success – the Split method is now recognized and not underlined, but wordSet.Count is still not working. I look at my code again and it was a case error – the original wordset was mistyped comapred to the wordSet. Some case correction and the compiler is no longer complaining. So the code now seems to work… listed below…

~~~
#light

let wordCount text = 
    let words = String.split [' '] text
    let wordSet = Set.ofList words
    let nWords = words.Length
    let nDups = words.Length - wordSet.Count
    (nWords, nDups)

let showWordCount text =
    let nWords,nDups = wordCount text
    printfn "--> %d words in text" nWords
    printfn "--> %d duplicate words" nDups
~~~ 
 
So recap – if I wanted to use the interactive compiler then I need to put the #r code. In my mind this is the equivalent of me adding the the references to my project. If however I want to use the powerpack in a project – I just need to make sure that the correct references are there. I feel like a noob once again!
