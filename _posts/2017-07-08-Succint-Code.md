---
layout: post
title: Succint Code
tags: 
category: General
---

Often the beauty of code is in it being succint without loosing it's meaning. 

Compare the following two equivalent poems... see which one holds more beauty to you?

### Poem 1

~~~
What life is like in Harlem  

What happens to a dream that has been deferred for a time?  
Does it dry up  
Like the way a raisin does when it's in the sun for a while?  
Or does it fester like the way an ugly sore would -   
And then after that does it run and run?  
Does it stink like rotten meat would smell to you?  
Or does it sort of crust and sugar over - you know -  
Like the way a syrupy sweet would?  
Maybe though it just sags in a downward motion  
Like the way a heavy load would sag.  
Or does it on the other hand explode like a bomb would?
~~~

### Poem 2

~~~
Harlem

What happens to a dream deferred?

      Does it dry up
      like a raisin in the sun?
      Or fester like a sore—
      And then run?
      Does it stink like rotten meat?
      Or crust and sugar over—
      like a syrupy sweet?

      Maybe it just sags
      like a heavy load.

      Or does it explode?
~~~

Removing fifty nine unnecessary words reduces the text from 113 to 54 words and uncovers a great poem. Now, if we look at code - I have two implementations solving the same problem

### Code 1

~~~
defmodule Howmanydig do

  def is_not_false(n), do: n !== false
  def is_two_digits_or_more(n), do: length(n |> Integer.digits) >=2
  def is_two_numbers_within_delta(a,b, delta), do: abs(a - b) <= delta
  def get_digits(n), do: n |> Integer.digits
  
  def is_unique_digits(n) do
  	digits = n |> get_digits
  	digits |> Enum.uniq |> length === (digits |> length)
  end
  
  def is_digits_matching_compare(n, compare, initial) do
  	n |> get_digits
    	|> Enum.reduce_while(initial, fn(cur, prev) -> 
      			if (compare.(cur,prev)) do 
            	{:cont, cur}
           	else 
            	{:halt, false}
            end
      	 end)
      |> is_not_false
  end
  
  def is_digits_increasing(n), do: is_digits_matching_compare(n, &(&1 > &2), -1) 
  
  def is_within_delta(n, d) do 
  	initial = n |> get_digits |> List.first 
    compare = fn(a,b) -> is_two_numbers_within_delta(a, b, d) end
  	is_digits_matching_compare(n, compare, initial)
  end
  
  def sel_number(n, d) do
  	 0..n
      |> Enum.to_list
      |> Enum.filter(&is_two_digits_or_more(&1))
      |> Enum.filter(&is_digits_increasing(&1))
      |> Enum.filter(&is_unique_digits(&1))
      |> Enum.filter(&is_within_delta(&1, d))
      |> length
  end
end
~~~

### Code 2

~~~
defmodule Howmanydig do
  def sel_number(n, d) do
    1..n
    |> Stream.map(&Integer.digits/1)
    |> Stream.filter(&(length(&1) >= 2))
    |> Stream.filter(&unique_increasing/1)
    |> Stream.filter(&diff_neigh_pairs_not_exceeds(&1, d))
    |> Enum.count
  end
  
  def unique_increasing(l), do: Enum.sort(Enum.uniq(l)) == l
  
  def diff_neigh_pairs_not_exceeds(l, n) do
     max = 
      Enum.zip(l, tl(l))
      |> Enum.map(fn {prev, next} -> next - prev end)
      |> Enum.max
    
    max <= n
  end
end
~~~

The second code example to me is more beautiful than the first. It has managed to not become ambigous, while still solving the same problem. It's succintness is its beauty.

#### Reference

[Keys to Great Writing Ch1 ]()
