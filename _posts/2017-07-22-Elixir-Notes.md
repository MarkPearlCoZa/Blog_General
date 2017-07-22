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

#### Atoms

Anything that starts with : is an atom

~~~
SomeModule.some_function(:some_atom)
~~~
