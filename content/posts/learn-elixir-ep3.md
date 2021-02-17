---
title: "Learn Elixir #3"
summary: "cond, if/unless, do/end"
description: "cond and if/unless statments and do/end blocks"
date: 2021-02-17T20:36:06-03:00
draft: false
categories: Elixir
tags:
- getting-start
- cli
- code
- programming
- learn-elixir
showToc: true
---

## Cond

**Useful to make multi conditions with different values and return the first that match true**

```elixir
cond do
  2 + 2 == 5 ->
    "This will not be true"
  2 * 2 == 3 ->
    "Nor this"
  1 + 1 == 2 ->
    "But this will"
end
```
```elixir
"But this will"
```
**This is equivalent to `else if` clause in many imperative languages (used much less here)**

**Is necessary add a final condition equal `true`, wich always will match, because if all the conditions return `nil` of `false`an error `CondClauseError` is raised**

```elixir
cond do
  2 + 2 == 5 -> 
    "This is never true"
  2 * 2 -> 3
    "Nor this"
  true ->
    "This is always true, equivalent to else"
end
```
```elixir
"This is always true, equivalent to else"
```

**`cond` considers any value besides `nil` or `false` to be `true`**

```elixir
cond do
  hd([1, 2, 3]) -> "1 is considered as true"
end
```
```elixir
"1 is considered true"
```

## If/Unless

**Elixir povider macros `if/2` and `unless/2` wich are useful when you needto checkfor onlyon condition**

_`if`_
```elixir
if true do
  "This works!"
end
```
```elixir
"This works!"
```
_`unless`_
```elixir
unless true do
  "This is will never be seen"
end
```
```elixir
nil
```

**They also suport `else`**
```elixir
if nil do
  "This won't be seen"
else
  "This will"
end
```
```elixir
"This will"
```

## `do/end` blocks

```elixir
iex> if true, do: 1 + 2
2
iex> if false, do: :this, else: :that
:that
```

These are equivalent:

_code/1_
```elixir
if true do
  a = 1 + 2
  a + 10
end
```
_code/2_
```elixir
if true, do: (
  a = 1 + 2
  a + 10
)
```
_out/all_
```
13
```




---

## referencies

Elixir Conditions: [_https://elixir-lang.org/getting-started/case-cond-and-if.html_](https://elixir-lang.org/getting-started/case-cond-and-if.html)

