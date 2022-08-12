# Section.1 gitbook安装

1.安装

首先需要安装Node.js

在命令行输入`node -v`和`npm -v`确认安装完成。

命令行输入`npm install gitbook-cli -g`安装gitbook，如果出现问题，尝试使用`cnpm install gitbook-cli -g`来安装gitbook。

安装完成后，在指定目录下输入`gitbook init`初始化gitbook仓库，出现报错，提示为

>../.../..../polyfills.js:287
>
>​if(cb.apply(this, arguments))

打开指定文件polyfills,js后，找到该代码，其包含在函数statFix中，该函数似乎是为了解决旧版本返回uid+gid时候的数据类型的问题，新版本中不会出现该问题，所以注释使用的三行代码掉即可。（参考链接：https://www.jianshu.com/p/6221330b36ba）

> // fs.stat = statFix(fs.stat)
>
> // fs.fstat = statFix(fs.fstat)
>
> // fs.lstat = statFix(fs.lstat)


gitbook init 命令只是用来创建readme.md和SUMMARY.md两个文档，如果代码出错，直接创建连个代码，然后使用gitbook build即可。

1. 使用 `gitbook init` 初始化书籍目录
2. 使用 `gitbook serve` 编译书籍

gitbook fetch 3.2.3  

gitbook fetch 2.6.7

等命令可以下载对应的版本
