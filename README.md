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
  另一支Go的祖先则是来自于贝尔实验室的一系列小众编程语言。这一支祖先虽然小众，但是对Go的特性却影响重大，正是由于该分支对Go的影响，才使得Go能够明显的同其他现代编程语言区分开来。这一系列语言的原型都来自于1978年Tony Hoare关于并发编程原理的论文。Tony提出了communicating sequential processes\(CSP\)的概念。在CSP模型中，一个程序实际上是一堆并行进程的组合，进程间没有共享的状态，进程间相互通讯通过频道（channel）来进行。不过Hoare的CSP描述只是一个概念上的语言，重点是说明并发性的一些基础概念。这个时候的CSP并不是一个用来可以编写可执行程序的编程语言实现。
```

Rob Pike和他的小伙伴们则开始动手进行一些实验性工作，把CSP理论落实到实际的编程语言上来。最早的实验产物被命名为Squeak（英文“吱吱声”之意，意为用于和老鼠交流的语言）。这玩儿真是用来和老鼠交流的——该语言主要用于处理鼠标和键盘的事件信息，用的是静态创建的channels。然后这伙人又捣鼓出来了升级版Newsqueak，加入了类似C语言的语句和表达式语法，以及类似Pascal语言的类型标注。Newsqueak已经是一个支持垃圾回收的纯功能性语言了，虽然用途仍然是管理键盘、鼠标，以及一些窗口消息事件。此时的Channels作为最高类型，可以支持动态创建，也可以以变量的形式存储。

Plan9操作系统在设计的时候也传承了这些成果，弄出来一个Alef语言。 Alef尝试把Newsqueak变成一种可视的系统编程语言，不过Alef去掉了GC的特性，这导致其在并发方面相当的挫。

Go的其他一些特性也分散的体现出一些不在族谱上的其他语言的特性。比如iota或多或少受到A语言的影响，而嵌套函数中的语义范围则来自于Scheme语言（大多数在Scheme之后诞生的编程语言都这么干）。当然也会有一些突变的新特性，比如Go创造性的slice概念，既提供了可以高效随机访问的动态数组，又不像传统的链表那样要考虑一些链接的复杂性。另外defer语句也是Go的首创。

Go语言计划

所有的编程语言都反映了其创造者的编程哲学，这其中通常会包含对现有编程语言的某些弱点的加强和改进。Go语言项目诞生之时Google正饱受与日俱增的系统复杂性困扰，而这并不只是Google一家会面临的问题，几乎所有的软件系统都会随着时间推移和功能增加，变得越来越无法维护。

正如Rob Pike指出的那样，复杂性是乘法属性的问题。修复系统中某一部分的问题会导致该部分慢慢变得更复杂，并且这一定会导致系统其他部分的复杂度增加。虽然从长期来看保持系统简洁对于一个好的软件来说至关重要，但是在日常开发的时候系统简洁性通常会让位于日益增加的新功能和新的配置属性，在要求出活儿越快越好的压力下经常会选择忽视系统的简洁性需求。

系统简洁性要想做好，就必须在项目开始之初就投入更多的精力来深刻理解待解决问题的本质，并且要求在整个项目生命周期中都严格遵守规则，认真区分哪些改进是好的，哪些改动是不好的，哪些改动是有害的会带来问题的。足够的精力投入下去，才能做到所谓好的改进，才能毫不妥协的实现Fred Brooks所说的设计上的“概念完整性”。糟糕的改动可达不到这一点，而有害的改动会牺牲系统简洁性来换取一时的方便。只有设计时充分考虑系统简洁性的需求，才可能做出一个可靠，安全得系统，才能保证系统演进的过程中保持一致性。

Go项目包括Go语言本身，相关工具集，标准库，还有最重要的一点：根生的简洁性思想。作为一门最新的高级编程语言，Go得益于不少前人淌出来的经验。在基本功能方面Go做的很好， Go拥有GC，软件包package，最高级函数，语义范围，系统调用接口，还有通常以UTF-8编码的不可变String。 但是相比其他一些语言来说Go的功能要少一些，而且并没有计划增多。比如说，Go没有隐式的数字转换，没有构造函数和析构函数，没有运算符重载，没有缺省的参数值，没有继承，没有泛型，没有异常，没有宏，没有函数标注，也没有线程本地存储。Go语言是成熟、稳定的，并且后向兼容，老版本的Go写的程序可以被新版编译器编译，也可以和新版标准库一起工作。

Go的类型系统对于避免绝大多数困扰程序员的粗心问题来说已经足够，不过比起其他可比的强类型语言来说要更简单一些。这在一个类型框架更广泛的架构中有时可能会导致一些孤立的无类型编程，Go程序员也无法像C++程序员和Haskell程序员那样深入的使用类型检查的证据来保证类型安全。不过在实战中Go给程序员提供了足够的安全性和运行时性能，这归功于一个相对强壮却并不复杂的类型系统。

Go鼓励使用现代计算机系统设计的一些先进理念，尤其是对于局部性原理的重要性。其內建的数据类型和大多数标准库的数据结构都是可以即开即用的，不需要显示的初始化或是隐式的构造函数，因此相对就少了一些隐藏的内存分配和写入。Go的聚合类型（Structs和arrays）直接保存数据元素，这就比使用非直接字段的语言消耗更少的存储和分配开销，也没有那么多的指针跳转。而且因为现代计算机是一个并行的机器系统，Go实现了基于CSP的并发机制。Go轻量级的线程（或者称为goroutines）的栈大小很小，以至于创建一个goroutine的开销小到实践中你可以同时创建上百万个goroutine一起跑。

Go标准库经常被描述为“自带电池”， 提供了干净的构件块，还有各种API： I\/O , 文本处理，图片，加密， 网络， 分布式应用，支持各种标准文件格式和协议。标准库和工具集通过广泛使用约定俗成，减少了配置和解释的需求，因此简化了程序逻辑，是的不同的Go程序之间在处理相似问题时更为相似，因此更容易被其他人所理解。用go tool编译的项目只需要使用文件名，标识名，还有一个可选的特殊注释就可以决定项目的所有库，可执行文件，测试，跑分，示例，平台特殊的变量，还有文档。Go源码本身包含了编译规范。

本书结构：

我们假定读者已经使用过一种或多种编程语言码过代码，比如C，C++，Java等编译性语言，或是解释型语言比如Python，Ruby，JavaScript等，所以我们不会像对待全新菜鸟那样掰碎了一口一口喂。其实语法看上去是相近的，变量、常量，表达式，控制流，还有函数的概念也都差不多。

第一章是一个基本概念的引导。这都是日常工作中经常用的东西，比如读写文件，格式化文本，创建图片，在server和client之间通信等等。

第二章描述了一个Go程序的结构组件——声明，变量，新类型，包，还有文件， 作用范围。第三章讨论numbers, booleans, strings, 还有常量，并且解释了如何用Unicode编码。第四章描述了复合类型，也就是用简单基本类型拼出来的新类型，比如数组，map，struct，还有slice，也就是Go的动态链表。第五章讨论了函数，还有错误处理，panic，recover，还有defer语句。

第一到第五章都是基础概念，这些都是主流编程语言都有的东西。Go的语法和风格有时候会和其他语言有些不同，不过大多数程序员都可以快速上手。剩下的章节集中讨论Go语言和其他语言不太一样的地方： 函数，接口，并发，包，测试，还有反射。

Go的面向对象编程方法也很特别。在Go的世界里没有类继承，事实上也没有class的概念。复杂的对象行为是通过简单行为的组合来完成的，木有继承。函数方法可以同任何用户定义的类型相关联，并不限于Struct，另外具体类型和抽象类型（接口）的关系是隐含的，所以一个具体类型可能会对应一个设计者在编程时并不知道的接口。在第六章第七章中我们进一步讨论函数。

第八章讲的是Go的并发，这是基于通信序列过程模型\(CSP\)实现的。有两个重要的组成部分： goroutines和channels。第九章解释了传统的基于共享变量的并发集中的各个方面。

第十章描述了包，也就是管理libraries的机制。这一章里也会说一下如何搞笑的使用go tool， 包括在编译，测试，跑分，格式化代码，文档以及其他任务。这都是一个命令搞定的。

第11章重点处理测试问题。这方面Go有个轻量级的方案，是一个可圈可点的亮点。得益于简洁的标准库和工具集，Go没有过于抽象的测试架构。测试库提供了一个基础架构，在其之上可以根据实际项目需要构建更加复杂的抽象。

第12章讨论了反射。就是程序在运行时检查自己的表述的能力。反射是一个有力的工具，不过用的时候要小心。这一章通过介绍一些Go的标准库是如何通过反射来实现的，以求解释清楚如何正确的权衡反射的应用。第13章解释了使用不安全的包绕过Go的类型系统进行底层编程的血淋淋的细节，也说明了什么时候这么做是合适的。

每一章都有一些练习来帮助检验对本章的理解是否深刻，同时这些练习也是对正文内容很好的补充和扩展。

几乎所有的详细代码都可以在gopl.io的git库中下载。每个例子都标识有包导入路径可以很方便的通过go get命令获取，编译，安装。你需要选择一个目录作为你的Go workspace， 然后把GOPATH环境变量指到该目录。如果需要也可以用go tool来创建这个目录，例如：



