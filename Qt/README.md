# Qt QClass & QtWidgets

## QClass

### [QString](./qclass_QString.md)

QString的转码等特性。

### [Qt MD5码](./qclass_QCryptographicHash.md)

md5码，个人理解，是一个加密码，同一个文件会生成唯一不重合的md5码。

使用情景：在写文件的监测功能时，需要保存检测过的历史信息，那么将检测文件夹的地址作为地址非常合适，但仅有一个问题：地址无法作为文件名保存。

### [文件(夹)监测](./qclass_QFileSystemWatcher.md)

QFileSystemWatcher是Qt自带的一个文件夹监控类，可以检测某一文件或者某一路径的文件变化情况。

监控文件夹，只能监控文件夹是否发生改变，无法监控具体的改变内容，需要再添加函数。

## QtWidgets

### [QTableWidget](./qtwidgets_tablewidget.md)

- 表格属性

- 单双击事件区分

### [QWidget事件](./qtwidgets_widget_event.md)

- 绘图事件

- 拖拽事件
