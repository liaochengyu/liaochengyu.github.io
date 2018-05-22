---
layout:     post                    # 使用的布局（不需要改）
title:      Data Structure List               # 标题 
subtitle:    #副标题
date:       2018-04-02              # 时间
author:     LCY                      # 作者
header-img: img/bing_4.JPG    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                              #标签
- python
- 数据结构 
---


> 本篇博客主要记录python中最常见的数据结构 **list** ，包含怎么创建`list`对象、访问、删除、更新等其他的一些常见的操作，可能归纳的不是很完善，有需要的朋友们，凑合着看看吧。

----------------

### 创建列表
* 直接使用`[]`进行创建，元素直接使用`，`进行分割
```python
words=['my','name','is','liaochengyu']
print(words)
```
**run:**
```python
['my', 'name', 'is', 'liaochengyu']
```
* 使用面向对象的方式创建
```python
words=list()
```

* `list`里面的元素的数据类型也可以不同，当然在列表里面也可以继续的嵌套`list`
```python
>>> L = ['Apple', 123, True,['my', 'name', 'is', 'liaochengyu']]
```

------------
### 访问列表
* 用索引来访问`list`中每一个位置的元素，记得索引是从`0`开始的，比如我们要访问words列表中的第一个元素，直接使用`words[0]`即可
```python
>>> words[0]
'my'
```
* 除了使用正的索引以外，还可以使用负索引，比如我们要访问最后一个元素，可以直接使用`words[-1]`
```python
>>> words[-1]
'liaochengyu'
```
* 列表对象还支持`切片`操作，`list[start:end:step]`，同样也可以有正负之分，根据实际情况而定
```python
>>> words[1:3]
['name', 'is']
```
**notice:**不要访问list中不存在的索引，否则会抛出`IndexError`错误，索引的最后一个为 `len(list)-1`（如果使用正索引的话），可以使用`len`函数获取长度

-------------
### [列表的常用方法](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)

*  `list.append("增加的列表元素")`，在列表的尾部追加一个元素
```python
>>> words.append('handsome')
>>> words
['my', 'name', 'is', 'liaochengyu', 'handsome']
```

* `list.index(“列表元素”)`，获取所需列表元素的序号，如我想获取``liaochengyu`这个元素在`list`中的索引信息
```python
>>> words.index('liaochengyu')
3
```

* `list.insert(序号，“列表新元素”)`，插入列表序号位置的新元素，后面的元素依次往后移动

```python
>>> words.insert(4,'beasts')
>>> words
['my', 'name', 'is', 'liaochengyu', 'beasts', 'handsome']
```

* `list.remove("列表元素")`，删除列表中的第一次（左侧开始数）出现的元素

```python
>>> words.remove('beasts')
>>> words
['my', 'name', 'is', 'liaochengyu', 'handsome']
```

* `list.count("列表元素")`，获取列表元素的个数
```python
>>> words.count('my')
1
>>> words.count('beautiful')
0
```


* `list.reverse()`，列表元素元素反转
```python
>>> words.reverse()
>>> words
['handsome', 'liaochengyu', 'is', 'name', 'my']
```

* `list.sort()`，列表的排序，按照元素首字母进行排序
```python
>>> words.sort()
>>> words
['handsome', 'is', 'liaochengyu', 'my', 'name']
```

* `list.pop()`，删除list末尾的元素(或者添加索引信息，删除对应的元素)，并返回
```python
>>> words.pop()
'name'
>>> words
['handsome', 'is', 'liaochengyu', 'my']
```


* 使用`del`语句来删除列表的的元素
```python
>>> words
['handsome', 'is', 'liaochengyu', 'my']
>>> del words[1]
>>> words
['handsome', 'liaochengyu', 'my']
```

* 其他的一些方法

 |操作|含义|
  :---:|:---:
`cmp(list1, list2) `|比较两个列表的元素
`len(list) `|获取列表元素个数
`min(list) `|返回列表元素最小值 
`min(list) `|返回列表元素最小值 
`max(list) `|返回列表元素最大值
`list.extend(seq)`|在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）
`list.clear() `|移除所有的元素，等价于`del a[:]`

* 列表对`+`和 `*`的操作符与字符串相似。`+` 号用于组合列表，`*`号用于重复列表。

Python |表达式 | 结果描述
 :---:|:---:|:---:
len([1, 2, 3]) | 3  |长度
[1, 2, 3] + [4, 5, 6]  | [1, 2, 3, 4, 5, 6]  |组合
['Hi!'] * 4 |['Hi!', 'Hi!', 'Hi!', 'Hi!']   | 重复
3 in/not in [1, 2, 3] | True    |元素是否存在于列表中
for x in [1, 2, 3]: print x, |   1 2 3  | 迭代
--------------
### 列表生成器(List Comprehensions)
* 举个列子，如果我们要生成一系列平方数的序列，我们可以这样做：
```python
>>> squares = []
for x in range(10):
    squares.append(x**2)
>>> squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```
但显得非常的繁琐，完全有悖于简洁语言`python`的风格，怎么能忍呢。
我们利用列表生成器一条语句就搞定了。
```python
>>> squares = list(map(lambda x: x**2, range(10)))
>>> squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```
等价于：
```python
squares = [x**2 for x in range(10)]
```
* 我们还可以添加`if`语句生成更加复杂的`list`

```python
>>> [(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]

[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```
等价于：
```python
>>> combs = []
>>> for x in [1,2,3]:
...     for y in [3,1,4]:
...         if x != y:
...             combs.append((x, y))
>>> combs
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```
* 我们还可以进行嵌套生成我们所需列表
```python
>>> matrix = [[1, 2, 3, 4],[5, 6, 7, 8],[9, 10, 11, 12]]
```

```python
>>> [[row[i] for row in matrix] for i in range(4)]
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```
等价于：
```python
>>> transposed = []
>>> for i in range(4):
...     transposed.append([row[i] for row in matrix])
>>> transposed
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```
----------------------

**写在最后: 如果本博客对你有一丢丢的帮助，请帮忙点个赞呗（主要赞是太少，显示在那里则不爽），谢谢啦，好人一生平安**

* 第一步：点击我博客的首页，滑动鼠标至页面最后，可看见以下图片，**点击数字**

![](https://raw.githubusercontent.com/liaochengyu/liaochengyu.github.io/master/img/star_1.jpg)

* 第二步：点动鼠标即可，是不是点完浑身轻松呢 ==）

![](https://raw.githubusercontent.com/liaochengyu/liaochengyu.github.io/master/img/star_2.jpg)





