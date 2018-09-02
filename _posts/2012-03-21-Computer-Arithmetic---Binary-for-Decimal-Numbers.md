---
layout: post
title: Computer Arithmetic - Binary for Decimal Numbers
tags: 
category: General
---
This may be of use to someone else doing this course…

The Problem

In the section on Computer Arithmetic it gives an example of converting -7.6875 to IEEE floating point format. I understand all the steps except for the first one, where it does the following...

7.6875 (base 10) = 111.1011 (base 2)

I don't understand the conversion - I realize that 111 (base 2) = 7 (base 10), but how does the .6875 part relate to the .1011? Or am I totally off track with this?

The Solution

The fractional part of the decimal to binary conversion is done as follows:

0.6875 x 2 = 1.375 = 0.375 + 1 (Keep the 1 separate)

0.375 x 2   = 0.75   = 0.75    + 0

0.75 x 2    = 1.5      = 0.5      + 1

0.5 x 2     = 1.0       = 0.0       + 1

The bit pattern of 0s and 1s on the right-hand side gives you the fractional part.

So 0.6875 (base 10) = .1011 (Base 2)

See also Stallings, chapter 19.