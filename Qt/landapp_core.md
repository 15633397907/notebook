# LandApp / Core

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [LandApp / Core](#landapp--core)
  - [Core::RegExp](#coreregexp)
  - [Core::SysSpace](#coresysspace)
    - [QstandardPaths](#qstandardpaths)
      - [a.displayName()](#adisplayname)
      - [b.findExecutable()](#bfindexecutable)
      - [c.writableLocation()](#cwritablelocation)
      - [举例](#举例)
    - [slovePath()](#slovepath)
    - [writeFile()](#writefile)

<!-- /code_chunk_output -->

## Core::RegExp

RegExp属于core库，只有.h文件，记录了（#define）部分常用的正则表达式。

```C++
#define _Reg_Number "^[-|+]?[0-9]*$"
#define _Reg_Number_N "^\\d{n}$"
#define _Reg_Float "^[-|+]?([1-9]\\d*\\.\\d*|0\\.\\d*[1-9]\\d*|0?\\.0+|0)$"
#define _Reg_Telephone "^(12[0-9]|14[5|7]|15[0|1|2|3|5|6|7|8|9]|18[0|1|2|3|5|6|7|8|9])\\d{8}$"
```

## Core::SysSpace

SysSpace属于core库，负责调用计算机中的标准路径（QStandardPaths类）。**solvePath()**函数负责调用InSAR_Console.exe所在路径（qapplicationDirPath+“/./plugins/InSAR_Console/InSAR_Console.exe”）;writeFile(QString, QStringList)将QStringList中存储的文本存储到QString路径下;docPath()函数负责调用操作手册路径。

### QstandardPaths

configPath()里用到了QStandardPaths 顾名思义为标准路径，用于解决不同操作系统（跨平台）标准路径不同的问题，例如“我的文档”在不同操作系统中的目录位置

|操作系统|路径|
|:-:|:-:|
|windows|C:/Users/Documents|
|Linux|~/Documents|

#### a.displayName()

QString QStandardPaths::displayName(QStandardPaths::StandardLocation type)

根据标准目录类型化，返回对应的本地名称，如果找不到，返回空QString。 例如指定type为DesktopLocation，则返回桌面名称；DocumentsLocation，则返回文档目录名称。

> `qDebug()<<QStandardPaths::displayName(QStandardPaths::DesktopLocation)`
>
> ​           `<<QStandardPaths::displayName(QStandardPaths::DocumentsLocation);`

（可以自行实验查看输出值）

#### b.findExecutable()

QString QStandardPaths::findExecutable(const QString &executableName, const QStringList &paths = QStringList())

在指定的路径中查找名为executableName的可执行文件，如果paths为空，则在系统路径中查找。 系统路径指PATH环境变量的值。 如果存在，返回可执行文件的绝对文件路径，如果没有找到，则返回空字符串。

> `QStringList paths;`
> `paths << "D:/notepadd++/soft/Notepad++";`
> `qDebug()<<QStandardPaths::findExecutable("notepad++", paths);`

（可以自行实验查看输出值）

#### c.writableLocation()

QStandardPaths::writableLocation(QStandardPaths::StandardLocation type)

用法与displayName()相似，返回对应的本地目录。如果找不到，返回空QString。

 #### 举例

`// displayName`
`qDebug() << "DesktopLocation: " << QStandardPaths::displayName(QStandardPaths::DesktopLocation);`
`qDebug() << "DocumentsLocation: " << QStandardPaths::displayName(QStandardPaths::DocumentsLocation);`
`qDebug() << "FontsLocation: " << QStandardPaths::displayName(QStandardPaths::FontsLocation);`
`qDebug() << "ApplicationsLocation: " << QStandardPaths::displayName(QStandardPaths::ApplicationsLocation);`
`qDebug() << "MusicLocation: " << QStandardPaths::displayName(QStandardPaths::MusicLocation);`
`qDebug() << "MoviesLocation: " << QStandardPaths::displayName(QStandardPaths::MoviesLocation);`
`qDebug() << "PicturesLocation: " << QStandardPaths::displayName(QStandardPaths::PicturesLocation);`
`qDebug() << "TempLocation: " << QStandardPaths::displayName(QStandardPaths::TempLocation);`
`qDebug() << "HomeLocation: " << QStandardPaths::displayName(QStandardPaths::HomeLocation);`
`qDebug() << "DataLocation: " << QStandardPaths::displayName(QStandardPaths::DataLocation);`
`qDebug() << "CacheLocation: " << QStandardPaths::displayName(QStandardPaths::CacheLocation);`
`qDebug() << "GenericCacheLocation: " << QStandardPaths::displayName(QStandardPaths::GenericCacheLocation);`
`qDebug() << "GenericDataLocation: " << QStandardPaths::displayName(QStandardPaths::GenericDataLocation);`
`qDebug() << "RuntimeLocation: " << QStandardPaths::displayName(QStandardPaths::RuntimeLocation);`
`qDebug() << "ConfigLocation: " << QStandardPaths::displayName(QStandardPaths::ConfigLocation);`
`qDebug() << "DownloadLocation: " << QStandardPaths::displayName(QStandardPaths::DownloadLocation);`
`qDebug() << "GenericConfigLocation: " << QStandardPaths::displayName(QStandardPaths::GenericConfigLocation);`
`qDebug() << "AppDataLocation: " << QStandardPaths::displayName(QStandardPaths::AppDataLocation);`
`qDebug() << "AppLocalDataLocation: " << QStandardPaths::displayName(QStandardPaths::AppLocalDataLocation);`
`qDebug() << "AppConfigLocation: " << QStandardPaths::displayName(QStandardPaths::AppConfigLocation);`
`// findExecutable`
`qDebug() << QStandardPaths::findExecutable("cmd.exe");`
`// writableLocation`
`qDebug() << QStandardPaths::writableLocation(QStandardPaths::DownloadLocation);`
`qDebug() << QStandardPaths::writableLocation(QStandardPaths::AppDataLocation);`

[原文链接](https://blog.csdn.net/luoshabugui/article/details/88012838)

### slovePath()

return QDir(qApp->applicationDirPath() + "/./plugins/InSAR_Console/InSAR_Console.exe").absolutePath();

展示了qApp与InSAR_Console的相对位置关系

### writeFile()

writeFile(QString filename, QStringList &text)

实际应用中，filename是文件路径，text是存储配置文件内容的QStringList。

……
