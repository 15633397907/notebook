# Section.3 string分割

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
