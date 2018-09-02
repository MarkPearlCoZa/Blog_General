---
layout: post
title: Sending emails with VB6 and MAPIMessages returns Unspecified Failure has Occurred (Runtime error ‘32002’)
tags: 
category: General
---
So, a morning of bashing my head an a new found appreciation for .Net…

Today I had to do some legacy app programming in vb6…

The issue we were trying to resolve was that we had an application sending emails via the MAPIMessages library. Everything worked fine in Windows XP, but if the user ran the same program in Windows 7 you would get a Runtime error ‘32002’.

After a fair amount of searching on the internet I got several conflicting reasons as to why this was “crashing”. To save those other poor soles that may come across this problem I have pasted a working vb6 solution that works in Windows 7 below…

Public Function TestEmail(ByRef MAPIMessages As MAPIMessages, ByRef MAPISession As MAPISession)
        Let MAPISession.DownLoadMail = False
        '---------------------------------------------------
        'Sign on Session
        '---------------------------------------------------
        If (MAPISession.SessionID = 0) Then
            Call MAPISession.SignOn
        End If

        With MAPIMessages
            .SessionID = MAPISession.SessionID
            .Compose
            .AddressResolveUI = False

            .MsgSubject = "This is a subject."
            .MsgNoteText = "This is a body."

            .RecipIndex = 0
            .RecipType = 1
            .RecipAddress = "smtp: youremail@gmail.com"
            .RecipDisplayName = "smtp: youremail@gmail.com"
        

            .Send False
        End With
End Function
Now there are a few gotchas that you have to be careful about…

You need to set the RecipDisplayName correctly, if you do not, even if the RecipAddress is correct it will return an error.

You also need to turn the AddressResolveUI to false…

Provided you have those two things done… it should work fine…

Good luck!