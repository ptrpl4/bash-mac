---
description: What is Hashing
---

# 🏦 Hash

#### links

https://www.freecodecamp.org/news/what-is-hashing
https://www.youtube.com/watch?v=2BldESGZKB8
https://www.youtube.com/watch?v=jmtzX-NPFDc

## Hashing

Hashing means using some algorithm to map object data to some representative fixed-size values

### Hash tables

Fast and convenient data structures that use hashing

Hash tables have to support 3 functions:
* insert (key, value)
* get (key)
* delete (key)

## Hash Function

![](../../aaa-assets/изображение%20(12).png)

example

if we want to store and check user passwords
1. save hash to DB\
   plaintext pass + hash function = password hash
2. check pass on login\
   compare new generated password hash and already stored password hash

### Salting

To avoid same hash for same data inputs we can add random keyword to input to make it unique

### Peppering

We can add same keyword to input value to make in changed

## Algoritms

![](../../aaa-assets/изображение%20(15).png)

## SHA-1

It is a string of 40 hexadecimal characters (0-9 and a-f) and is computed from the contents of a file or directory structure. The SHA-1 hash looks something like this: `24b9da6552252987aa493b52f8696cd6d3b00373`

![](../../aaa-assets/изображение%20(14).png)
