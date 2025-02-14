---
title: "Learn Elixir #2"
summary: "case"
description: "Case Condition and Anonymous Functions guards"
date: 2021-02-16T19:23:38-03:00
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


## Case

```elixir
case {1, 2, 3} do       
  {1, _x, 3} ->  
    "This clause will match and bind _x to 2 in this clause"
   
  {4, 5, 6} ->
    "This clause won't match"

   _ ->
    "This clause would match any value"
end
```
```elixir
"This clause will match and bind _x to 2 in this clause"
```

**To use pattern match you need to use pin`^` operator**

```elixir
x = 1

case 10 do
  ^x -> "Won't match"
  _ -> "Will match"
end
```
```elixir
"Will match"
```

**Clause allow extra coditions to be specified via guards**

```elixir
case {1, 2, 3} do
  {1, x, 3} when x > 0 ->
    "Will match"
  _ ->
    "Would match, if guard condition were not satisfied"
end
```
```elixir
"Will match"
```

**Erros in guards will not leak but simply make the guard fail**

```elixir
iex> hd(1)
** (ArgumentError) argument error
  :erlang.hd(1)
```

```elixir
case 1 do
  x when hd(x) -> "Won't match"
  x -> "Got #{x}"
end
```
```elixir
"Got 1"
```
**Anonymous Functions can also have multiple clauses and guards**

```elixir
f = fn
  x, y when x > 0 -> x + y
  x, y -> x * y
end
```
```elixir
iex> f.(1, 3)
4
iex> f.(-1, 3)
-3
```

---

## referencies

Elixir Conditions: [_https://elixir-lang.org/getting-started/case-cond-and-if.html_](https://elixir-lang.org/getting-started/case-cond-and-if.html)

