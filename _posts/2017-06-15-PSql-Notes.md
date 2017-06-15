---
layout: post
title: PSql Notes
tags: Postgres
category: Tech
---

### Returning a fixed value list

~~~
select * from  
(Values(1, 'one'), (2, 'two'), (3, 'three')) 
as t(num, letter)
~~~
