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

#### Working with lists

Cons operator is |, it is used to split a list into head and tail (remaining elements)

~~~
languages = ["Elixir", "JavaScript", "Ruby", "C#"]
[first, second, third, fourth] = languages

[head | tail] = languages
[head | _ ] = languages
~~~

#### Recursion

Below is an example of a recursive call on a collection...

~~~
defModule Language do
    def print_list(head | tail) do
        IO.puts head
        print_list(tail)
    end

    def print_list([]) do
    end
end
~~~

#### Optional Parameters

~~~
defModule Examples do
    def balance(transactions, options \\ [])
        ...
    end
end
~~~

~~~
defmodule Printer do
  def greet(name, options \\ []) do
    greeting = options[:prefix] || "Hello"
    ...
  end
end
~~~

#### Print to screen

~~~
IO.puts "Hello world"
~~~

#### Map to tuple

~~~
@number_map Enum.into(Enum.zip( (0..20), ~w(zero one two three four five six seven eight nine ten eleven twelve thirteen fourteen fifteen sixteen seventeen eighteen nineteen twenty)), %{} )
~~~

#### Get a element of a tuple

~~~
{:ok, "hello"} |> elem(1)   # returns hello
~~~

#### Map Examples

~~~
person = %{ "name" => "Brooke", "age" => 42 } # Creates a map

Map.fetch(person, "name") # returns the tuple
Map.fetch!(person, "name") # returns the value, not the tuple
~~~

#### For Loops

~~~
for count <- 1..(length(a) - 1) do
  with {head, tail} <- Enum.split(a, count) do
    [Enum.join(head, " "), Enum.join(tail, " ")]
  end
end
~~~

~~~
 String.graphemes(s)
|> Enum.with_index(1)
~~~

#### Public vs Private Functions

~~~
defp some_function do  # a private function
...
end

def some_other_function do # a public function
...
end
~~~

#### Naming Conventions

* [Read naming conventions](https://github.com/elixir-lang/elixir/blob/master/lib/elixir/pages/Naming%20Conventions.md)  

### Managing State

#### Agents

~~~
defmodule ExampleState do
    @name __MODULE__
    def start_link() do
        Agent.start_link(fn-> 1 end, @name)
    end

    def get_state() do
        Agent.get(@name, fn(x)-> x end)
    end

    def some_def() do
        case start_link do
          {:ok, _}       -> some_def
          {:error, _}    -> get_state
        end
    end
end
~~~

Sometimes you want to have multiple state in a module, you can do this by...

~~~
defmodule ExampleState do
    def start_link() do
        Agent.start_link(fn-> 1 end, name:StateStore)
    end

    def get_state() do
        Agent.get(StateStore, fn(x)-> x end)
    end

    def some_def() do
        case start_link do
          {:ok, _}       -> some_def
          {:error, _}    -> get_state
        end
    end
end
~~~

#### Case vs Cond

Use case to check multiple patterns
Use cond to check multiple conditions

#### Skipping Tests

~~~
defmodule Api.Router.Test do
  use ExUnit.Case, async: true
  use Plug.Test

  @tag :skip
  test "authenticates requests" do
    conn = conn(:get, "/api/pomodoro/fgsd73n")
             |> put_req_header("cookie", "not a valid cookie")
             |> Api.Router.call([])

    assert conn.status == 401
  end
end
~~~
