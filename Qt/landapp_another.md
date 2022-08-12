# LandApp / IO, Plot, QXlsx & Util

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [LandApp / IO, Plot, QXlsx & Util](#landapp--io-plot-qxlsx--util)
  - [IO](#io)
  - [Plot](#plot)
  - [QXlsx](#qxlsx)
  - [Util](#util)

<!-- /code_chunk_output -->

## IO

主要是文本的读read写write，以及拆分splitLine操作。

其中splitLine有两种方式，当输入一个参数QString时，函数会打开QString对应的文本文档，逐行拆分并输出QStringList；当输入两个参数QString、QString时，函数会以第二个QString作为分隔符，拆分第一个QString并输出QStringList。

## Plot

调用qcustomplot函数（是一个基于Qt的画图和数据可视化C++控件）。QCustomPlot 致力于提供美观的界面，高质量的2D画图、图画和图表，同时为实时数据可视化应用提供良好的解决方案。

## QXlsx

是一个读取excel的，开源软件库。

## Util

共包含三个函数、分别是：

1.QStringList util::readFromCSV(QString filename)：xt/csv数据的读取，逐行存储值QStringList并输出；

2.void util::LongitudeLatitudeToDMS(double value, int &deg, int &min, int &sec)：输入经纬度，转换为度分秒。

3.QString util::LongitudeLatitudeToDMS(double value)：输入经纬度，转换为度分秒，文本形式输出“%1° %2′ %3″ ”。