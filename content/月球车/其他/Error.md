## NameError: name 'xxx' is not defined
[Python中对错误NameError: name 'xxx' is not defined进行总结 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/183863747)

## ndentationError:expected an indented block
[(58条消息) python问题：IndentationError:expected an indented block错误解决_NeilHappy的博客-CSDN博客](https://blog.csdn.net/neilhappy/article/details/7724959)
```
Python语言是一款对缩进非常敏感的语言，给很多初学者带来了困惑，即便是很有经验的Python程序员，也可能陷入陷阱当中。最常见的情况是tab和空格的混用会导致错误，或者缩进不对，而这是用肉眼无法分别的。

在编译时会出现这样的错_**IndentationError:expected an indented block**_说明此处需要缩进，你只要在出现错误的那一行，按空格或Tab（但不能混用）键缩进就行。

往往有的人会疑问：我根本就没缩进怎么还是错，不对，该缩进的地方就要缩进，不缩进反而会出错，，比如：

_**if xxxxxx：**_

_**（空格）xxxxx**_

或者

_**def xxxxxx：**_

_**（空格）xxxxx**_

还有

_**for xxxxxx：**_

_**（空格）xxxxx**_

一句话 有冒号的下一行往往要缩进，该缩进就缩进
```
