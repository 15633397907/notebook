# std::vector's error

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [std::vector's error](#stdvectors-error)
  - [length](#length)
  - [bas_alloc](#bas_alloc)

<!-- /code_chunk_output -->

## length

## bas_alloc

直接读取溢出的`vector<string>`会使程序崩溃，

```C++
std::vector<std::string> vec_str(4);
vec_str[0]="q_";vec_str[1]="w_";vec_str[2]="e_";vec_str[3]="r_";
std::string dst = vec_str[3]+"_"+vec_str[4]+"_"+vec_str[5];
std::cout<<dst<<std::endl;
system("pause");
```

```cmd
terminate called after throwing an instance of 'std::bad_alloc'
  what():  std::bad_alloc
```
