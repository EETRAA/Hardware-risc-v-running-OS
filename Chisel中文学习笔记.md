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
- [Chisel的api网站](https://www.chisel-lang.org/api/latest/)，这里可以找到[Chisel3主要的api列表](https://www.chisel-lang.org/api/latest/chisel3/index.html)，当然不要忘了[向上层查看](https://www.chisel-lang.org/api)
- [Cookbook](https://github.com/freechipsproject/chisel3/wiki/Cookbook)
- [CheatSheet](https://github.com/freechipsproject/chisel-cheatsheet/releases/latest/download/chisel_cheatsheet.pdf)

Chisel是基于Scala的，所以有Scala的学习经验的话，会很好的帮助理解Chisel，当然在遇到Chisel的一些难解的问题时，翻翻Scala的手册也是很好的解决办法。

- [Scala的官方教程](https://docs.scala-lang.org/)
- 这本[Scala语言规范的中文版](https://static.runoob.com/download/Scala%E8%AF%AD%E8%A8%80%E8%A7%84%E8%8C%83.pdf)也有很大的参考价值，在[此项目][(](https://github.com/EETRAA/Hardware-risc-v-with-OS-support))下也有备份可供大家下载

这里很是推荐在学习了Scala的同时，将Scala的[_style guide_ 这本手册](https://docs.scala-lang.org/style/index.html)认真阅读，它将帮助我们写出更加具有Scala味道的代码。不仅可以提升自己代码的阅读与理解速度，也便于交流，当然对于编译器的编译后执行效率的提高还有待考证。

## 开始学习吧！

官方的推荐是从[Chisel Bootcamp](https://github.com/freechipsproject/chisel-bootcamp)开始来认识Chisel。本教程是基于Jupyter的，这里有[在线版本](https://mybinder.org/v2/gh/freechipsproject/chisel-bootcamp/master)，无需安装Jupyter。

还有一本[Cookbook](https://github.com/freechipsproject/chisel3/wiki/Cookbook)可供参考，此书写了一些用Chisel实现的电路的例子。

官方也贴心的为我们提供了一份Chisel的[CheatSheet](https://github.com/freechipsproject/chisel-cheatsheet/releases/latest/download/chisel_cheatsheet.pdf)。可以将此打印出来或者下载下来作为提示。

Chisel Bootcamp，使用的是Jupyter，这个工具有很多的好处，它可以边学习边查看代码，在当前的界面便可以查看到运行的结果。重要的是当前Jupyter已被很多人使用，所以还是很有必要去学习一下这个工具的。安装的时候推荐使用[Anaconda](https://www.anaconda.com)安装Jupyter，Anaconda为python套件，有很多东西都会帮忙安装好，**我们为了学习而不是去学习如何安装软件**，就直接采用Anaconda的方案吧。

安装时记得去查看距离自己最近的镜像站，有很好的加速作用。比如我所在的地方使用[ustc的镜像站](http://mirrors.ustc.edu.cn/)便可以有很好的加速效果。

安装好之后就可以在没有联网的情况下撒欢地学习啦，当然最重要的是有时官方网站速度很慢，等待加载的时间太痛苦了。


# Module 1: Introduction to Scala

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

包和导入：鼓励将命名更有意义，更有层次。

Scala是一门面向对象的编程语言：

类可以从特征继承。可以将特征想象成一个能让类继承多个类的途径，但是这个途径有所限制。

println中$符号后边可以跟表达式，像这样：${...}

匿名函数在Scala中同样使用很多

当一个函数的参数有默认值时，此函数被调用时，可以不给默认值传参数。

>**_初识篇完。_**

# Module 2.1: Your First Chisel Module

Motivation：
Chisel代表的是**C**onstructing **H**ardware **I**n a **S**cala **E**mbedded **L**anguage.

必要的设置：（先遵循官方的设置，有需求时再去修改）

```Scala
val path = System.getProperty("user.dir") + "/source/load-ivy.sc"
interp.load.module(ammonite.ops.Path(java.nio.file.FileSystems.getDefault().getPath(path)))
```

以下是在Scala中使用Chisel库的必要语句

```Scala
import chisel3._
import chisel3.util._
import chisel3.iotesters.{ChiselFlatSpec, Driver, PeekPokeTester}
```

## 接下来就是一个简单的Chisel写的模块了，会有很多不好理解的东西，但不影响学习，

```Scala
// Chisel Code: Declare a new module definition
class Passthrough extends Module {
  val io = IO(new Bundle {
    val in = Input(UInt(4.W))
    val out = Output(UInt(4.W))
  })
  io.out := io.in
}
```
Module是所有Chisel模块必须继承的类
```Scala 
val io = IO(...)
```
这里val io中的io是强制命名的。
```Scala 
new Bundle {
    val in = Input(...)
    val out = Output(...)
}
```
在IO(...)中进行端口的声明。
```Scala 
UInt(4.W)
```
UInt表示无符号整型
```Scala
io.out := io.in
```
:=是有方向的操作符

使用硬件形成语言的好处是可以用基语言Scala当做脚本语言去运行。如上述中的Chisel passthrough模块就可以用Scala去调用Chisel的编译器去生成相应的Verilog模块。这个过程称为**阐述**
虽然Chisel会尽力去保留你定义的模块名称，但有时会失败。

实例：一个模块生成器

```Scala
// Chisel Code, but pass in a parameter to set widths of ports
class PassthroughGenerator(width: Int) extends Module { 
  val io = IO(new Bundle {
    val in = Input(UInt(width.W))
    val out = Output(UInt(width.W))
  })
  io.out := io.in
}

// Let's now generate modules with different widths
println(getVerilog(new PassthroughGenerator(10)))
println(getVerilog(new PassthroughGenerator(20)))
```
这里使用了Scala语言的特性实现了一个Chisel模块生成器

## 测试你的硬件代码

Chisel有内置的测试器

实例：一个测试器
```Scala
// Scala Code: Calling Driver to instantiate Passthrough + PeekPokeTester and execute the test.
// Don't worry about understanding this code; it is very complicated Scala.
// Think of it more as boilerplate to run a Chisel test.
val testResult = Driver(() => new Passthrough()) {
  c => new PeekPokeTester(c) {
    poke(c.io.in, 0)     // Set our input to value 0
    expect(c.io.out, 0)  // Assert that the output correctly has 0
    poke(c.io.in, 1)     // Set our input to value 1
    expect(c.io.out, 1)  // Assert that the output correctly has 1
    poke(c.io.in, 2)     // Set our input to value 2
    expect(c.io.out, 2)  // Assert that the output correctly has 2
  }
}
assert(testResult)   // Scala Code: if testResult == false, will throw an error
println("SUCCESS!!") // Scala Code: if we get here, our tests passed!
```

上面发生了什么呢？
poke()给输入赋值，expect()检查是否得到的是预测到的值。
如果不想检查输出的值，则可以使用peek()来输入值。

## Looking at Generated Verilog/FIRRTL

查看Verilog/FIRRTL代码。

### 附录:

println()并不是最好的调试手段。因为println()函数是scala的函数，所以并不可以在电路仿真阶段使用，因为生成的代码是FIRRTL或者是Verilog。

## Module 2.2: Combinational Logic

Scala的强类型特性使得Chisel的数据类型在计算时要相互匹配，不然会有Err出现。

Example: Mux and Concatenation

```Scala
class MyOperatorsTwo extends Module {
  val io = IO(new Bundle {
    val in      = Input(UInt(4.W))
    val out_mux = Output(UInt(4.W))
    val out_cat = Output(UInt(4.W))
  })

  val s = true.B
  io.out_mux := Mux(s, 3.U, 0.U) // should return 3.U, since s is true
  io.out_cat := Cat(2.U, 1.U)    // concatenates 2 (b10) with 1 (b1) to give 5 (101)
}

println(getVerilog(new MyOperatorsTwo))
class MyOperatorsTwoTester(c: MyOperatorsTwo) extends PeekPokeTester(c) {
  expect(c.io.out_mux, 3)
  expect(c.io.out_cat, 5)
}
assert(Driver(() => new MyOperatorsTwo) {c => new MyOperatorsTwoTester(c)})
println("SUCCESS!!")
```

本章节多了几个练习，重要的是开始理解Chisel的框架。

## Module 2.3: Control Flow

最后有效语句
```Scala
class LastConnect extends Module {
  val io = IO(new Bundle {
    val in = Input(UInt(4.W))
    val out = Output(UInt(4.W))
  })
  io.out := 1.U
  io.out := 2.U
  io.out := 3.U
  io.out := 4.U
}

// Chisel Code: Declare a new tester for modules
class LastConnectTester(c: LastConnect) extends PeekPokeTester(c) {
  expect(c.io.out, 4)  // Assert that the output correctly has 4
}

//  Test LastConnect
val works = Driver(() => new LastConnect) {
  c => new LastConnectTester(c)
}
assert(works)        // Scala Code: if works == false, will throw an error
println("SUCCESS!!") // Scala Code: if we get here, our tests passed!
```

实际上运行到了最后一句语句，也就是io.out 被赋值了4。

## `when`, `elsewhen`, and `otherwise`

```Scala
when(someBooleanCondition) {
  // things to do when true
}.elsewhen(someOtherBooleanCondition) {
  // things to do on this condition
}.otherwise {
  // things to do if none of th boolean conditions are true
}
```
此结构无返回值。

## The Wire Construct

```Scala
/** Sort4 sorts its 4 inputs to its 4 outputs */
class Sort4 extends Module {
  val io = IO(new Bundle {
    val in0 = Input(UInt(16.W))
    val in1 = Input(UInt(16.W))
    val in2 = Input(UInt(16.W))
    val in3 = Input(UInt(16.W))
    val out0 = Output(UInt(16.W))
    val out1 = Output(UInt(16.W))
    val out2 = Output(UInt(16.W))
    val out3 = Output(UInt(16.W))
  })

  val row10 = Wire(UInt(16.W))
  val row11 = Wire(UInt(16.W))
  val row12 = Wire(UInt(16.W))
  val row13 = Wire(UInt(16.W))

  when(io.in0 < io.in1) {
    row10 := io.in0            // preserve first two elements
    row11 := io.in1
  }.otherwise {
    row10 := io.in1            // swap first two elements
    row11 := io.in0
  }
```

`Wire()`这里理解为连线。可出现在`:=`的左边或右边。

```Scala
// verify the all possible ordering of 4 numbers are sorted
class BetterSort4Tester(c: Sort4) extends PeekPokeTester(c) {
  List(1, 2, 3, 4).permutations.foreach { case i0 :: i1 :: i2 :: i3 :: Nil =>
    println(s"Sorting $i0 $i1 $i2 $i3")
    poke(c.io.in0, i0)
    poke(c.io.in1, i1)
    poke(c.io.in2, i2)
    poke(c.io.in3, i3)
    expect(c.io.out0, 1)
    expect(c.io.out1, 2)
    expect(c.io.out2, 3)
    expect(c.io.out3, 4)
  }
}
```

这里第一次出现了`List()`特性，知道是tester的特性便好，可使得测试方便。

Chisel提供了一个方便的状态机映射函数`Enum()`，如何使用呢？将枚举中的元素当做是UInt便好。

```Scala
when (io.state === idle) {
    when      (io.coffee) { io.nextState := coding } 
    .elsewhen (io.idea) { io.nextState := idle }
    .elsewhen (io.pressure) { io.nextState := writing }
  } .elsewhen (io.state === coding) {
    when      (io.coffee) { io.nextState := coding } 
    .elsewhen (io.idea || io.pressure) { io.nextState := writing }
  } .elsewhen (io.state === writing) {
    when      (io.coffee || io.idea) { io.nextState := writing }
    .elsewhen (io.pressure) { io.nextState := grad }
  }
```

## Module 2.4: Sequential Logic

没有状态的电路是没有意义的。没有状态的电路是没有意义的。没有状态的电路是没有意义的......

Chisel强大之处在于将设计参数化。

寄存器：

默认情况下，每个Chisel模块含有一个隐含的共享时钟，这会节省一些时间。

```Scala
class RegisterModule extends Module {
  val io = IO(new Bundle {
    val in  = Input(UInt(12.W))
    val out = Output(UInt(12.W))
  })
  
  val register = Reg(UInt(12.W))
  register := io.in + 1.U
  io.out := register
}

class RegisterModuleTester(c: RegisterModule) extends PeekPokeTester(c) {
  for (i <- 0 until 100) {
    poke(c.io.in, i)
    step(1)
    expect(c.io.out, i+1)
  }
}
assert(chisel3.iotesters.Driver(() => new RegisterModule) { c => new RegisterModuleTester(c) })
println("SUCCESS!!")
```

这里的寄存器由`Reg(tpe)`函数创建。调用函数`step(n)`使得时钟跳动n次。

注意：

- 时钟输入端并没有被显示声明，因为使用了隐含时钟。
- 寄存器在时钟上升沿被更新。

在Chisel中，这两者是不同的：`UInt`和`2.U`，前者是类型，后者是硬件节点。（hardware node）

`val myReg = Reg(UInt(2.W))` -->legal 

`val myReg = Reg(2.U)` -->illegal 

```Scala
class RegNextModule extends Module {
  val io = IO(new Bundle {
    val in  = Input(UInt(12.W))
    val out = Output(UInt(12.W))
  })
  
  // register bitwidth is inferred from io.out
  io.out := RegNext(io.in + 1.U)
}

class RegNextModuleTester(c: RegNextModule) extends PeekPokeTester(c) {
  for (i <- 0 until 100) {
    poke(c.io.in, i)
    step(1)
    expect(c.io.out, i+1)
  }
}
assert(chisel3.iotesters.Driver(() => new RegNextModule) { c => new RegNextModuleTester(c) })
println("SUCCESS!!")
```

这里的寄存器名称没有显示声明。
以上代码段实现的功能与前面的无异。

`val myReg = RegInit(UInt(12.W), 0.U)`
`val myReg = RegInit(0.U(12.W))`

生成有初始化值的寄存器。

一下为有初始化的模块的实例：

```Scala
class RegInitModule extends Module {
  val io = IO(new Bundle {
    val in  = Input(UInt(12.W))
    val out = Output(UInt(12.W))
  })
  
  val register = RegInit(0.U(12.W))
  register := io.in + 1.U
  io.out := register
}
println(getVerilog(new RegInitModule))
```

`PeekPokeTesters()`始终会在测试前调用重置，当然手动调用`reset(n)`也是可以的，这样会使得reset处于高电平n个周期。

寄存器的值在被运算时决定的是输出值。寄存器自身的数据类型不变。

`val reg: UInt = Reg(UInt(4.W))`

由此来改变寄存器的类型。

## Appendix: Explicit clock and reset

`withClock(){}`,`withReset(){}`和`withClockAndReset(){}`被用来重写时钟。

有一件需要注意的事情是`reset`为同步的，其类型为`Bool`型。在Chisel中时钟(`Clock`)有自己的类型。通过使用`asClock()`，`Bool`型值可以被转换为`Clock`型。

总结：

在下一节中我们会把学到的所有东西整合到一个例程中。

## Module 2.5: Putting it all Together: An FIR Filter

此章节中提供了两个例程。

在其中一个例程中我们初见了rocketchip的身影。

```Scala
...
import dspblocks._
import freechips.rocketchip.amba.axi4._
import freechips.rocketchip.amba.axi4stream._
import freechips.rocketchip.config._
import freechips.rocketchip.diplomacy._
import freechips.rocketchip.regmapper._
...
```
## Module 2.6: ChiselTest (formerly Testers2)

在此章节中我们见到了新的测试工具，ChiselTest(Testers2)。

```Scala
...
import chisel3._
import chisel3.util._
import chisel3.experimental._
import chisel3.experimental.BundleLiterals._
import chisel3.tester._
import chisel3.tester.RawTester.test
...
```

当然在此也可以看到Chisel也正是处于开发当中，不可避免的有命名混乱，文档不全的问题，留给risc-v团队的时间不多了。

## Module 3.1: Generators: Parameters

```Scala
class ParameterizedWidthAdder(in0Width: Int, in1Width: Int, sumWidth: Int) extends Module {
  require(in0Width >= 0)
  require(in1Width >= 0)
  require(sumWidth >= 0)
  val io = IO(new Bundle {
    val in0 = Input(UInt(in0Width.W))
    val in1 = Input(UInt(in1Width.W))
    val sum = Output(UInt(sumWidth.W))
  })
  // a +& b includes the carry, a + b does not
  io.sum := io.in0 +& io.in1
}

println(getVerilog(new ParameterizedWidthAdder(1, 4, 6)))
```

这里的`require(in0Width >= 0)`对参数进行检查。

## Module 3.2: Generators: Collections

这里的Collection指的是Scala中。

### Example: FIR 参考模型

```Scala
/**
  * A naive implementation of an FIR filter with an arbitrary number of taps.
  */
class ScalaFirFilter(taps: Seq[Int]) {
  var pseudoRegisters = List.fill(taps.length)(0)

  def poke(value: Int): Int = {
    pseudoRegisters = value :: pseudoRegisters.take(taps.length - 1)
    var accumulator = 0
    for(i <- taps.indices) {
      accumulator += taps(i) * pseudoRegisters(i)
    }
    accumulator
  }
}
```

`poke`函数中的accumulator作为函数的返回值。

```Scala
val filter = new ScalaFirFilter(Seq(1, 1, 1, 1))

var out = 0

out = filter.poke(1)
println(s"out = $out")
assert(out == 1)  // 1, 0, 0, 0

out = filter.poke(4)
assert(out == 5)  // 4, 1, 0, 0
println(s"out = $out")

out = filter.poke(3)
assert(out == 8)  // 3, 4, 1, 0
println(s"out = $out")

out = filter.poke(2)
assert(out == 10)  // 2, 3, 4, 1
println(s"out = $out")

out = filter.poke(7)
assert(out == 16)  // 7, 2, 3, 4
println(s"out = $out")

out = filter.poke(0)
assert(out == 12)  // 0, 7, 2, 3
println(s"out = $out")
```

上面是简单的一个测试，将我们前面设计好的类实例化后，进行简单的方法调用，来测试是否工作正常。

```Scala
val goldenModel = new ScalaFirFilter(Seq(1, 1, 1, 1))

Driver(() => new My4ElementFir(1, 1, 1, 1)) {
  c => new PeekPokeTester(c) {
    for(i <- 0 until 100) {
      val input = scala.util.Random.nextInt(8)

      val goldenModelResult = goldenModel.poke(input)

      poke(c.io.in, input)

      expect(c.io.out, goldenModelResult, s"i $i, input $input, gm $goldenModelResult, ${peek(c.io.out)}")

      step(1)
    }
  }
}
```

### Example: Parameterized FIR Generator

```Scala
class MyManyElementFir(consts: Seq[Int], bitWidth: Int) extends Module {
  val io = IO(new Bundle {
    val in = Input(UInt(bitWidth.W))
    val out = Output(UInt(bitWidth.W))
  })

  val regs = mutable.ArrayBuffer[UInt]()
  for(i <- 0 until consts.length) {
      if(i == 0) regs += io.in
      else       regs += RegNext(regs(i - 1), 0.U)
  }
  
  val muls = mutable.ArrayBuffer[UInt]()
  for(i <- 0 until consts.length) {
      muls += regs(i) * consts(i).U
  }

  val scan = mutable.ArrayBuffer[UInt]()
  for(i <- 0 until consts.length) {
      if(i == 0) scan += muls(i)
      else scan += muls(i) + scan(i - 1)
  }

  io.out := scan.last
}
```

其中的 `bitWith` 参数是为了控制滤波器可以处理的数据的长度。

`ArrayBuffer` 允许我们使用 `+=` 操作符来为其增加元素。

### Hardware Collections

### Example: Add run-time configurable taps to our FIR

```Scala
class MyManyDynamicElementVecFir(length: Int) extends Module {
  val io = IO(new Bundle {
    val in = Input(UInt(8.W))
    val out = Output(UInt(8.W))
    val consts = Input(Vec(length, UInt(8.W)))
  })

  // Reference solution
  val regs = RegInit(VecInit(Seq.fill(length - 1)(0.U(8.W))))
  for(i <- 0 until length - 1) {
      if(i == 0) regs(i) := io.in
      else       regs(i) := regs(i - 1)
  }
  
  val muls = Wire(Vec(length, UInt(8.W)))
  for(i <- 0 until length) {
      if(i == 0) muls(i) := io.in * io.consts(i)
      else       muls(i) := regs(i - 1) * io.consts(i)
  }

  val scan = Wire(Vec(length, UInt(8.W)))
  for(i <- 0 until length) {
      if(i == 0) scan(i) := muls(i)
      else scan(i) := muls(i) + scan(i - 1)
  }

  io.out := scan(length - 1)
}
```

上述的代码为我们的FIR生成器添加了一个名为 `consts` 的IO口，它使得我们可以在代电路生成后，也可以进行参数的修改。

最简单的说明就是我们先前用参数定制电路，使得一段代码可以因参数的不同产生不同的定制电路，而现在使用 `Vec()` 使得电路的在生成后，参数也可以由外部改变。

一般有两种情况下需要使用。

1. 需要一个IO口的集合
2. 需要用硬件索引来读取集合的值。

```Scala
class MyManyDynamicElementVecFir(length: Int) extends Module {
  val io = IO(new Bundle {
    val in = Input(UInt(8.W))
    val out = Output(UInt(8.W))
    val consts = Input(Vec(length, UInt(8.W)))
  })

  // Reference solution
  val regs = RegInit(VecInit(Seq.fill(length - 1)(0.U(8.W))))
  for(i <- 0 until length - 1) {
      if(i == 0) regs(i) := io.in
      else       regs(i) := regs(i - 1)
  }
  
  val muls = Wire(Vec(length, UInt(8.W)))
  for(i <- 0 until length) {
      if(i == 0) muls(i) := io.in * io.consts(i)
      else       muls(i) := regs(i - 1) * io.consts(i)
  }

  val scan = Wire(Vec(length, UInt(8.W)))
  for(i <- 0 until length) {
      if(i == 0) scan(i) := muls(i)
      else scan(i) := muls(i) + scan(i - 1)
  }

  io.out := scan(length - 1)
}
```

```Scala
val goldenModel = new ScalaFirFilter(Seq(1, 1, 1, 1))

Driver(() => new MyManyDynamicElementVecFir(4)) {
  c => new PeekPokeTester(c) {
    poke(c.io.consts(0), 1)//这里便使用了IO口集合索引
    poke(c.io.consts(1), 1)
    poke(c.io.consts(2), 1)
    poke(c.io.consts(3), 1)
    for(i <- 0 until 100) {
      val input = scala.util.Random.nextInt(8)

      val goldenModelResult = goldenModel.poke(input)

      poke(c.io.in, input)

      expect(c.io.out, goldenModelResult, s"i $i, input $input, gm $goldenModelResult, ${peek(c.io.out)}")

      step(1)
    }
  }
}
```

## Module 3 Interlude: Chisel Standard Library

这章节主要介绍了一些Chisel标准库里的东西，包括了一些就接口和常用的模块。




































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

**http://twitter.github.io/scala_school/** 一个scala学习资源

**http://twitter.github.io/effectivescala/index-cn.html** 一个scala学习资源

_programming in scala_ scala作者编写，引申出为什么要去看作者编写的东西
































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
