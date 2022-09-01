# qmake语法（pro文件写法）

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [qmake语法（pro文件写法）](#qmake语法pro文件写法)
  - [生成文件图标设置](#生成文件图标设置)
  - [中间文件生成路径](#中间文件生成路径)
  - [QMAKE_CXXFLAGS](#qmake_cxxflags)
  - [stdlib.h no such file or directory](#stdlibh-no-such-file-or-directory)

<!-- /code_chunk_output -->

## 生成文件图标设置

```qmake
RC_FILE += res_widget.rc
RC_ICONS += SARBOX_BLUE_512.ico
```

rc文件内容：

```rc
IDI_ICON   ICON    DISCARDABLE     ".\\icon\\SARBOX_BLUE_512.ico"
```

1. 创建*.rc文件，写明图标所在路径（相对路径即可）
2. qmake中添加如上所示的`RC_FILE`和`RC_ICONS`两行代码，执行qmake
*：有时一次执行qmake后新生成的文件仍然不带图标，需要多次尝试...

## 中间文件生成路径

```qmake
CONFIG(debug, debug|release){
    DESTDIR =       $$PWD/../../bin/debug
    UI_DIR =        ./debug/UI
    MOC_DIR =       ./debug/MOC
    OBJECTS_DIR =   ./debug/OBJ
}else{
    DESTDIR =       $$PWD/../../bin/release
    UI_DIR =        ./release/UI
    MOC_DIR =       ./release/MOC
    OBJECTS_DIR =   ./release/OBJ
}
```

其中，`DESTDIR`为生成文件路径（exe、dll等文件），`UI_DIR`是又*.ui自动生成的ui_*.h文件的路径，`MOC_DIR`是自动生成的存放指针和槽函数的moc_*.h文件的路径，`OBJECTS_DIR`是各个.cpp生成的中间文件*.o的路径

## QMAKE_CXXFLAGS

将所有的警告当成错误处理

```qmake
QMAKE_CXXFLAGS += -Werror = return-type //函数有返回值
QMAKE_CXXFLAGS += -Werror = return-local-addr //返回局部变量地址
QMAKE_CXXFLAGS += -Werror = missing-field-initializers //缺少初始值设定项
QMAKE_CXXFLAGS += -Werror = maybe-uninitialized //变量可能没有被初始化
QMAKE_CXXFLAGS += -Werror = delete-non-virtual-dtor //
QMAKE_CXXFLAGS += -Werror = unused-but-set-variable //设置了但未使用的变量
QMAKE_CXXFLAGS += -Werror = parentheses //括号不匹配
QMAKE_CXXFLAGS += -Werror = pointer-arith //指针用在了算术运算
QMAKE_CXXFLAGS += -Werror = reorder //警告构造函数的顺序不会被使用
QMAKE_CXXFLAGS += -Werror = format-extra-args //格式不对
QMAKE_CXXFLAGS += -Werror = format= //格式不对
QMAKE_CXXFLAGS += -Werror = unused-variable //未使用的变量
```

忽略该警告

```qmake
QMAKE_CXXFLAGS += -Wno-unused-function //未使用的函数
QMAKE_CXXFLAGS += -Wno-unused-parameter //设置了但未使用的参数
QMAKE_CXXFLAGS += -Wno-comment //注释使用不规范。
QMAKE_CXXFLAGS += -Wno-sequence-point //如出现i=i++这类代码，则报警告
```

## stdlib.h no such file or directory

linux编程时，
`#include <QDialog>`后，通过多级include ，最后到达`#include <cstdlib.h`>中，

在cstdlib.h中，`#include_next <stdlib.h>`报错，提示：`no such file or directory`

[原因及解决方法(form csdn)](https://blog.csdn.net/xuleisdjn/article/details/108345311)

原因：
这是由于gcc7已经吧stdlib.h纳入了libstdc++以进行更好的优化，C Library的头文件stdlib.h使用 Include_next，而include_next对gcc系统头文件路径很敏感

解决方法：

在.pro文件中，添加

```qmake
DEFINES += ENABLE_PRECOMPILED_HEADERS=OFF
QMAKE_CFLAGS_ISYSTEM = -I
greaterThan(QT_MAJOR_VERSION, 4): {
QT += widgets
QMAKE_CFLAGS_ISYSTEM=-I
}
```
