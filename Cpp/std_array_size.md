# 计算数组长度

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [计算数组长度](#计算数组长度)
  - [动态数组](#动态数组)
  - [静态数组](#静态数组)
  - [检测数组为动态或静态的方法](#检测数组为动态或静态的方法)

<!-- /code_chunk_output -->

## 动态数组

```C++
size_t x = 20;
double * arr = new double [x];
std::cout<<_msize(arr)/sizeof(*arr)<<std::endl;
// cmd: 20
```

## 静态数组

```C++
double arr[15];
std::cout<<sizeof(arr)/sizeof(*arr)<<std::endl;
// cmd: 15
```

## 检测数组为动态或静态的方法

如果使用计算动态数组长度的方式计算静态数组会导致异常报错（_msize问题），而用计算静态数组长度的方式计算动态数组则会返回0（sizeof(arr_a) < sizeof(*arr_a), 返回整数0）.

...
