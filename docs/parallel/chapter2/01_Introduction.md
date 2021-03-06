# 介绍

目前，在软件应用中使用最广泛的并发编程范例是**多线程**。通常，一个应用有一个进程，分成多个独立的线程，并行运行、互相配合，执行不同类型的任务。

虽然这种模式存在一些缺点，有很多潜在的问题，但是多线程的应用依然非常广泛。

现在几乎所有的操作系统都支持多线程，几乎所有的编程语言都有相应的多线程机制，可以在应用中通过线程实现并发。

所以，使用多线程编程来实现并发的并用是个不错的选择。然而，多线程并不是唯一的选择，有不少其他的方案的表现比多线程好的多。

**线程是独立的处理流程**，可以和系统的其他线程并行或并发地执行。**多线程可以共享数据和资源**，利用所谓的共享内存空间。线程和进程的具体实现取决于你要运行的操作系统，但是总体来讲，我们可以说线程是包含在进程中的，**同一进程的多个不同的线程可以共享相同的资源**。相比而言，**进程之间不会共享资源**。

每一个线程基本上包含3个元素：**程序计数器，寄存器和栈**。与同一进程的其他线程共享的资源基本上包括**数据和系统资源**。每一个线程也有自己的运行状态，可以和其他线程同步，这点和进程一样。

线程的状态大体上可以分为 ready,running,blocked。线程的典型应用是应用软件的并行化——为了充分利用现代的多核处理器，使每个核心可以运行单个线程。相比于进程，使用线程的优势主要是性能。相比之下，在进程之间切换上下文要比在统一进程的多线程之间切换上下文要重的多。

多线程编程一般使用共享内容空间进行线程间的通讯。这就使管理内容空间成为多线程编程的重点和难点。
