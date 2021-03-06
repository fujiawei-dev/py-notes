# 并行世界的Python

作为一种解释型的语言，Python的速度并不算慢。如果对速度有很高的要求的话，可以选择用更快的语言实现，比如C或C++，然后用Python调用。

Python的一种常见应用场景是实现高级的逻辑。Python的解释器就是用C语言写的，即CPython。解释器将Python转换成一种中间语言，叫做Python字节码，类似于汇编语言，但是包含一些更高级的指令。当一个运行一个Python程序的时候，评估循环不断将Python字节码转换成机器码。解释型语言的好处是方便编程和调试，但是程序的运行速度慢。

其中的一种解决办法是，用C语言实现一些第三方的库，然后在Python中使用。

另一种方法是使用即时编译器来替换Cpython，例如PyPy，PyPy对代码生成和Python的运行速度做了优化。

但是在本书中，我们将研究第三种方法。Python提供了很多可以利用并行的模块，在后面的章节中，我们将着重讨论这些并行编程的模块。

接下来，本章将介绍两种基本概念：线程和进程，以及它们在Python中的表现。

