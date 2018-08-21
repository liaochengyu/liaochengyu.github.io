# 第一章 .NET之道

.NET可以理解为 **运行库环境** 和 **基础类库**

概念：
+ COM: component object model, 组件对象模型
+ CLR: common language runtime, 公共语言运行库，主要为我们定位、加载和管理.NET类型
+ CTS: common type sytem, 公共类型系统，CTS完整的我描述了运行库所支持的所有可能的数据类型和编程结构，它指的是一个集合{类、接口、委托、枚举、结构}，每个类型又是一个集合{构造函数、终结器、静态构造函数、嵌套类型、操作符、属性、索引器、字段、只读字段、常量、事件}中的一些元素
+ CLS: common language specification, 公共语言规范
+ BCL: base class library, 基础类库，封装了各种基本类型，如线程、文件输入和输出、图形绘制以及与各种硬件设备的交互
+ 托管语言：C#/VB/C++/JS/F#
+ 托管代码: managed code，简单来说就是必须运行在.NET运行库下的代码成为托管代码

