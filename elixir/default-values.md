Elixir allows for default values in function definitions:

```
defmodule Test do
  def sum(a \\ 3, b, c \\ 7) do
    a + b + c
  end
end
```

Which would work as follows:

```
iex>Test.sum(11, 22, 33)
66
iex>Test.sum(11, 22)
40
```

So far, so good. What's interesting is that when providing only one paramter
to `sum`, Elixir will pattern match that param as `b`, or the parameter
without a default value:

```
Test.sum(11)
21
```

It works because using a default value is actually creating an additional method definition:

```
def sum(a, b), do: sum(a, b, 7)
def sum(b),    do: sum(3, b, 7)
```

Reference:
http://chimera.labs.oreilly.com/books/1234000001642/ch02.html#CH02-ET02
