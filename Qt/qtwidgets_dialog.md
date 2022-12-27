# QDialog

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

## exec()

qdialog与widget的一个区分是“dialog默认为模态（isModal）窗口”，设置模态窗口的对话框，使用exec()启动程序,会阻塞线程，从而达到**处理完弹窗事件后才可继续运行其他窗口**的效果。

`exec()`函数需要重写（override）, 其中一种写法是：

```c++
// .h
#include <qeventloop.h>
#include <qevent.h>

private:
QEventLoop* m_loop;
int m_result;

public slots:
int exec();
void closeEvent(QCloseEvent* event);

// .cpp
int my_dialog::exec()
{
    show();
    m_loop = new QEventLoop(this);
    m_loop->exec(); //利用事件循环实现模态
    return m_result;
}
void my_dialog::closeEvent(QCloseEvent* event)
{
    m_loop->quit();
    event->accept();
}
```

在`exec()`中显示窗口(`show()`)，再使用`QEventLoop`阻塞线程，等待程序退出时执行`QEventLoop::quit()`后结束循环事件，返回`m_result`，结束函数。
