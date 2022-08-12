# Gitbook添加插件

通过添加插件可以使gitbook生成的电子书元素更加丰富。

在电子书根目录下创建book.json文件，

添加电子书的基础信息，

```JSON
{
    "title" : "我的学习笔记",
    "author" : "litan",
    "description" : "日常工作中用到的一些技术总结",
    "language" : "zh-hans",
}
```

添加插件信息，

```JSON
{
    "title" : "我的学习笔记",
    "author" : "litan",
    "description" : "日常工作中用到的一些技术总结",
    "language" : "zh-hans",
    "plugins" :[
        "katex",
        "expandable-chapters-small"
    ]
}
```

保存book.json文件后，命令行运行gitbook install，通过npm安装gitbook插件。

>上段代码中\
katex插件可以使html正常显示TeX格式代码；\
expandable-chapters-small插件是使侧边栏伸缩的插件。

>显示数学公式的插件已知有两个，分别是`mathjax`和`katex`， [公式插件详情参考网页](https://chrisniael.gitbooks.io/gitbook-documentation/content/format/math.html)。分别下载两种插件后发现，mathjax在下载时会报错（并没有详细查看报错原因和查找解决方案），而katex插件则可以正常下载和使用，所以比较推荐优先下载katex。

  "back-to-top-button",   返回顶部  （报错提示，仅支持gitbook > 3.1.1以上的版本使用，故无法与gitbook build --gitbook=3.0.0共同使用）
  "lightbox 弹窗形式显示图片
