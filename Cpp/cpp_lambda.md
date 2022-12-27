# lambda表达式

## 折叠表达式和泛型lambda

```c++
//before
if(x=='x'||x=='X'||x=='e'||x=='E'||x=='.'){
    work();
}

//after
static auto anyone = [](auto&& k, auto&&... args) ->bool { return ((args == k) || ...); };
if(anyone(x,'x','X','e','E','.')){
    work();
}
```

>作者：码农出击
链接：https://www.zhihu.com/question/561629881/answer/2810564299
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。