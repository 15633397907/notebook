# chrono c++的计时功能

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [chrono c++的计时功能](#chrono-c的计时功能)
  - [代码](#代码)

<!-- /code_chunk_output -->

## 代码

```c++
auto start = std::chrono::system_clock::now();
/// 一个费时的函数
func();
auto end = std::chrono::system_clock::now();
auto duration = std::chrono::duration_cast<std::chrono::microseconds>(end - start);
cout <<  "Spent" << double(duration.count()) * std::chrono::microseconds::period::num / std::chrono::microseconds::period::den << " seconds." << endl;
```

此方法可以精确到微妙，如花费了0.123456秒

num 和 den分别表示分子(numerator)和分母(denominator),在上面的代码中，num=1， den=1,000,000

count( ) 用来返回时间

C++11的 #include< chrono >和传统的 #include < ctime >相比，代码量较多，但是精度也更高
