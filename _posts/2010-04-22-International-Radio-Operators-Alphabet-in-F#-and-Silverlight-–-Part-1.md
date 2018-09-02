---
layout: post
title: International Radio Operators Alphabet in F# and Silverlight – Part 1
tags: 
category: General
---
So I have been delving into F# more and more and thought the best way to learn the language is to write something useful. I have been meaning to get some more Silverlight knowledge (up to now I have mainly been doing WPF) so I came up with a really simple project that I can actually use at work.

Simply put – I often get support calls from clients wanting new activation codes. One of our main app’s was written in VB6 and had its own “security” where it would require about a 45 character sequence for it to be activated. The catch being that each time you reopen the program it would require a different character sequence, which meant that when we activate clients systems we have to do it live! This involves us either referring them to a website, or reading the characters to them over the phone and since nobody in the office knows the IROA off by heart we would come up with some interesting words to represent characters… 9 times out of 10 the client would type in the wrong character and we would have to start all over again… with this app I am hoping to reduce the errors of reading characters over the phone by treating it like a ham radio.

My “Silverlight” application will allow for the user to input a series of characters and the system will then generate the equivalent IROA words… very basic stuff e.g.

Character Input – abc

Words Generated – Alpha Bravo Charlie

After listening to Anders Hejlsberg on Dot Net Rocks Show 541 he mentioned that he felt many applications could make use of F# but in an almost silo basis – meaning that you would write modules that leant themselves to Functional Programming in F# and then incorporate it into a solution where the front end may be in C# or where you would have some other sort of glue.

I buy into this kind of approach, so in this project I will use F# to do my very intensive “Business Logic” and will use Silverlight/C# to do the front end.

F# Business Layer

I am no expert at this, so I am sure to get some feedback on way I could improve my algorithm. My approach was really simple. I would need a function that would convert a single character to a string – i.e. ‘A’ –> “Alpha” and then I would need a function that would take a string of characters, convert them into a sequence of characters, and then apply my converter to return a sequence of words… make sense?

Lets start with the CharToString function

~~~
let CharToString (element:char) =        
    match element.ToString().ToLower() with
    | "1" -> "1"      | "5" -> "5"        | "9" -> "9"
    | "2" -> "2"      | "6" -> "6"        | "0" -> "0"
    | "3" -> "3"      | "7" -> "7"        
    | "4" -> "4"      | "8" -> "8"        
    | "a" -> "Alpha"  | "b" -> "Bravo"    | "c" -> "Charlie"
    | "d" -> "Delta"  | "e" -> "Echo"     | "f" -> "Foxtrot"
    | "g" -> "Golf"   | "h" -> "Hotel"    | "i" -> "India"
    | "j" -> "Juliet" | "k" -> "Kilo"     | "l" -> "Lima"
    | "m" -> "Mike"   | "n" -> "November" | "o" -> "Oscar"
    | "p" -> "Papa"   | "q" -> "Quebec"   | "r" -> "Romeo"
    | "s" -> "Sierra" | "t" -> "Tango"    | "u" -> "Uniform"
    | "v" -> "Victor" | "w" -> "Whiskey"  | "x" -> "XRay"
    | "y" -> "Yankee" | "z" -> "Zulu"     | element -> "Unknown"        
~~~

Quite simple, an element is passed in, this element is them converted to a lowercase single character string and then matched up with the equivalent word. If by some chance a character is not recognized, “Unknown” will be returned…

I know need a function that can take a string and can parse each character of the string and generate a new sequence with the converted words…

~~~
let ConvertCharsToStrings (s:string) =
    s |> Seq.toArray 
      |> Seq.map(fun elem -> CharToString(elem))
~~~

Here… the Seq.toArray converts the string to a sequence of characters. I then searched for some way to parse through every element in the sequence. Originally I tried Seq.iter, but I think my understanding of what iter does was incorrect. Eventually I found Seq.map, which applies a function to every element in a sequence and then creates a new collection with the adjusted processed element. It turned out to be exactly what I needed…

To test that everything worked I created one more function that parsed through every element in a sequence and printed it. AT this point I realized the the Seq.iter would be ideal for this… So my testing code is below…

~~~
let PrintStrings items =
    items |> Seq.iter(fun x -> Console.Write(x.ToString() + " "))

let newSeq = ConvertCharsToStrings("acdefg123")
PrintStrings newSeq
Console.ReadLine()      
~~~
 
Pretty basic stuff I guess… I hope my approach was right?

In Part 2 I will look into doing a simple Silverlight Frontend, referencing the projects together and deploying….