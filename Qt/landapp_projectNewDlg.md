# Project工程文件

LadnApp中，有关Project—工程文件的创建和使用记录。

比较有趣的点：

新建窗口（基于QDialog）与其父类的简单交互：

```C++
    ProjectNewDlg dlg(this);
    if(QDialog::Accepted == dlg.exec())
```

而在`ProjectNewDlg`的创建过程中，点击确定按钮会调用函数`accept()`，即使dlg的返回值`dlg.exec()`为`QDialog::Accpeted`。

现在的project，是创建一个文件夹，并保存一个QgsProject
