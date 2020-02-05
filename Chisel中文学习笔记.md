# Chisel 中文学习笔记

## 自己的一些想法

- 当初学习HDL时就有想法将其升级为面向对象编程的想法，因为自己挺喜欢做框架之类的东西的，但是当时因为自身技术限制的原因就没有实现。当risc-v公开的时候，当时吸引我的其实是Chisel的出现，也许是之前做游戏开发的缘故吧，就像是我初三那年苹果的WWDC上发布的swift语言一样震撼，苹果实现了自家的硬件跑自家的软件，到现在的使用自家的编程语言，真正实现了“自家的东西自家用”的理念，所以就立马产生了学习Chisel这门语言的想法。
- 写这篇的目的也是督促自己，就像是在游戏CS中学到的一样：人不要站在没用的地方。也为了监督自己，做框架，做系统的东西。"...God loves those who make people laugh. ..."-- _Amusing Ourselves to Death_
- 此文档目前先存在于risc-v项目下，等篇幅到一定容量后再考虑移动位置吧。

## 学习资源

我们以官方的学习资源为准，毕竟自己写的东西自己最清楚。

- [Chisel的官网](https://www.chisel-lang.org/)
- [Chisel安装相关](https://github.com/freechipsproject/chisel3/blob/master/SETUP.md)
- [Chisel的wiki网站](https://github.com/freechipsproject/chisel3/wiki)

Chisel是基于Scala的，所以有Scala的学习经验的话，会很好的帮助理解Chisel，当然在遇到Chisel的一些难解的问题时，翻翻Scala的手册也是很好的解决办法。

- [Scala的官方教程](https://docs.scala-lang.org/)
- 这本[Scala语言规范的中文版](https://static.runoob.com/download/Scala%E8%AF%AD%E8%A8%80%E8%A7%84%E8%8C%83.pdf)也有很大的参考价值，在此项目下也有备份可供大家下载。

这里很是推荐在学习了Scala的同时，将Scala的[_style guide_ 这本手册](https://docs.scala-lang.org/style/index.html)认真阅读，它将帮助我们写出更加具有Scala味道的代码。不仅可以提升自己代码的阅读与理解速度，也便于交流，当然对于编译器的编译后执行效率的提高还有待考证。

[chisel的api网站](https://www.chisel-lang.org/api/latest/)，这里可以找到[Chisel3主要的api列表](https://www.chisel-lang.org/api/latest/chisel3/index.html)


## 开始学习吧！
