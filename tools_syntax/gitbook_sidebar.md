# Gitbook侧边栏导航问题

使用新下载的nodejs和npm安装gitbook
`npm gitbook-cli -g`
会自动安装npm中最新版的gitbook（可能是3.2.3），该版本使用`gitbook build`生成的电子书侧边栏存在一些问题，以下是对应每个问题的解决方法。

1.侧边栏链接无法跳转

查找资料后，解决方法有两种，一是修改 _book/gitbook/theme.js文件，二是使用低版本gitbook。


a. 修改theme.js文件

打开theme.js文件，搜索`if(m)for(n.handler&&`，将`if(m)`修改为`if(false)`，即可。

这种方法的缺点是每次`gitbook build`后都需要修改该文件。

b.降低gitbook版本

网上很多博客都提到使用2.6.7版本的gitbook，但在下载和使用时总是会出现异常报错并且解决方法不容易搜索到。仅有一篇博客提到使用3.0.0版本，经过测试发现确实可行，`gitbook fetch 3.0.0`下载该版本gitbook，没有异常报错情况出现，且`gitbook build --gitbook=3.0.0`指令可以正常完成。并且侧边栏可以正常跳转。

2.侧边栏父节点链接跳转异常

通过上述两种方法可以解决侧边栏不同页面之间无法跳转的问题，但使用时发现父节点信息（如chpter01/README.md等）仍有异常情况。

根据gitbook规则，在SUMMARY.md文档中，需要为每个父节点添加README.md文档，用于介绍父节点信息，但是在`gitbook build`后，打开网页点击父节点发现该链接为无法连接到README.md文档（如：./chapter01/这种情况）

<center>缺图</center>

经过实验，这种情况的解决方法是把**README.md文档改名**，具体的更改要求暂不清楚，但可能只要不只是README.md即可。（可以参考点击本文档父节点后跳转的链接）
