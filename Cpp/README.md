# C++ 库 & 代码说明 & 自写函数

## Std

### [filesystem](./std_filesystem.md)

C++17版本下的文件系统，支持文件的遍历搜索、路径判断等功能

### [fstream](./std_fstream.md)

ifstream & ofstream, std的文件读写, 包括文本文件和二进制文件

### [regex正则表达式规则](./std_regex.md)

正则表达式的语法

### [特殊数据的正则表达式](./std_regex_plus.md)

$2^n$值的筛选方法

## Eigen

矩阵运算库

### [Eigen的矩阵插值](./eigen_interp.md)

### [Eigen与Matlab操作对比](./eigen_compare_with_matlab.md)

### [Eigen线性方程解](./eigen_linear_algebra.md)

包括 SVD QR & 传统方程

## GDAL

图像读取常用的库。

### [设置坐标系统](./gdal_setProjection.md)

4326坐标系统的添加。以及其他坐标系统的搜索网站。

### [数据格式](./gdal_GDALDataset.md)

MEM, 可以保存到内存中的数据格式。

### [GDAL影像读写的进度值](./gdal_Progress.md)

gdal的进度条的回调函数使用方法。

## [TinyXML](./tinyxml_.md)

简单的三方库, 文件中记录的是version 1的代码, 但与2区别不大。

## Function

### [二进制数据读写(float)](./cpp_binary_float_IO.md)

说明：

### [翻转的线](./cpp_filpedLine.md)

可以在循环中使用, 实现类似于等待的效果, 机制还不完善。

### [cmd显示for循环进度](./cpp_for_processBar.md)

输出for循环的进度值，\r不占用太多行数

### [linux <-> windows平替函数](./cpp_LINUX_WIN32.md)

linux 与 windows 部分不支持双平台代码的平替选择。

### [Mat IO](./cpp_mat_IO.md)

读取matlab的 mat矩阵到C++

### [stringSplit字符串切割](./cpp_stringSplit.md)

支持长度大于1的切割符，以弥补std::string无split的问题，

## 编程知识

### [设计模式-单例模式](./programing_Singleton_Pattern.md)

一种创建型的设计模式，该模式的主要目的就是确保某个类有且仅有一个实例存在。

### [原子操作](./programing_atomic_operation.md)

并行处理中，最小的操作单位。
