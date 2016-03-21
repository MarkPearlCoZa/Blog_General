---
layout: post
title: CSharp DateTime Notes
tags: Language
category: Tech
---

#### Parsing DateTime from String in a specific format ####

~~~
DateTime theDate = DateTime.ParseExact(dateText, "yyyyMMdd", CultureInfo.InvariantCulture);
~~~
