---
layout:     post                    # 使用的布局（不需要改）
title:      Matplotlab               # 标题 
subtitle:                            #副标题
date:       2018-04-04              # 时间
author:     LCY                      # 作者
header-img: img/bing_6.JPG    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                              #标签
- python
- Matplotlab
- 可视化


---
>`Python` 究竟如何在数据分析领域做到游刃有余？因为它有“四板斧”，分别是`Matplotlib、NumPy、SciPy、Pandas`。本篇博客是用于记录在我学习`python`的数据可视化包`Matplotlab`中内容。包括其基本使用和在学习过程中所遇到的一些问题。

* `Matplotlib` ：是画图工具
* `NumPy`：是矩阵运算库
* `SciPy` ：是数学运算工具
* `Pandas` ：是数据处理的工具

---

 俗话说“知己知彼，百战不殆”，在学习某个模块之前，就要了解，学习完之后我能用它来做什么，他有什么样的功能，在这里就不说了，大家可以直接移步维基百科[matplotlib](https://zh.wikipedia.org/wiki/Matplotlib)，不能科学上网的参考其他百科也行。这里给出`Matplotlab`的[官方网页](https://matplotlib.org/index.html#)。
 接下来首先推荐一个基础的[入门教程](https://pythonprogramming.net/matplotlib-intro-tutorial/)，这个教程主要是利用`matplotlab`进行 **数据可视化**操作，可以借此来熟悉使用`matplotlab`功能，不过它是 ~~英文版~~ 的，其中包括视频教程和文本教程。如果外文对有些朋友不是很友好的话，你也可以参考大佬在简书上的[翻译版](https://www.jianshu.com/p/aa4150cf6c7f)。

接下来的两篇帖子都是比较适合初学者阅读的，可以比较快速的对matplotlib有一个比较全面的认识。

* https://www.jianshu.com/p/ebe721199d72 
* https://www.jianshu.com/p/78ba36dddad8

----------------
#### 图形要素基本概念
* 首先，你要绘制一幅图，就要知道它是由哪些要素所构成的，他们的基本含义又是什么？下面这张图可以帮助我们对`matplotlib`所绘图要素有一个基本的认识。
    * 标题(title)：就是所绘图像名字
    * 图例(legend)：区别一幅图中的不同曲线
    * 网格(grid)：网格便于观察图像
    * 图标(makers)：标记，有许多不同符号的选择
    * 边框(spines)：
    * 子图(axes)：一个figure中可以有多个子图
    * x轴( x axis)：表述对应轴所代表的含义
    
![](https://upload-images.jianshu.io/upload_images/7931281-8aa927f71b6854f2.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

* `Axis` 和 `Axes` 以及 `Figure` 这三者关系，你看完下图，会恍然大悟。
![](https://upload-images.jianshu.io/upload_images/7931281-45a5018dcaad5bfb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/385)
