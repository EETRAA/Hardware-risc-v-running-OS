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
- [Chisel的api网站](https://www.chisel-lang.org/api/latest/)，这里可以找到[Chisel3主要的api列表](https://www.chisel-lang.org/api/latest/chisel3/index.html)

Chisel是基于Scala的，所以有Scala的学习经验的话，会很好的帮助理解Chisel，当然在遇到Chisel的一些难解的问题时，翻翻Scala的手册也是很好的解决办法。

- [Scala的官方教程](https://docs.scala-lang.org/)
- 这本[Scala语言规范的中文版](https://static.runoob.com/download/Scala%E8%AF%AD%E8%A8%80%E8%A7%84%E8%8C%83.pdf)也有很大的参考价值，在此项目下也有备份可供大家下载

这里很是推荐在学习了Scala的同时，将Scala的[_style guide_ 这本手册](https://docs.scala-lang.org/style/index.html)认真阅读，它将帮助我们写出更加具有Scala味道的代码。不仅可以提升自己代码的阅读与理解速度，也便于交流，当然对于编译器的编译后执行效率的提高还有待考证。

## 开始学习吧！

官方的推荐是从[Chisel Bootcamp](https://github.com/freechipsproject/chisel-bootcamp)开始来认识Chisel。本教程是基于Jupyter的，这里有[在线版本](https://mybinder.org/v2/gh/freechipsproject/chisel-bootcamp/master)，无需安装Jupyter。

还有一本[Cookbook](https://github.com/freechipsproject/chisel3/wiki/Cookbook)可供参考，此书写了一些用Chisel实现的电路的例子。

官方也贴心的为我们提供了一份Chisel的[CheatSheet](https://github.com/freechipsproject/chisel-cheatsheet/releases/latest/download/chisel_cheatsheet.pdf)。可以将此打印出来或者下载下来作为提示。

Chisel Bootcamp，使用的是Jupyter，这个工具有很多的好处，它可以边学习边查看代码，在当前的界面便可以查看到运行的结果。重要的是当前Jupyter已被很多人使用，所以还是很有必要去学习一下这个工具的。安装的时候推荐使用[Anaconda](https://www.anaconda.com)安装Jupyter，Anaconda为python套件，有很多东西都会帮忙安装好，**我们为了学习而不是去学习如何安装软件**，就直接采用Anaconda的方案吧。

安装时记得去查看距离自己最近的镜像站，有很好的加速作用。比如我所在的地方使用[ustc的镜像站](http://mirrors.ustc.edu.cn/)便可以有很好的加速效果。

安装好之后就可以在没有联网的情况下撒欢地学习啦，当然最重要的是有时官方网站速度很慢，等待加载的时间太痛苦了。


在Scala中if语句会返回值，是一个很强大的功能，特别是使用在函数和类的初始化中。
```Scala
val likelyCharactersSet = if (alphabet.length == 26)
    "english"
else 
    "not english"

println(likelyCharactersSet)//来自官方的教程
```

函数：当函数没有参数时，不需要()双括号。一般来说，无双括号的函数仅仅会返回一个值而不是改变一些东西，当函数确实会改变类的变量或者是打印一些东西时，则需要双括号。

Scala支持函数重载，但是官方建议避免使用。

Scala的for语句：
```Scala
for (i <- 0 to 7) { print(i + " ") }
println()//这里是从0到7

for (i <- 0 until 7) { print(i + " ") }
println()//这里是从0到6

for(i <- 0 to 10 by 2) { print(i + " ") }
println()//步进为2
```
for语句可便利一个结构中的所有元素。





































<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
我们会时不时的遇到这几个名词：Chisel，FIRRTL，iotesters(Chisel Testers)，testers2(chisel-testers2)，treadle，diagrammer(Chisel / FIRRTL Diagramming Project)。

- Chisel：代表了Chisel这门语言本身，加上Chisel标准库和Chisel测试便利工具，这三个东西一起提供了一种新的硬件设计的方法。

- FIRRTL：是在Chisel之后的开发用来编译电路的编译器。实现了后端的描述，自动的电路转换，还有重要的**Verilog代码生成。**

- iotesters：IO测试，包含三种测试方法。

- testers2：将来替代iostesters的。

- treadle：实验性的电路仿真器，未来将成为iotesters项目的一部分。

- diagrammer：生成由Chisel构建的电路的层次图。由GraphViz项目驱动。(话说以前还有研究过使用此引擎写一个代码函数调用解析器来着，最后发现又撞到了一个已经被人研究过的领域了，什么静态解析，动态解析，比我想的周到多了)

验证相关：目前有三种测试方法，以Chisel模块的方式呈现。IO端口的类型决定了使用哪个模块。

这三个模块分别是：
>1. [PeekPokeTester](https://www.chisel-lang.org/>chisel-testers/#peekpoketester)
>2. [SteppedHWIOTester](https://www.chisel-lang.org/>chisel-testers/#steppedhwiotester)
>3. [OrderedDecoupledHWIOTester](https://>www.chisel-lang.org/chisel-testers/>#ordereddecoupledhwiotester)

其中特殊的是PeekPokeTester，它支持两种不同的后端，Firrtl Interpreter，verilator backend。
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
Appendix：
