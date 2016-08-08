# The Go Programming Language

“Go 是一个开源的编程语言，它使得人们可以很容易的创建简洁、可靠、且高效的软件” ---摘自golang.org官网

```
2007年九月， Google的三个在计算机界举足轻重的人物，Robert Griesemer\(Java HotSpot虚拟机和Google V8 JavaScript engine的核心开发者之一\)、Ken Thompson\(Unix操作系统的联合开发者，B语言之父，C语言联合创造者\)、以及Rob Pike\(Plan9分布式操作系统作者，同Ken Thompson一起创造了UTF-8编码\) ， 开始构想Go语言的蓝图。2009年11月，Go的第一个版本发布。Go语言及其配套的一系列工具集的主要设计目标是要兼具足够的表达力和高效性。这里高效性值得是同时在编译效率和执行效率方面都高效，并且可以帮助程序员高效的写出可靠稳定的程序。

  Go猛一看长得比较像C语言。和C语言一样，Go面向的是专业的程序设计人员，玩的溜的老鸟可以利用Go在最小的开销代价下获得极大的性能。不过并不能说Go只是一个升级版的C。Go语言在设计的时候借鉴移植了不少其他语言的有点，同时也吸取其他语言的教训避开了一些容易导致复杂性和不可靠性的坑。Go语言在处理并发性问题方面有着过人的天资，并且在处理数据抽象和面向对象编程问题时灵活得令人发指。此外，Go语言拥有程序员们喜闻乐见的GC机制，可以自动管理内存
```

```
Go语言特别适合拿来做网络服务器，或是一些工具软件。不过作为一门通用编程语言，Go当然也可以拿来做一些其他领域的事情，比如图像处理，移动应用，或是机器学习等等。Go语言正在逐步取代一些弱类型的脚本语言，这得益于Go很好的平衡了表达性和安全性。Go语言通常可以获得比动态语言更高的执行速度，同时不会因为未知类型之类的错误导致程序挂掉。

Go是一个开源醒目，这意味着任何人只要感兴趣都可以自由的研究Go的编译器，标准库以及相关工具库代码。来自全世界的爱好者们活跃在社区里，一起为Go项目提交着各种各样的代码。Go语言可以运行于任何类Unix操作系统，包括Linux，FreeBSD，OpenBSD，Mac OS X，甚至还包括Plan9 系统，当然微软的Windows也在内。在这些操作系统上写的Go程序不需要修改就可以移植到其他操作系统上运行。 
```

本书主要目的在于帮助你尽快的开始上手Go语言，让你高效的掌握Go语言的特性，能够充分利用Go语言及其标准库的强大之处，写出清晰、地道、高效的程序。

Go语言的身世

和生物物种的进化类似，优秀的编程语言也会在一起杂交出新的编程语言。这些新语言不但兼具其祖先的优势，有时因为杂交优势还能获得出乎意料的惊喜。从语言演变的影响我们可以了解很多关于语言设计时的考虑，为什么语言要设计成这个样子，又到底是为了适应什么样的应用环境，等等等等。下图就展现了Go语言设计时所考虑到的早期其他编程语言的影响：

![](/assets/ancestors.png)

Go 有时候会被描述为“和C长得很像的语言”，或者说成是“21世纪的C语言”。 从C语言那里，Go继承了表达式语法，控制流语句，基本数据类型，call-by-value参数传递机制，指针，还有最重要的一个特性：也就是C语言所强调的，把程序编译成有效的机器编码，原生的同目标操作系统配合高效工作。

```
  不过Go的家庭族谱上还有其他的祖先。其中一个主要的分支来自于Niklaus Wirth创造的一系列语言。这一支的影响始于Pascal语言，然后从Modula-2语言引入了package包的概念，借鉴Oberon语言去掉了module interface稳健和module implementation
```

稳健的区别，而Oberon-2语言则影响了Go的package语法，import语法，和declaration语法， Object Oberon则提供了函数声明的语法格式参考。

```
  另一支Go的祖先则是来自于贝尔实验室的一系列小众编程语言。这一支祖先虽然小众，但是对Go的特性却影响重大，正是由于该分支对Go的影响，才使得Go能够明显的同其他现代编程语言区分开来。这一系列语言的原型都来自于1978年Tony Hoare关于并发编程原理的论文。Tony提出了communicating sequential processes\(CSP\)的概念。在CSP模型中，一个程序实际上是一堆并行进程的组合，进程间没有共享的状态，进程间相互通讯通过频道（channel）来进行。不过Hoare的CSP描述只是一个概念上的语言，重点是说明并行性的一些基础概念。这个时候的CSP并不是一个用来可以编写可执行程序的编程语言实现。
```

