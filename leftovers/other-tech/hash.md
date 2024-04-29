---
description: What is Hashing
---

# 🏦 Hash

#### links

[https://www.freecodecamp.org/news/what-is-hashing/](https://www.freecodecamp.org/news/what-is-hashing/)\
[https://www.youtube.com/watch?v=2BldESGZKB8](https://www.youtube.com/watch?v=2BldESGZKB8)\
[https://www.youtube.com/watch?v=jmtzX-NPFDc](https://www.youtube.com/watch?v=jmtzX-NPFDc)

### **What is hashing?** <a href="#what-is-hashing" id="what-is-hashing"></a>

Hashing means using some algorithm to map object data to some representative value.

Hash tables have to support 3 functions.

* insert (key, value)
* get (key)
* delete (key)

### Hash Function

<figure><img src="../../.gitbook/assets/изображение (12).png" alt=""><figcaption></figcaption></figure>

example

if we want to store and check user passwords

1. save hash to DB\
   plaintext pass + hash function = password hash
2. check pass on login\
   compare new generated password hash and already stored password hash

### Salting

To avoid same hash for same data inputs we can add random keyword to input to make it unique&#x20;

### Peppering

We can add same keyword to input value to make in changed

## Algoritms

<figure><img src="../../.gitbook/assets/изображение (15).png" alt=""><figcaption></figcaption></figure>

## SHA-1

It is a string of 40 hexadecimal characters (0-9 and a-f) and is computed from the contents of a file or directory structure. The SHA-1 hash looks something like this: `24b9da6552252987aa493b52f8696cd6d3b00373`

<figure><img src="../../.gitbook/assets/изображение (14).png" alt=""><figcaption></figcaption></figure>
