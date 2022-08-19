# string分割

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [string分割](#string分割)
  - [参数说明](#参数说明)
  - [代码](#代码)
  - [version 2](#version-2)

<!-- /code_chunk_output -->

## 参数说明

输入字符串str，

输出待分割的字符串数组strList，

输入分割符号split。

## 代码

```C++
#include <iostream>
#include <string>
#include <vector>

using std::vector;
using std::string;

void strSplit(string str, vector<string> &strList, string split){
    // strList.clear();
    std::string::size_type pos1, pos2;
    pos2 = str.find(split);
    pos1 = 0;
    while(std::string::npos != pos2){
        strList.push_back(str.substr(pos1,pos2-pos1));
        pos1 = pos2 + split.size();
        pos2 = str.find(split, pos1);
    }
    if (pos1 != str.length())
        strList.push_back(str.substr(pos1));
}
```

## version 2

升级版本，可识别连续的分隔符

```C++
void strSplit_ver2(std::string input, std::vector<std::string>& output, std::string split)
{
    //output.clear();
    std::string::size_type pos1, pos2;
    pos1 = input.find_first_not_of(split);
    pos2 = input.find(split,pos1);

    if (pos1 == std::string::npos) {
        return;
    }
    if (pos2 == std::string::npos) {
        output.push_back(input.substr(pos1));
        return;
    }
    output.push_back(input.substr(pos1, pos2 - pos1));
    strSplit_ver2(input.substr(pos2 + 1), output, split);
    
}
```

函数的输入和输出：

```cmd
cin:
_____PART1______PART2_PART3___
strSplit_ver2:
PART1
PART2
PART3
```
