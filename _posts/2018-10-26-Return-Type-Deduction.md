---
layout: post
title: C++ Template Return Type Deduction from Integer Parameter 
comments: true

```
#include <iostream>

template<int N>
struct item_return{ typedef int type; };
 
template<int T>
typename item_return<T>::type foo(){ return T; }
 
template<>
struct item_return<1>{ typedef int type; };

template<>
struct item_return<2>{ typedef double type; };
 
template<>
int foo<1>(){ return 42; }

template<>
double foo<2>(){ return 42.1; }
 
int main(){
    std::cout << foo<2>() << std::endl;
}

```

Live Demo:

https://wandbox.org/permlink/bmRsHB8ICdUWd7Mi

