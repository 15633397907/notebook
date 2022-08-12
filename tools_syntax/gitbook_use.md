# Gitbook 命令

gitbook init 命令只是用来创建readme.md和SUMMARY.md两个文档，如果代码出错，直接创建连个代码，然后使用gitbook build即可。

1. 使用 `gitbook init` 初始化书籍目录
2. 使用 `gitbook serve` 编译书籍

在文件修改过程中，每一次保存文件，`gitbook serve` 都会自动重新编译，所以可以持续通过浏览器来查看最新的书籍效果！

编译markdown文档，可以使用Typora_0.9（测试版本不收费，1.0后需要收费使用），或在VSCode中安装markdown组件。

在SUMMARY.md中添加相关章节后，执行`gitbook init`，会自动创建`SUMMARY.md`中的目录结构。

连续两个`{` `{`会导致build失败。

解决方法是在两个`{`之间添加一个空格，即`{ {`，即可解决问题。

安装calibre，并确定安装目录（如：C:\Program Files (x86)\Calibre2）已经被添加到环境变量中后（首次添加可能需要重启），输入以下命令可以生成相应格式的文件。

```shell
gitbook pdf     //生成pdf
gitbook epub    //生成epub ?
gitbook mobi    //生成mobi ?
```


