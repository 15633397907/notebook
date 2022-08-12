# widget控件的常用事件

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [widget控件的常用事件](#widget控件的常用事件)
  - [paintEvent绘图事件](#paintevent绘图事件)
  - [dragEnterEvent & dropEvent 拖拽事件](#dragenterevent--dropevent-拖拽事件)

<!-- /code_chunk_output -->

## paintEvent绘图事件

paintEvent(QPaintEvent *event) 主要用于图形的绘制，当设置布局（layout）后，改变窗口尺寸会触发update/repaint？事件，重新对QWidget进行绘制

使用方法：

以**渐变色条**为例，

创建一个“plus”版的widget控件，重载paintEvent事件，不关注`mousePressEvent`

```C++
//// .h
class widget_plus1 : public QWidget
{
    Q_OBJECT
public:
    explicit widget_plus1(QWidget *parent = nullptr);
    ~widget_plus1();

    int widget_plus1_num;

protected:
    void paintEvent(QPaintEvent* event);
    void mousePressEvent(QMouseEvent* event);

signals:
    void mousePressed();

};
```

函数的定义：

```C++
/// .cpp 
widget_plus1::widget_plus1(QWidget *parent):QWidget(parent){}

widget_plus1::~widget_plus1(){}

void widget_plus1::paintEvent(QPaintEvent *event)
{
    QPainter painter(this);
    painter.setRenderHint(QPainter::Antialiasing,true);
    /// 规定线性梯度的样式, 此处线性变形规定起点为(0,0) 终点为(0,height) , 目的是线性变形与横坐标无关, 即水平方向的颜色显示相同
    QLinearGradient Linear(0,0,0,this->height());   
    /// 设置起止点的颜色
    Linear.setColorAt(0,QColor(0,0,0));
    Linear.setColorAt(1,QColor(255,0,0));
    /// 将笔刷设置为刚才设置好的线性梯度变化样式 Linear
    painter.setBrush(Linear);
    painter.setPen(Qt::transparent);
    /// 规定painter的绘画区域, 此处自由设置, 示例中希望绘制区域与窗口尺寸相同
    painter.drawRect(0,0,this->width(),this->height());         
    Q_UNUSED(event);
}

void widget_plus1::mousePressEvent(QMouseEvent *event)
{
    QPoint mouse = event->pos();
    widget_plus1_num = mouse.y() * 255 / this->height();
    emit mousePressed();
}
```

结果展示：

<img src="./pics/press_event__linear_gradien.png">

paintEvent 绘图事件,  在窗体显示影像时使用率非常高

## dragEnterEvent & dropEvent 拖拽事件

实现拖动数据进度该组件并进行处理的情况

dropEnterEvent的官方说明:

This event handler is called when a drag is in progress and the mouse enters this widget. The event is passed in the event parameter.
If the event is ignored, the widget won't receive any drag move events.

当拖动过程中鼠标进入此小部件时，将调用此事件处理程序。事件在事件参数中传递。

如果忽略该事件，小部件将不会收到任何拖动事件。

dropEvent的官方说明:

This event handler is called when the drag is dropped on this widget. The event is passed in the event parameter.

当拖放到此小部件上时，将调用此事件处理程序。事件在事件参数中传递。


[该功能很重要但未来得及测试和学习，故先放链接，待后续学习和使用后再详细说明心得](https://blog.csdn.net/xiaolong1126626497/article/details/114024762)

也可以再QtCreator的帮助中搜索“Drag and Drop”查看文档学习。
