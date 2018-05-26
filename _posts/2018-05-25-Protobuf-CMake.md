---
layout: post
title: CMake and Protocol Buffers on Windows 
comments: true
---

# Protocol Buffers

[Protocol buffers](https://developers.google.com/protocol-buffers/) are Google's language-neutral, platform-neutral approach for serializing structured data. 

On linux, you can easily install it using package management. On Windows, you may build it from source and install it. [Here](
https://github.com/google/protobuf/blob/master/cmake/README.md) is the instructions to install it on Windows.

Suppose it is installed under the install location, such as `d:\pgk\protobuf`, the directory structure is as follows:

>+---bin
>+---cmake
>+---include
>|   \---google
>|       \---protobuf
>|           +---compiler
>|           |   +---cpp
>|           |   +---csharp
>|           |   +---java
>|           |   +---javanano
>|           |   +---js
>|           |   +---objectivec
>|           |   +---php
>|           |   +---python
>|           |   \---ruby
>|           +---io
>|           +---stubs
>|           \---util
>\---lib
>    \---pkgconfig 


# CMake


