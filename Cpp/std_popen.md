# popen

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [popen](#popen)
  - [与cmd的交互](#与cmd的交互)
  - [代码示例](#代码示例)
  - [popen+cmd-where：文件搜索](#popencmd-where文件搜索)

<!-- /code_chunk_output -->

## 与cmd的交互

可调用cmd，并且获取cmd实时的（每一行）输出结果

## 代码示例

通过调用cmd，执行`gdalinfo.exe --formats`命令，该命令是查看gdalinfo支持的数据格式（前提是要有gdalinfo且环境变量可查到该文件）
```C++
char buffer[4096];
const char* szCmd = "gdalinfo.exe --formats";
FILE* pipe = _popen(szCmd, "r");
if (!pipe) {
    return 1;
}

```

## popen+cmd-where：文件搜索