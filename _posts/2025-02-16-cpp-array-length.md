---
layout: post
date: 2025-02-16
title: Length of an array in C++
tags: programming
last_updated: 2025-02-16
status: init
type: note
---

I have been away from coding vanilla C++ (without protos, vectors, containers) for so long that I had completely forgotten that one can't get the length of an array in C++ with `arr.length` like in Java. Took me back to my college days when I looked this up today:

```cpp
int length = sizeof(arr) / sizeof(arr[0]);
```

`sizeof(arr)` gives the size of the array in bytes. Java, [I think I'm in love with you!](https://tenor.com/en-GB/view/ted-mosby-love-im-in-gif-19020561){:target="_blank"}

Length of a character array is less verbose:

```cpp
char arr[] = "wow!";
int length = strlen(arr);
```