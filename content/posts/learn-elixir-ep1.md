---
title: "Learn Elixir"
summary: "Hello Word"
description: "Running scripts and study Basic types"
date: 2021-02-02T19:03:14-03:00
draft: true
categories: Elixir
tags:
- getting-start
- cli
- code
- programming
- learn-elixir
draft: false
showToc: true
---

## [Introduction](https://elixir-lang.org/getting-started/introduction.html)

_Interative mode_: **iex**

_Initial Commands_:
```elixir
iex> 40 + 2
42
iex> "hello" <> " world"
"hello world"
```

_Running Scripts_: `elixir hello-word.exs`

_Hello Word:_
```elixir
IO.puts "Hello Word"
```
```elixir
"Hello Word"
```

## [Basic types](https://elixir-lang.org/getting-started/basic-types.html)

### _Get Data Type_: `i data`
```elixir
iex> i 1
```
will show something like this:
```
Term
  1
Data type
  Integer
Reference modules
  Integer
Implemented protocols
  IEx.Info, Inspect, List.Chars, String.Chars
```

### _Basic Types_
```elixir
iex> 1          # integer
iex> 0x1F       # integer
iex> 1.0        # float
iex> true       # boolean
iex> :atom      # atom / symbol
iex> "elixir"   # string
iex> [1, 2, 3]  # list
iex> {1, 2, 3}  # tuple
```

### _Math_
```elixir
iex> 1 + 2
3
iex> 5 * 5
25
iex> 10 / 2
5.0
```
`10/2` always return a float number, to get an integer, use `div` and `rem` functions:
```elixir
iex> div(10, 2)
5
iex> div 10, 2
5
iex> rem 10, 3
1
```

### _Shortcut Notations_
```elixir
iex> 0b1010 # binary
10
iex> 0o777 # octal
511
iex> 0x1F # hexadecimal
31
```

### _Scientific Notation_
```elixir
iex> 1.0
1.0
iex> 1.0e-10
1.0e-10
```

### _Round Function_
```elixir
iex> round(3.58)
4
iex> trunc(3.58)
3
```
