---
layout:     post                    # 使用的布局（不需要改）
title:      Decorator              # 标题 
subtitle:    #副标题
date:       2018-04-03              # 时间
author:     LCY                      # 作者
header-img: img/cover/bing_5.JPG    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                              #标签
- python

---
>本篇博客是根据学习[廖雪峰python教程](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/0014318435599930270c0381a3b44db991cd6d858064ac0000)而记录的笔记，你可以移步，也可以直接看我的笔记（内容有一定补充和删减，包括一些自己的理解）。

> 函数是Python内建支持的一种封装，我们通过把大段代码拆成函数，通过一层一层的函数调用，就可以把复杂任务分解成简单的任务，这种分解可以称之为面向过程的程序设计。函数就是面向过程的程序设计的基本单元。
> 
> 而函数式编程（请注意多了一个“式”字）——Functional Programming，虽然也可以归
> 结到面向过程的程序设计，但其思想更接近数学计算。


----------------
### 匿名函数
大家可能还不知道，在我的另一篇博客[Data Structure List](https://liaochengyu.github.io/2018/04/02/Data-Structure-List/)中，有段代码就已经使用了匿名函数。

```python
>>> squares = list(map(lambda x: x**2, range(10)))
>>> squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```
* 关键字`lambda`表示匿名函数，冒号前面的`x`表示函数参数看，冒号后面的表示函数的表达式，
匿名函数有个限制，就是 **只能有一个表达式**，不用写`return`，返回值就是该表达式的结果。
* 匿名函数也是一个函数对象，也可以吧匿名函数赋值给一个变量，再利用变量来调用该函数。

```python
>>> f=lambda x: x**3
>>> f
<function <lambda> at 0x00000000010DE048>
>>> f(9)
729
```
* 还可以把匿名函数作为返回值返回，即 `return lambda x: x**3`

----------------
### 装饰器

* 简单来说，就是在代码运行期间，在不修改现有函数的基础上，`动态的增加函数功能`的代码，就称之为“**装饰器**”（decorator），翻译的还是比较的形象，贴近国人思维和它本身的功能的。

----------------

##### 主要运用场景
1. 注入参数（提供默认参数，生成参数）
2. 记录函数行为（日志、缓存、计时什么的）
3. 预处理／后处理（配置上下文什么的）
4. 修改调用时的上下文（线程异步或者并行，类方法）

----------------

##### example
* 接下来我们来看看一个简单的例子，来加深对装饰器的理解：
```python
def studying():
    return 'liaochengyu is studying'
```
这是一个简单的函数，直接返回一个字符串。

* 现在如果我要增加一些内容，比如添加一个日期信息，该怎么做呢？按照传统的可以直接在原函数的基础上添加即可。

* 那现在就有一个问题了，如果有其他的函数也需要这样的功能，也这样暴力的一个一个的添加吗？显然不科学嘛，毕竟python这么的强大。这时候装饰器就派上用场了。

```python
import time
def date(func):
    def wrapper():
        date = time.strftime("%d/%m/%Y")
        print('on the %s , %s'%(date,func()))
    return wrapper
@date
def studying():
    return ('liaochengyu is studying')
@date
def resting():
    return(' liaochengyu is resting')
```

```python
resting()
studying()
on the 03/04/2018 ,  liaochengyu is resting
on the 03/04/2018 , liaochengyu is studying
```
这样一来，定义好装饰器后，我们就可以通过`@语法`使用了，使用装饰器输出我们想要的结果，使用了装饰器的函数就具有了装饰器所赋予的额外功能。

* 除此之外，装饰器还可以带参数，这样具有更大的灵活性

```python
import time
def decorator(place):
    def date(func):
        def wrapper():
            date = time.strftime("%d/%m/%Y")
            print('on the %s and %s , %s'%(date,place,func()))
        return wrapper
    return date

@decorator('library')
def studying():
    return ('liaochengyu is studying')
@decorator('bedroom')
def resting():
    return(' liaochengyu is resting')
```

```python
resting()
studying()
on the 03/04/2018 ,  liaochengyu is resting
on the 03/04/2018 , liaochengyu is studying
```

* 装饰器的参数除了允许基本类型，还允许`类`作为参数。
还有类装饰器，改变函数`__name__`等内容，以上这部分有时间再补上。



-----------
### 参考文献
* [理解 Python 装饰器就看这一篇](https://www.zhihu.com/question/31265857)
* [廖雪峰python教程](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/0014318435599930270c0381a3b44db991cd6d858064ac0000)
* [装饰器笔记](https://www.jianshu.com/p/1e2394733e77)

--------------


**写在最后: 如果本博客对你有一丢丢的帮助，请帮忙点个赞呗（主要赞是太少，显示在那里则不爽），谢谢啦，好人一生平安**

* 第一步：点击我博客的首页，滑动鼠标至页面最后，可看见以下图片，**点击数字**

![](https://raw.githubusercontent.com/liaochengyu/liaochengyu.github.io/master/img/star_1.jpg)

* 第二步：点动鼠标即可，是不是点完浑身轻松呢 ==）

![](https://raw.githubusercontent.com/liaochengyu/liaochengyu.github.io/master/img/star_2.jpg)






