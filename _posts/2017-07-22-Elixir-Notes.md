---
layout: post
title: Elixir Notes
tags: 
category: Tech
---

#### Pure Functions

* return value should rely entirely on parameters  
* no side effects  

#### Define a module

~~~
defmodule ModuleName do
    ...
end
~~~

#### Define a function

~~~
def FunctionName(parameter1, paremeter2) do
    ...
end
~~~

#### Piping

~~~
SomeModule.some_function("Some string")

"Some string" |> SomeModule.some_function
~~~

#### Pattern Matching

The = symbol in Elixir is called the match operator.
The <> symbol in Elixir is a string concatenation operator.

~~~
"Jose " <> last_name = "Jose Valim"
~~~

The above snippet matches last_name with "Valim"

#### Tenary

Elixir doesn't have a tenary operator, but we can use something sorta similar

~~~
condition && trueValue || falseValue
~~~

#### Atoms

Anything that starts with : is an atom

~~~
SomeModule.some_function(:some_atom)
~~~

#### String Interpolation

~~~
name = "Mark"
"Hello #{name}, how are you"
~~~

#### Anonymous Functions

Functions can:  
* be assigned to variables  
* be passed around as variables  

Anonymous functions have:  
* No name  
* No module  
* created using arrow syntax fn ->  

~~~
max_balance = fn(amount) -> "Max: #{amount}" end
~~~

Invoking anon functions use .() syntax

~~~
max_balance.(500)
~~~

Anon functions can be split into multiple clauses using pattern matching

~~~
account_transaction = fn
    (balance, amount, :deposit) -> balance + amount
    (balance, amount, :withdrawl) -> balance - amount
end
~~~

There is a shorthand for anon functions using the & symbol

~~~
deposit = fn(balance, amount) -> balance + amount end
deposit = &(&1 + &2)
~~~

#### Print to screen

~~~
IO.puts "Hello world"
~~~

#### Map to tuple

~~~
@number_map Enum.into( Enum.zip( (0..20), ~w(zero one two three four five six seven eight nine ten eleven twelve thirteen fourteen fifteen sixteen seventeen eighteen nineteen twenty)), %{} )
~~~
