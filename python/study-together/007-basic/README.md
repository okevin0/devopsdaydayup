组团学Python第7期班会-缩进/标识符/关键字/注释

同学们好！欢迎大家继续我们的第7期不定期班会，一起来系统的学习Python。

本期学习内容：基础知识大杂烩（缩进/标识符/关键字/注释）

这一期是在我们正式进入Python主环节前的基础知识科普大杂烩。所谓主环节，是指Python的数据类型（Data Type）、流程控制（Control Flow）、函数（Function）、类（Class）与对象（Object）、异常处理（Exception）、文件读写（File Read/Write）、模块（Module）等这些大部分Python书都会着重介绍的内容。

今天的内容概念虽然琐碎，但是非常基础且重要，值得我们提前了解一下。


缩进
我们在之前介绍Python这门语言的特点的时候，有提到它“近乎洁癖的缩进格式规范”。在表示一段有层次关系的代码的时候，比如for或if语句（这个以后会介绍），一些语言会使用诸如大括号｛｝的符号把语句里的所有相关代码括起来，这样程序才知道它们的之间的从属关系。理论上，只要在括号里，你写成一整行都无所谓，虽然难看了点。当然为了美观整齐，更方便其他人阅读，大家约定俗成的按照缩进整齐排列。

但是Python比较特别，它没有使用这些符号，而是把这种美观的缩进硬性规定了。你如果缩进错了，系统会直接无情的报错。

这让我想起初中时候打篮球，隔壁班有个篮球高手，每次和他打，如果投球姿势不好看，他都会补上一句：“动作太丑，进球无效”。大概就是这个意思。

关于更多缩进知识点，请参考廖神的这篇文章：https://www.liaoxuefeng.com/wiki/1016959663602400/1017063413904832


注释
所谓的注释，就是Python解释器不解释的语句，这些语句让你有机会用自然语言给你的程序添加说明，让阅读你代码的人（或者未来的你自己）能更好的理解这段代码的含义或用途。更通俗的说，注释就是代码的说明书。

通常用井号#开头的段落解释器就会忽略其后面的内容。比如：

\# 大家好，我是注释，请忽略我
print("Hello Python people!")

上面这段代码的第一行就这样被跳过了。

有时候我们在调试程序的时候也会临时把一段代码注释掉先不执行，以后需要这个语句的时候只要删掉#就可以了。这个功能在一些IDE里有快捷键，比如在VScode里快捷键是:

MacOS:
Shift + Option + A:
/* 多
    行 */
CMD + /:
// 单行

Windows:
Shift + Alt + A:
/* 多
    行 */

CTRL + /:
// 单行


在代码之后也可以写注释，比如:

print("Hello Python people!") # 大家好，我是注释，请忽略我

这个Pyhon也支持。

不过这里有一个例外，就是有时候你会看到文件第一行会有个这样的语句 #！/usr/bin/python3，这个就不是注释了，尤其是在Linux或Mac环境里，这一行会告诉系统解释器程序的具体位置在哪，这就好像在Windows里的扩展名的功能一样，.doc程序会用Word打开, .xml会用Excel打开一样。如果没有它，你必须手动指定解释器的具体位置，比如：

$ /usr/bin/python3  /path/to/helloworld.py


但是有了它，你就可以这样（注：前提是该文件可执行)

cd /path/to/file
./helloworld.py

这个和Shell脚本是一样的，它还有个专门的名字，叫做shebang（she指的是#，bang指的是！）

关于代码注释，我们一定要小心，不要注释一些正确的废话。注释的目的主要是阐述代码的用途和原理，也就是做什么怎么做，还有就是要力求简单无奇异。这个以后在我们介绍如何优化代码的可读性的时候会再介绍。


标识符

标识符就是变量、函数（重复利用的代码段）、类（创建对象的模板）、属性（类里面的变量）等可以由程序员指定的代码元素。

标识符的字符不可以随意命名，它遵循以下命名规则：

1.大小写有区别，Myname和myname是两个不同的标识符
2.首字可以是下划线或字母，但不能是数字。myname和_myname都是合法标识符，2myname或2_myname就不合法，程序会报错。
3.除了首字符外只能是字母数字或下划线，不能包含其他特殊字符，比如myname$ 就不合法会报错。
4.关键字不能作为标识符（下面会讲什么是关键字）
5.不要使用Python内置函数作为标识符，以后班会再和大家介绍什么是内置函数


这几条命名规则一定要谨记了，因为Python考试会考。


关键字

在Python中有一些字符被程序保留用作特殊用途，比如and，or，True，if等，一共33个，除了True，False和None以外，都是小写。具体可参照：https://www.geeksforgeeks.org/python-keywords-and-identifiers/amp/


语句

Python中一行代码代表一条语句，语句的结尾一般不加分号，不过你加了也不会报错，只是不符合Python规范而已。

以上为一些你必须知道的基础知识。下一期班会开始，我们就会开启主环节模式，先从最重要的数据类型开始。我们下期见！

今日练习：使用vscode快捷键注释一段语句