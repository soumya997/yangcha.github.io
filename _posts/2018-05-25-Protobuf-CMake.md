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

```dos
+---bin
+---cmake
+---include
|   \---google
|       \---protobuf
|           +---compiler
|           |   +---cpp
|           |   +---csharp
|           |   +---java
|           |   +---javanano
|           |   +---js
|           |   +---objectivec
|           |   +---php
|           |   +---python
|           |   \---ruby
|           +---io
|           +---stubs
|           \---util
\---lib
    \---pkgconfig 
```

# CMake

[CMake](https://cmake.org) is an excellent tool for building, testing and packaging.

```cmake
find_package(Protobuf REQUIRED)
include_directories(${Protobuf_INCLUDE_DIRS})
include_directories(${CMAKE_CURRENT_BINARY_DIR})
protobuf_generate_cpp(PROTO_SRCS PROTO_HDRS foo.proto)
protobuf_generate_cpp(PROTO_SRCS PROTO_HDRS EXPORT_MACRO DLL_EXPORT foo.proto)
protobuf_generate_cpp(PROTO_SRCS PROTO_HDRS DESCRIPTORS PROTO_DESCS foo.proto)
protobuf_generate_python(PROTO_PY foo.proto)
add_executable(bar bar.cc ${PROTO_SRCS} ${PROTO_HDRS})
target_link_libraries(bar ${Protobuf_LIBRARIES})
```
