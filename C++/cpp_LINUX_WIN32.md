# Section.1 LINUX & WIN32


<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [Section.1 LINUX & WIN32](#section1-linux--win32)
  - [头文件替换](#头文件替换)
  - [sprintf_s -> snprintf](#sprintf_s---snprintf)
  - [fopen_s -> fopen](#fopen_s---fopen)
  - [memset](#memset)
  - [_strlwr 平替（无函数）](#_strlwr-平替无函数)
  - [_splitpath_s 平替（无函数）](#_splitpath_s-平替无函数)
  - [_fseeki64 ->  fseeko64](#_fseeki64----fseeko64)
  - [CPU数量](#cpu数量)

<!-- /code_chunk_output -->


## 头文件替换

| library | windows              | linux                  |
| ------- | -------------------- | ---------------------- |
| io      | \#include <io.h>     | ?                      |
| dirent  | \#include <dirent.h> | \#include <sys/stat.h> |

## sprintf_s -> snprintf

```c++
char tag[256];
char* str;
#ifdef windows
        sprintf_s(tag,"<%s>",str);
#elif defined __linux__
        snprintf(tag,256,"<%s>",str);
#endif
```

## fopen_s -> fopen

```C++
const char* charPath
FILE *pFile
#ifdef windows
fopen_s(&pFile,charPath,"rb");
#elif defined __linux__
pFile = fopen(charPath,"rb");
#endif
```

## memset

linux下需要添加string.h （不是\<string\>）

## _strlwr 平替（无函数）

```C++
char str[256];
 #ifdef windows
_strlwe(str);
#elif defined __linux__
for(char* ptr = str; *ptr; ptr++){
*ptr = tolower(*ptr);
}
#endif
```

## _splitpath_s 平替（无函数）

```C++
1.SARImgIO.h中，只去后缀szExt的情况：
#include <stdio.h>
#include <string.h>
 
#ifdef windows
_splitpath_s(szFileName, szDri, szDir, szName, szExt);
#elif defined __linux__
std::string strFileName = szFileName;
std::string::size_type pos = strFileName.find_last_of(".");
strcpy(szExt, strFileName.substr(pos, strFileName.size()-1).c_str());
#endif
2......（未完成）
```

## _fseeki64 ->  fseeko64

西电 孙浩南好像说这里函数计算结果不相同？

```C++
#ifdef windows
_fseeki64(file, (nSizeBOff+(nLWidth+i*imgWidth)*nSizeT), SEEK_SET);
#elif defined __linux__
_fseeko64(file, (nSizeBOff+(nLWidth+i*imgWidth)*nSizeT), SEEK_SET);
#endif
```

## CPU数量

openmp需要使用

```C++
int intnCPUs;
#ifdef windows
#include<windows.h>
SYSTEM_INFO SystemInfo;
GetSystemInfo(&SystemInfo);
intnCPUs = SystemInfo.dwNumberOfProcessors;
#elif defined __linux__
#include <unistd.h>
#include <iostream>
intnCPUs = sysconf(_SC_NPROCESSORS_CONF);
#endif
intnCPUs *= 0.9;
```



