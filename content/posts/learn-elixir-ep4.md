---
title: "Learn Elixir #4"
summary: "binaries, strings, and charlists"
description: "study texts"
date: 2021-02-18T14:16:24-03:00
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

## Unicode and Code Points

**You can use `?` before a character literal to see your code point**
```elixir
iex> ?a
97
iex> ?ł
322
```
```elixir
iex> "\u0061" === "a"
true
iex>0x0061 = 97 = ?a
97
```

## UTF-8 and Encodings

**Elixir uses UTF-8 to encode its strings, which means that code are encoded as a series of 8-bit bytes**

**`String.lenght/1` count graphemes, but `byte_size/1` reveals the number of underlying raw bytes needed to store the string when using UTF-8. UTF-8 requires one byte to represent the characters `h`, `e`, and `o`, but two bytes to represent `ł`**

```elixir
iex> string = "hełło"
iex> String.length(string)
5
iex> byte_size(string)
7
```
## Charlist

**A charlist is a list of integers where all the integers are valid code points**

```elixir
iex> 'hełło'
[104, 101, 322, 322, 111]
iex> is_list 'hełło'
true
iex> 'hello'
'hello'
iex> List.first('hello')
104
```
```elixir
iex> heartbeats_per_minute = [99, 97, 116]
'cat'
```

```elixir
iex> to_charlist "hełło"
[104, 101, 322, 322, 111]
iex> to_string 'hełło'
"hełło"
iex> to_string :hello
"hello"
iex> to_string 1
"1"
```
```elixir
iex> 'this ' <> 'fails'
** (ArgumentError) expected binary argument in <> operator but got: 'this '
    (elixir) lib/kernel.ex:1821: Kernel.wrap_concatenation/3
    (elixir) lib/kernel.ex:1808: Kernel.extract_concatenations/2
    (elixir) expanding macro: Kernel.<>/2
    iex:1: (file)
iex> 'this ' ++ 'works'
'this works'
iex> "he" ++ "llo"
** (ArgumentError) argument error
    :erlang.++("he", "llo")
iex> "he" <> "llo"
"hello"
```

---

## referencies

Binaries, strings, and charlists: [_https://elixir-lang.org/getting-started/binaries-strings-and-char-lists.html_](https://elixir-lang.org/getting-started/binaries-strings-and-char-lists.html)

