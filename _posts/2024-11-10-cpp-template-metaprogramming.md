---
layout: post
date: 2024-11-10
title: C++ Template Metaprogramming
tags: programming
last_updated: 2024-11-10
status: budding
---

Recently, I heard the term "template metaprogramming" from someone at work. I had no clue about what it was. So I started reading about it. These are the notes for the learning.

## What is Metaprogramming

I admit I had no idea what metaprogramming was either. Let's start there.

According to [Wikipedia](https://en.wikipedia.org/wiki/Metaprogramming),

> Metaprogramming is a computer programming technique in which computer programs have the ability to treat other programs as their data. It means that a program can be designed to read, generate, analyse, or transform other programs, and even modify itself, while running.

Wait what? A program can even modify itself while running? According to [this StackOverflow answer](https://stackoverflow.com/a/42220709), that is the simplest definition of metaprogramming! Moreover, according to the answer,

> Your accepted answer says programs that manipulate themselves. Those are indeed metaprograms but they are a subset of all metaprograms.
>
> All:
> - Parsers
> - Domain specific languages (DSLs)
> - Embedded domain specific languages (EDSLs)
> - Compilers
> - Interpreters
> - Term rewriters
> - Theorem provers
>
> are metaprograms.

[This playlist](https://youtube.com/playlist?list=PLWxziGKTUvQFIsbbFcTZz7jOT4TMGnZBh) explains it in detail. Some notes:

- Programming transforms data, metaprogramming transforms programs to code. In C++, we use _template specializations_ to do this.
- A metaprogram that looks at its own structure is Reflection.
- C++ template metaprogram = compile-time reflection
- Template specialization - partial and full. Read [here](https://en.cppreference.com/w/cpp/language/partial_specialization)
  - Google "class template argument deduction" for details
- To read: `type_traits` [here](https://www.internalpointers.com/post/quick-primer-type-traits-modern-cpp)