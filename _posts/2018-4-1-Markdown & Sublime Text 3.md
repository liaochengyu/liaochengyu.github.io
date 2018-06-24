---
layout:     post                    # 使用的布局（不需要改）
title:      Markdown & Sublime Text 3              # 标题 
subtitle:    #副标题
date:       2018-04-01              # 时间
author:     LCY                      # 作者
header-img: img/cover/bing_2.JPG    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                              #标签
- 工具
 
---

## sublime text3安装
* 到[sublime text官网](https://www.sublimetext.com/3)下载，傻瓜式安装，此处省略千言万语，然后打开就可以使用了。
* 安装Package Control,使用Ctrl+`快捷键或者通过View->Show Console菜单打开命令行，粘贴如下代码运行：

```
import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read())
```
完成后重启sublime，可以在Preferences菜单下看到Package Settings和Package Control两个子菜单。

* Package Control安装插件： 
1、使用快捷键Ctrl+Shift+P(如果调不出来，可能与其他冲突了，我的就与搜狗五笔输入法的某个快捷键冲突了）或者通过Tools->Command Palette调出命令面板 
2、输入install 调出 Install Package 选项并回车，然后在列表中选中要安装的插件或者直接在输入框中输入你要安装的插件的名字。

## sublime text3常用插件

#### [SublimeREPL](https://blog.csdn.net/dchen1993/article/details/53307263)(可以实现交互和新建窗口运行，实现IDE的作用)

* 1.`cmd+shift+p`调出快捷命令窗口，输入`install`，选择`Package Control:Install Package`（前提是安装了Package Control，如何安装请google，一段     代码的事情） 
* 2.输入`sublimerepl`，选择`sublimeREPL`，然后它就会在后台安装。
* 3.配置快捷键，一般定义以下的快捷键:

```
    {
    "keys": ["f5"],
    "caption": "SublimeREPL: Python - RUN current file",
    "command": "run_existing_window_command",
    "args": {
        "id": "repl_python_run",
        "file": "config/Python/Main.sublime-menu"
            }
     }
```

##### [BracketHighlighter](http://www.cnblogs.com/liu-liang/archive/2013/06/09/3129471.html)(高亮显示括号等)

* 1.打开`package Control`，选择`install Package `
* 2.输入`BracketHighlighter`，回车
* 3.这样该插件会自动安装，安装后所有的提示高亮都是白色或没有提示。按`preferences`-->`package settings`-->`Bracket highlighter`-->`Bracket settings` --> `Default`会打开一个文件
* 4.将`"bracket_styles"`中的`style`改为`hightlight`
* 5.将`"bracket_styles"`以下的样式类型去掉注释
* 6.在`color scheme`查看你所用的配色类型，我用的是`Monokai`
* 7.在`Color Scheme - Default`文件中找到你所使用的配色文件（我的是`Monokai.tmTheme`），打开
* 8.添加以下代码,通过添加这样的代码块并修改颜色和样式名称，获得自己喜欢的高亮提示。

```    
    <dict>
            <key>name</key>
            <string>Bracket Curly</string>
            <key>scope</key>
    <string>brackethighlighter.curly</string>
            <key>settings</key>
            <dict>
                <key>foreground</key>
                <string>#A6E22E</string>
            </dict>
    </dict>
``` 
    
   

## markdown基本语法
[markdown基本语法](http://xianbai.me/learn-md/index.html)

## markdown语法补充
>以下内容是对markdown基本语法的一些补充（不常使用）

#### 照片的居中问题

+ 使用 `<center></center>` 的用法

```
<center>
![TeXstudio](http://img.hb.aicdn.com/233c89ac3ebff6260d497ec761da0fc6c50bb9f7b665b-pFidR8_fw658)
</center>
```
<div align="center">
<img width="150" height="150" src="https://liaochengyu.github.io/img/404.PNG"/>
</div>

+ 使用`<img src="">`的用法规则

```
<img src="https://liaochengyu.github.io/img/404.PNG" width="200" height="250" alt="这是一张照片">
```

<img src="https://liaochengyu.github.io/img/404.PNG" width="200" height="250" alt="这是一张照片">

**note:** 使用`<img src="">`可以控制图片的大小，其中 **alt**表示的对图片的描述， **src**表示图片的地址


####  字体、字号与颜色
```
<font face="黑体">
我是黑体字
</font>  
<font face="微软雅黑">
我是微软雅黑
</font>  
<font face="STCAIYUN">
需要粘贴的内容
</font>  
<font color=#0099ff size=7 face="黑体">
需要粘贴的内容
</font>  
<font color=#00ffff size=72>
需要粘贴的内容
</font>  
<font color=#DC143C size=4> 
需要粘贴的内容
</font>
```

<div align="center">
<font face="宋体" size="5" color="#ff0000">
    我最喜欢markdown编写文档。
</font>
</div>

**note:** 对字体、字号和颜色的控制，主要使用`<font></font>`用法，进行相应的控制

## markdown文件预览

>详细设置请点击[**链接**](https://www.jianshu.com/p/7cbd50058ea3)查看，涉及的主要的插件包括：


* Markdown Eiditing(同于编辑)
* Markdown Preview(在浏览器中查看，快捷键: <kbd>alt</kbd>+<kbd>m</kbd>)
* OmniMarkupPreviewer(在浏览器中实时的查看，快捷键：<kbd>ctrl</kbd>+<kbd>alt</kbd>+<kbd>o</kbd>) 现在使用的是这个。


在浏览器中实时的查看后，使用其打印功能直接另存为为PDF文件，不要选择虚拟打印机进行打印，而直接选择 **另存为PDF文件** 即可，否则，可能出现空白PDF的清况不能实现查找功能。

## sublime快捷键
* [Sublime Text 3插件安装及快捷键的使用](http://blog.csdn.net/paranoidyang/article/details/54379452)
* [sublime快捷键](https://segmentfault.com/a/1190000012118721)

----------------------

**写在最后: 如果本博客对你有一丢丢的帮助，请帮忙点个赞呗（主要赞是太少，显示在那里则不爽），谢谢啦，好人一生平安**

* 第一步：点击我博客的首页，滑动鼠标至页面最后，可看见以下图片，**点击数字**

![](https://raw.githubusercontent.com/liaochengyu/liaochengyu.github.io/master/img/star_1.jpg)

* 第二步：点动鼠标即可，是不是点完浑身轻松呢 ==）

![](https://raw.githubusercontent.com/liaochengyu/liaochengyu.github.io/master/img/star_2.jpg)

