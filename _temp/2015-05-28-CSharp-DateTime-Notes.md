---
layout: post
title: CSharp DateTime Notes
tags: Language
category: General
---

#### Parsing DateTime from String in a specific format ####

~~~
DateTime theDate = DateTime.ParseExact(dateText, "yyyyMMdd", CultureInfo.InvariantCulture);
~~~
