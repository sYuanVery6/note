## Base

### Java

------

#### 语言基础

1. `环境` **JDK和JRE区别？**

> * JDK：Java Development Kit的简称，java开发工具包，提供了java的开发环境和运行环境
> * JRE：Java Runtime Environment的简称，java的运行环境，为java的运行提供了所需环境
>
> 具体来说JDK包含JRE，同时还包含了编译Java源码的编译器javac以及一些java程序调试和分析的工具。
>
> ##### 实际案例
>
> 1. 503数管项目中，实现客户端选择本地文件上传到服务器上的程序，在部署过程中，就是在每个客户端部署了一个JRE和Tomcat

2. `内存地址` `对象引用` == 和equals的区别是什么？

> * == 解读
>   * 基本类型：比较的是值是否相同
>   * 引用类型：比较的是引用地址是否相同
> * equals 解读
>   * equals是Object的内置方法，本质上就是 == ，类可以重写equals的equals方法，来自定义两个对象的比较

3. `对象引用` `hashcode` **两个对象的hashCode()相同，则equals也一定为true，对吗？**

> 不对，两个对象的hashCode()相同，equals不一定为true
>
> ##### 个人理解
>
> 从Object角度看，JVM每new一个Object，他都会将这个Object丢到一个Hash表中去，这样的话，下次做Object的比较或者取这个对象的时候，它会根据对象的hashCode再从Hash表取这个对象。这样做的目的是提高取对象的效率
>
> 改写equals时总是要改写hashCode

4. `java关键字` **final在java中有什么作用？**

> * final修饰的类叫最终类，该类不可被继承
> * final修饰的方法不能被重写
> * final修饰的变量叫常量，常量必须被初始化，初始化之后值就不能被修改
> * 被final修饰的常量，在编译阶段会存入常量池中
> * 被final修饰的方法，JVM会尝试将其内联，以提高运行效率

5. `java类型` `String` String属于基础的数据类型吗？

> String 不属于基础类型，String是java封装的字符串类型，底层是一个不可变char类型的数组

6. `java类型` `String` **String常用方法？**

> * equals：比较内容
> * length：获取长度
> * indexOf(String str):获取str在字符串对象中第一次出现的索引
> * subString
> * trim：去除两端空格
> * split：通过某个字符分隔，返回一个分割后的字符串数组
> * 大小写转换、开始结尾判断、判空...

7. `java类型` `String` **java中操作字符串都有哪些类？它们之间有什么区别？**

> 操作字符串的类有String、StringBuilder、StringBuffer
>
> 区别：
>
> * String和StringBuffer、StringBuilder的区别在于String声明的对象时不可变的对象，每次操作都会生成一个新的String对象，然后将指针指向新的String对象，而StringBuilder和StringBuilder可以在原有对象的基础上进行操作，所以在经常改变字符串内容的情况下最高不要使用String。
> * StringBuffer和StringBuilder最大的区别在于，StringBuffer是线程安全的，而StringBuilder是非线程安全的，所以StringBuilder性能高于StringBuilder。

8. `java类型` `String` **String str = "i"与String str = new String("i")一样吗？**

> 不一样，因为内存的分配方式不一样。String str = "i"的方式，java虚拟机会将其分配带常量池中；而通过new声明则会被分到堆内存中。

9.  `抽象类` **抽象类必须要有抽象方法吗?**

> 不需要，抽象类不一定非要有抽象方法

10. `抽象类` **普通类和抽象类有哪些区别？**

> * 普通类不能包含抽象方法，抽象类可以包含抽象方法，抽象方法只需申明，无需实现
> * 抽象类不能直接实例化，普通类可以直接实例化
> * 抽象方法不能生命为静态、不能用private修饰，不能用final修饰

[^date]: 2021-06-07

11. `接口` `抽象类` **接口和抽象类有什么区别？**

> * 实现：子类通过extends来继承抽象类，接口必须使用implements来实现接口
> * 构造函数：抽象类可以有构造函数；接口不能有
> * main方法：抽象类可以有main方法，并且能运行，接口不能有main方法
> * 实现数量：子类只能继承一个抽象类，却可以实现多个接口
> * 访问修饰符：接口中的方法默认使用public修饰；抽象类中的方法可以是任意访问修饰符

12. `IO流` **java中IO流分为几种？**

> 按照功能分：
>
> * 输入流 input
> * 输出流 output
>
> 按照类型分：
>
> * 字节流
> * 字符流
>
> 字节流和字符流的区别：字节流按8位传输以字节为单位输入输出数据，字符流按16位传输以字符为单位输入输出数据
>
> ##### 实际案例
>
> * 在面试过程中出现的频率小，但是在实际项目中却经常用。
> * 访问外部接口下载文件（附件的数据提取功能，网络IO）
> * 卫星数据存档（503数管）
> * 接口文件的传递（503调度，各个模块之间的接口通信）

13. `IO流` **BIO、NIO、AIO有什么区别？**

> * BIO：Block IO 同步阻塞式IO，就是我们平常使用的传统IO，它的特点是模式简单实用方便，并发处理能力低
> * NIO：New IO同步非阻塞IO，是传统IO的升级，客户端和服务端通过Channel（通道）通讯，实现了多路复用
> * AIO：Asynchronous IO是NIO的升级，也叫NIO2，实现了异步非阻塞IO，异步IO的操作基于事件和回调机制
>
> ##### TODO：了解NIO实现原理，待补充

14. `文件` **File的常用方法有哪些？**

> * exists：是否存在
> * delete：删除
> * mkdir：创建文件夹
> * 获取文件名，文件路径等...

15. `内部类` **内部类有什么用？**

> 内部类可以有多个实例，每个实例都有自己的状态信息，并且与其他外围对象的信息相互独立。在当儿外围类当中，可以让多个内部类以不同的方式实现同一接口，或者继承同一个类。创建内部类对象的时刻不依赖与外部类对象的创建。内部类并没有令人疑惑的"is-a"关系，他就像一个独立的实体。此外，内部类提供了更好的封装，除了该外围类，其他类都不能访问。
>
> ##### 实际应用
>
> * 单例模式可以通过静态内部类的方式实现线程安全
> * JDK源码中的HashMap的Node类（源码中经常出现）

16. `克隆`  **clone()是哪个类的方法？**

> clone是Object自带的七个方法之一，是native方法，对象想要重写克隆方法需实现Cloneable接口（只是一个标志性接口）

17. `克隆` `设计模式` `原型模式` `对象拷贝` **深拷贝和浅拷贝**

> * 浅拷贝：被复制对象的所有变量都含有与原来对象相同的值，而所有的对其他对象的引用仍然指向原来的对象。换言之，浅拷贝仅仅复制所考虑的对象，而不是复制他所引用的对象。
> * 深拷贝：被复制对象的所有变量都含有与原来的对象相同的值，而那些引用其他对象的变量将指向被复制过的新对象，而不再是原有的那些被引用的对象，换言之，深拷贝吧要复制的对象所引用的对象都复制一遍

18. `java关键字` **static都有哪些用法？**

> * 修饰静态变量
> * 修饰静态方法
> * 修饰静态代码块，多用于初始化操作
> * 修饰内部类

19. `继承` **父类的静态方法能否被子类重写？**

> 不能，重写只适用于实例方法，不能用于静态方法，而子类当中含有和父类相同签名的静态方法，我们一般称之为隐藏

20. `对象` **什么是不可变对象？好处是什么?**

> 不可变对象指对象一旦被创建，状态就不能再改变，任何修改都会创建一个新的对象，如String、Integer及其他包装类，不可变对象最大的好处是线程安全。

21. `静态` `语法特性` 静态变量和实例变量的区别？

> 静态变量存储在方法区，属于类所有。实例变量存储在堆当中，其引用存在当前线程栈。需要注意的是从JDK1.8开始用于实现方法区的PermSpace被MetaSpace取代了。

22. `对象` **java创建对象的几种方式**

> * 通过new关键字调用构造方法进行创建
> * 通过反射进行创建
> * 采用clone机制
> * 通过序列化创建

23. `面向对象` **面向对象的三个特征？**

> * 继承：extends
> * 封装：访问修饰符
> * 多态：implments

24. `面向对象` `多态` **JVM是如何实现多态的**

> 动态绑定技术（dynamic binding），执行期间判断所引用对象的实际类型，根据实际类型调用对应的方法

25. `面向对象` `接口` **接口的意义**

> * 规范
> * 扩展
> * 回调

26. `抽象类` **抽象类的意义**

> * 为其他子类提供一个公共的类型
> * 封装子类中重复定义的内容
> * 定义抽象方法，子类虽然有不同的实现，但是定义是一致的

27. `面向对象` `多态` **Java多态**

> 对象的多态：父类或者接口的引用指向其子类的对象
>
> 实质：多态实际上是自动类型提升，即向上转型。向上转型为了提高提高扩展性并限制特有方法，向下转型为了使用特定方法；对于转型都是子类对象做着类型的变化

28. `面向对象` `多态` `方法重写` `方法重载`  **方法的重写和重载**

> 区别：
>
> | 区别点   | 重载方法OverLoading | 重写方法OverRiding                               |
> | -------- | ------------------- | ------------------------------------------------ |
> | 参数列表 | 必须修改            | 不能修改                                         |
> | 返回类型 | 可以修改            | 不能修改                                         |
> | 异常     | 可以修改            | 可以减少或者删除，但是不能抛出新的或者更广的异常 |
> | 访问     | 可以修改            | 一定不能做更严格的限制，可以降低限制             |
> | 使用范围 | 在一个类中          | 在子类中                                         |
> | 多态类别 | 编译时多态          | 运行时多态                                       |
>
> ##### 编译时多态与运行时多态
>
> * 编译时多态：发生在方法重载的时候，在类加载的时候会加载两个方法的版本。这个过程是在编译期就是确定的，这个时候我们通过不同参数调用相同函数名的时候就会返回不同的结果。
> * 运行时多态发生在继承的时候，父类有个方法，子类重写了父类的方法。这时候由父类对象指向子类的实例的时候，就会调用子类的方法。

### Java Thread

------

1. `并发` `并行` **并发和并行有什么区别？**

> * 并行是指两个或者多个事件在同一时刻发生；而并发是指两个或多个事件在同一时间间隔发生
> * 并行是在不同实体上的多个事件，并发是在同一实体上的多个事件
>
> 所以并发编程的目标是充分的利用处理器的每一个核，以达到最高的处理性能

2. `线程` `进程` **线程和进程的区别？**

> 简而言之，进程是程序运行和资源分配的基本单位，一个程序至少有一个进程。一个进程至少有一个线程。进程在执行过程中拥有独立的内存单元，而多个线程贡献内存资源，减少切换次数，从而效率更高。线程是进程的一个实体，是cpu调度和分派的基本单位，是比程序更小的能独立运行的基本单位。同一进程中的多个线程之间可以并发执行。

3. `守护线程` **守护线程是什么？**

> 守护线程（Daemon Thread），是个服务线程，准确地来说就是服务其他的线程

4. `线程` `线程创建` **创建线程有哪几种方式？**

> 1. 继承Thread类，重写run方法（因为java的单继承机制，不推荐）
> 2. 实现Runnable接口，实现run方法
> 3. 实现Callable接口，实现call方法，通过FutureTask创建并启动新线程
> 4. 通过线程池创建线程

5. `Runnable` `Callable` **Runnable和Callable二者区别？**

> * Runnable的线程执行体返回值是void，而Callable的线程执行体是有返回值的，和Future、FutureTask配合可以用来获取异步执行的结果
> * Callable接口call方法允许将异常向上抛出，也可以直接在内部处理，而Runnable接口实现类中的run方法的异常必须在内部处理掉，不能向上抛出

6. `线程状态`**线程有哪些状态？**

> ```java
> public enum State {
>         /**
>          * 创建状态，尚未启动的线程的线程状态
>          */
>         NEW,
> 
>         /**
>          * 运行/就绪状态，一个处于运行状态的线程正在JVM中执行；也有可能正在等待获取CPU分配资源
>          */
>         RUNNABLE,
> 
>         /**
>          * 阻塞状态，等待锁资源而阻塞的线程状态，处于阻塞状态的线程正在等待其他线程释放锁，从而获取资源。或者在调用Object.wait()之后进入一个同步的方法/块
>          */
>         BLOCKED,
> 
>         /**
>          * 等待状态，由于调用了以下方法之一，线程处于等待状态：
>          * Object.wait with no timeout
> 		 * Thread.join with no timeout
>          * LockSupport.park
>          * 处于等待状态的线程正在等待另一个线程执行特定的操作。例如，在一个对象上调用了Object.wait()的线程正在等待另一个线程在该对象上调用Object.notify()或者Object.notifyall()。调用Thread.join()的线程正在等待指定线程终止。
>          */
>         WAITING,
> 
>         /**
>          * 定时等待状态，由于调用了下列方法中的一个，并且指定了正在等待的时间，线程处于定时等待状态：
>          * Thread.sleep
>          * Object.wait with timeout
>          * Thread.join with timeout
>          * LockSupport.parkNanos
>          * LockSupport.parkUntil
>          */
>         TIMED_WAITING,
> 
>     	/**
>     	 * 终止状态，线程已经执行完
>     	 */
>         TERMINATED;
> ```
>
> ![线程状态转换图](https://img-blog.csdn.net/20180512102914671?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoaTJodWFuZw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

7. `线程方法` **sleep()和wait()有什么区别？**

> * slepp():方法时线程类（Thread）的静态方法，让线程进入睡眠状态，让出执行机会给其他线程，等到休眠时间结束后，线程进入就绪状态和其他线程一起竞争CPU的执行时间。因为sleep()是静态方法，他不能改变对象的锁，当一个Synchronized块中调用了sleep()方法，线程进入休眠，但是对象的锁还没有释放，其他线程依然无法访问这个对象
> * wait():wait是Object类的方法，当一个线程执行到wait方法时，它就进入到一个和该对象相关的线程池，同时释放对象的锁，使得其他线程能够访问，可以通过notifyall，notify方法来唤醒等待的线程

8. `线程方法` **notify()和notifyall()有什么区别？**

> * 如果线程调用了对象的wait方法，那么线程便会处于该对象的等待池中，等待池中的线程就不会竞争该对象的锁
> * 当有线程调用了对象的notifyAll方法（唤醒所有wait线程）或notify方法（只随机唤醒一个wait线程），被唤醒的线程会进入该对象的锁池中，锁池中的线程回去竞争该对象锁。
> * 优先级高的线程竞争到对象锁的概率大，假若某线程没有竞争到该对象锁，他还会留在锁池中，唯有在次调用wait方法，它才会重新回到等待池中。而竞争到对象锁的线程则继续往下执行，知道执行完synchronized代码块，他会释放掉该对象锁，这时锁池中的线程会继续竞争该对象锁。

9. `线程方法` **线程的run()和start()有什么区别？**

> 每个线程都是通过某个特定的Thread对象对应的方法run()来完成其操作，方法run()称为线程体。通过调用Thread类的start()方法来启动一个线程。
>
> * start()方法来启动一个线程，真正实现了多线程运行。这时无需等待run方法体代码执行完毕，可以直接继续执行下面的代码；这时此线程是处于就绪状态，并没有运行。然后通过此Thread类调用方法run()来完成其运行状态，这里方法run()称为线程体，它包含了要执行的这个线程内容，run方法运行结束，此线程终止。然后CPU在调度其他线程。
> * run()方法是在本线程里的，只是线程里的一个函数，而不是多线程的。如果直接调用run()，其实就相当于是调用了一个函数而已，直接调用run方法必须等待run()方法执行完毕才能执行下面的代码，所以执行路径还是只有一条，根本就没有线程的特征，所以在多线程执行时要使用start方法而不是run方法

10. `线程池` **创建线程池的方式有几种？**

> * 通过线程池工具类Executors创建特定参数的线程池，不推荐使用，可能会引起OOM，阻塞队列接近无限
> * 通过new ThreadPoolExecutor(...)自定义创建
>
> ##### 线程池参数详解：
>
> ```java
> public ThreadPoolExecutor(int corePoolSize,
>                               int maximumPoolSize,
>                               long keepAliveTime,
>                               TimeUnit unit,
>                               BlockingQueue<Runnable> workQueue,
>                               ThreadFactory threadFactory,
>                               RejectedExecutionHandler handler)
> ```
>
> * corePoolSize:线程池中的常驻核心线程数，线程中的线程数目达到corePoolSize后，就会把任务放到缓存队列。（银行的受理窗口数）
> * maximumPoolSize:线程池的最大线程数，此值必须大于等于1（容量）（最大窗口上限，加班窗口）
> * keepAliveTime:多余的空闲线程的存活时间，当前线程池数量超过corePoolSize时，当空闲时间达到keepAliveTime时多余的空间线程被销毁，直到只剩下corePoolSize个线程为止
> * unit:keepAliveTime的时间单位
> * workQueue:阻塞队列，类似于银行里面的候客区，存放已经被提交但是未被执行的任务
> * threadFactory:表示生成线程池中工作线程的线程工厂，用于创建线程，一般用默认即可（银行网点的logo/员工的制服，胸卡...）
> * handler:拒绝策略，表示当队列满并且工作线程大于等于线程池最大线程数时，采用的策略
>
> ##### 使用线程池的优势
>
> 线程池主要控制运行的线程数量，处理过程中将任务放入队列，然后在线程创建后启动这些任务，如果线程数量超过了最大数量，超出数量的线程排队等候其他线程执行完毕，再从队列中取出任务再执行。
>
> 特点：线程用；控制最大并发数；管理线程
>
> ##### 线程池合理配置参数
>
> CPU密集型：CPU核数+1
>
> IO密集型：并不是一直执行任务，尽可能多配置线程，CPU核数*2

11. `线程安全` **Java程序中怎么保证多线程的运行安全？**

> * 原子性：提供互斥访问，同一时刻只能有一个线程对数据进行操作（atomic,synchronized）
> * 可见性：一个线程对主内存的修改可以及时地被其他线程看到（synchronized,volatile）
> * 有序性：一个线程观察其他线程中的指令执行顺序，由于指令重排序，该观察结果一般杂乱无序（happens-before原则）

12. `锁` `锁升级` **多线程锁的升级原理是什么？**

> 传统的synchronized是重量级锁，为了减少获得锁和释放锁带来的性能损耗，在javaSE1.6引入了“偏向锁”和“轻量级锁”的概念
>
> ##### 升级过程
>
> * 偏向锁：大多数情况下，锁不仅不存在多线程竞争，而且总是由同一线程多次获得，为了让线程获得锁的代价更低而引入了偏向锁。当一个线程访问同步代码块的时候，会在对象头和栈帧中的锁记录存储该线程的线程id（偏向线程id），以后该线程在进入和退出同步代码块时，不需要进行CAS操作来加锁和解锁，只是简单的测试一下对象头的MarkWord里是否存储着指向当前线程的偏向锁
> * 轻量级锁：如果有第二个线程与获取偏向锁的线程来竞争同一资源，偏向锁就会升级为轻量级锁。此时两个线程会在线程的栈帧中创建用于存储锁记录的空间(ThreadPool)，并将对象头MarkWord赋值到锁记录中。然后线程尝试使用CAS将对象头中的MarkWord替换为指向锁记录的指针。如果成功，当前线程获得锁，如果失败，当前线程便尝试通过自旋来获取锁。轻量级锁的解锁是，会使用原子的CAS操作将Displaced Mark Word替换回对象头，如果成功，表示没有竞争发生，如果失败，表示当前锁存在竞争，锁就会膨胀成重量级锁
> * 重量级锁：轻量级锁执行在用户态，重量级锁执行在内核态，需要向CPU申请。每一个重量级锁下有一个队列，里面存放着被阻塞等待获取锁的线程，阻塞状态不消耗资源。
>
> ![img](https://i0.hdslb.com/bfs/article/ec9213ac3c1342d584fd12d09fda7afc52afb45f.jpg@1256w_698h_progressive.webp)

13. `锁` `CAS` **CAS的理解**

> * 基本概念
>
> CAS全称Conmpare And Swap；比较并且交换。是计算机科学中用来实现多线程同步的原子指令。
>
> * 运行原理
>
> 当一个线程对主存中的某个变量A（值为0）进行计算时，先从主存中拿到这个变量A，然后在该线程的私有内存中对变量A进行计算，计算之后，再去主存中拿到变量A，将之前拿到的变量A的值与第二次拿到的变量A的值进行计算。如果前后两次拿到的值相等，则将计算后的变量A的值更新到主存中的变量A中。如果不相等，则将新拿到的变量A重新进行计算。
>
> ![CAS运行机制](C:\Users\sYuan\AppData\Local\Temp\CAS运行机制.png)
>
> * ABA问题
>
> CAS可以有效的提示并发效率（不用锁），但是也会引起ABA问题。
>
> ABA问题：假设有两个线程T1和T2都要操作主存中的变量X，变量X的值为A，此时T1先获取到变量X，当T1在自己的私有内存中计算变量X值时，T2获取到变量X后将X的值更新为A并写回主存。然后T1将变量X的值计算成了B，此时T1通过CAS比较当前主存中变量X的值，但是此时主存中的变量X的值已经不是之前的A了，是一个新的A。T1比较后会将变量X（B）重新更新到主存中。
>
> 如何解决？在对象中额外增加一个变量（例如版本号）来标志对象是否有过变更。[乐观锁]

14. `java关键字` `锁` `线程安全` Synchronized和volatile关键字及线程安全

> ##### 线程安全
>
> 是指当多个线程同时读写一个共享资源并且没有任何同步措施时，导致出现脏数据或者不可预见的结果的问题
>
> ##### 共享变量的内存可见性
>
> java内存模型规定，将所有变量都放在主内存中，当线程使用变量时会把主存里面的变量复制到自己的工作空间（工作内存）中，线程读写变量时操作的是自己工作内存中的变量，操作完后再将变量值更新到主内存中。
>
> 内存不可见问题：当两个线程操作同一共享变量时，都会将变量放在自己的工作内存中处理，在将数据更新到主存中，会导致其他线程对新的数据不可见的问题。即内存不可见问题。
>
> 解决内存不可见问题：volatile关键字。
>
> ##### synchronized关键字
>
> synchronized是java提供的一种原子性内置锁，java的每个对象都可以把它当做一个同步锁来使用，这些java内置的使用者看不到的锁被称为内置锁，也叫监视器锁。拿到内部锁的线程会正常退出同步代码块，或者抛出异常后或者在同步代码快内调用了该内置锁资源的wait系方法时释放该锁资源。
>
> ##### synchronized缺点
>
> 由于java的线程是与操作系统的原生线程一一对应的，所以当阻塞一个线程时，需要从用户态切换到内核态执行阻塞操作，这是很耗时的操作，而synchronized的使用就会导致上下文去诶换。并且带来线程调度开销
>
> ##### synchronized内存语义
>
> synchronized的内存语义可以解决共享变量的内存可见性问题。进入synchronized块的内存语义是把synchronized块内使用到的变量从线程的工作内存中清除，这样在synchronized块内使用到该变量时就不会从线程的工作内存中获取，而是从主内存中获取。退出synchronized块的内存语义是把在synchronized块内对共享变量的修改刷新到主内存。其实这也是加锁和释放锁的语义
>
> ##### synchronized的实现过程
>
> 一段同步代码块在编译成字节码后，synchronized对应了monitor enter(开启监视器)和monitor exit(退出监视器)两条字节码指令，然后在jvm执行的过程中自动进行锁升级
>
> monitor enter 和monitor exit和机器指令lock comxchg相关
>
> ##### synchronized的几种实现方式
>
> ```java
> public class SynchronizedTest {
> 
>     private Object object;
> 
>     public static synchronized void staticLock(){
>         //给SynchronizedTest.Class上锁
>     }
> 
>     public static void staticLock2(){
>         synchronized (SynchronizedTest.class){
>             //给SynchronizedTest.Class上锁
>         }
>     }
> 
>     public synchronized void objectLock(){
>         //给该对象this上锁
>     }
> 
>     public void objectLock2(){
>         synchronized (this){
>             //给该对象this上锁
>         }
>     }
> 
>     public void objectLock3(){
>         synchronized (object){
>             //给变量object上锁，只能修饰引用类型
>         }
>     }
> 
> }
> ```
>
> ##### volatile关键字
>
> 使用锁的方式解决内存可见性问题太笨重。为了解决内存可见性问题，java还提供了一种弱形式的同步，那就是volatile关键字。这个关键字可以确保对一个变量的更新对其他线程马上可见。当一个变量被声明为volatile时，线程在写入变量时不会把值缓存在寄存器或者其他地方，而是会把值刷新回主内存。当其他线程读取该共享变量时，会从主内存获取最新值，而不是从当前的工作内存中获取
>
> ##### volatile内存语义
>
> 与synchronized有相似之处，写入volatile变量时等价于退出synchronized块的操作，而读取volatile变量时等价于进入synchronized的操作。并非在所有情况下synchronized与volatile是等价的，volatile只提供了内存可见性，并没有保证操作的原子性。
>
> > tips：原子性是指在一系列操作时，这些操作要么全部执行，要么全部不执行，不存在只执行一部分的情况，如果不能保证操作的原子性，name就会出现线程安全问题。

15. `锁` `死锁` 什么是死锁？怎样避免死锁？

> ##### 死锁的概念
>
> 死锁是指两个或者两个以上的进程在执行过程中，由于竞争资源或者由于彼此通信而造成的一种阻塞现象，若无外力作用，他们都将无法推进下去。
>
> ##### 死锁的必要条件
>
> * 互斥条件：进程对所分配的资源不允许其他进程进行访问。
> * 请求和保持条件：进程在获取一定资源后，又向其他资源发出请求，但是资源可能被其他进程持有，而处于等待
> * 不可剥夺条件：进程已经获得的资源在未完成使用之前，不可被剥夺，只能在使用完后自己释放
> * 环路等待条件：是指进程发生死锁后，若干进程之间经常一种头尾相接的循环等待资源关系
>
> ##### 死锁的java代码实现
>
> ```java
> package com.ayuan.daliy.therad;
> 
> /**
>  * @author ayuan
>  * @Title:
>  * @Package
>  * @Description:
>  * @date 2021/6/15  20:51
>  */
> public class DeadThread {
> 
>     private Object o1 = new Object();
> 
>     private Object o2 = new Object();
> 
>     private Runnable r1 = new Runnable() {
>         @Override
>         public void run() {
>             synchronized (o1){
>                 try {
>                     // 给r2预留获取o2对象的时间
>                     Thread.sleep(1000);
>                 } catch (InterruptedException e) {
>                     e.printStackTrace();
>                 }
>                 synchronized (o2){
>                     System.out.println("i am r1 ...");
>                 }
>             }
>         }
>     };
> 
>     private Runnable r2 = new Runnable() {
>         @Override
>         public void run() {
>             synchronized (o2){
>                 try {
>                     // 给r1预留获取o1对象的时间
>                     Thread.sleep(2000);
>                 } catch (InterruptedException e) {
>                     e.printStackTrace();
>                 }
>                 synchronized (o1){
>                     System.out.println("i am r2 ...");
>                 }
>             }
>         }
>     };
> 
>     private void dead(){
>         Thread t1 = new Thread(r1);
>         Thread t2 = new Thread(r2);
> 
>         t1.start();
>         t2.start();
>     }
> 
>     public static void main(String[] args) {
>         DeadThread deadThread = new DeadThread();
>         deadThread.dead();
>     }
>     
> }
> ```
>
> ##### 检查死锁及解决方案
>
> * 通过jps -l查看当前计算机上执行的java程序进程pid
>
> ```bash
> PS C:\Users\sYuan> jps -l
> 20640 org.jetbrains.jps.cmdline.Launcher
> 2720
> 3316 sun.tools.jps.Jps
> 5832 com.ayuan.daliy.therad.DeadThread
> 6604 org.jetbrains.idea.maven.server.RemoteMavenServer
> ```
>
> * 通过jstack [pid]查看该进程下的线程情况
>
> ```bash
> PS C:\Users\sYuan> jstack 5832
> 2021-06-15 20:59:10
> Full thread dump Java HotSpot(TM) 64-Bit Server VM (25.221-b11 mixed mode):
> 
> "DestroyJavaVM" #14 prio=5 os_prio=0 tid=0x0000000002c83800 nid=0x1878 waiting on condition [0x0000000000000000]
>    java.lang.Thread.State: RUNNABLE
> 
> "Thread-1" #13 prio=5 os_prio=0 tid=0x000000001e7c2800 nid=0x47d0 waiting for monitor entry [0x000000001f5cf000]
>    java.lang.Thread.State: BLOCKED (on object monitor)
>         at com.ayuan.daliy.therad.DeadThread$2.run(DeadThread.java:42)
>         - waiting to lock <0x000000076ba7aaa8> (a java.lang.Object)
>         - locked <0x000000076ba7aab8> (a java.lang.Object)
>         at java.lang.Thread.run(Thread.java:748)
> 
> "Thread-0" #12 prio=5 os_prio=0 tid=0x000000001e7c1800 nid=0x2830 waiting for monitor entry [0x000000001f4cf000]
>    java.lang.Thread.State: BLOCKED (on object monitor)
>         at com.ayuan.daliy.therad.DeadThread$1.run(DeadThread.java:26)
>         - waiting to lock <0x000000076ba7aab8> (a java.lang.Object)
>         - locked <0x000000076ba7aaa8> (a java.lang.Object)
>         at java.lang.Thread.run(Thread.java:748)
> 
> "Service Thread" #11 daemon prio=9 os_prio=0 tid=0x000000001e642800 nid=0x55d0 runnable [0x0000000000000000]
>    java.lang.Thread.State: RUNNABLE
> 
> "C1 CompilerThread3" #10 daemon prio=9 os_prio=2 tid=0x000000001e622800 nid=0x4e98 waiting on condition [0x0000000000000000]
>    java.lang.Thread.State: RUNNABLE
> 
> "C2 CompilerThread2" #9 daemon prio=9 os_prio=2 tid=0x000000001e620000 nid=0x468c waiting on condition [0x0000000000000000]
>    java.lang.Thread.State: RUNNABLE
> 
> "C2 CompilerThread1" #8 daemon prio=9 os_prio=2 tid=0x000000001e61d000 nid=0x25f0 waiting on condition [0x0000000000000000]
>    java.lang.Thread.State: RUNNABLE
> 
> "C2 CompilerThread0" #7 daemon prio=9 os_prio=2 tid=0x000000001e61b000 nid=0x29ac waiting on condition [0x0000000000000000]
>    java.lang.Thread.State: RUNNABLE
> 
> "Monitor Ctrl-Break" #6 daemon prio=5 os_prio=0 tid=0x000000001e619800 nid=0x50b8 runnable [0x000000001edce000]
>    java.lang.Thread.State: RUNNABLE
>         at java.net.SocketInputStream.socketRead0(Native Method)
>         at java.net.SocketInputStream.socketRead(SocketInputStream.java:116)
>         at java.net.SocketInputStream.read(SocketInputStream.java:171)
>         at java.net.SocketInputStream.read(SocketInputStream.java:141)
>         at sun.nio.cs.StreamDecoder.readBytes(StreamDecoder.java:284)
>         at sun.nio.cs.StreamDecoder.implRead(StreamDecoder.java:326)
>         at sun.nio.cs.StreamDecoder.read(StreamDecoder.java:178)
>         - locked <0x000000076bbc9d28> (a java.io.InputStreamReader)
>         at java.io.InputStreamReader.read(InputStreamReader.java:184)
>         at java.io.BufferedReader.fill(BufferedReader.java:161)
>         at java.io.BufferedReader.readLine(BufferedReader.java:324)
>         - locked <0x000000076bbc9d28> (a java.io.InputStreamReader)
>         at java.io.BufferedReader.readLine(BufferedReader.java:389)
>         at com.intellij.rt.execution.application.AppMainV2$1.run(AppMainV2.java:48)
> 
> "Attach Listener" #5 daemon prio=5 os_prio=2 tid=0x000000001e561000 nid=0x4934 waiting on condition [0x0000000000000000]
>    java.lang.Thread.State: RUNNABLE
> 
> "Signal Dispatcher" #4 daemon prio=9 os_prio=2 tid=0x000000001e55f000 nid=0x3314 runnable [0x0000000000000000]
>    java.lang.Thread.State: RUNNABLE
> 
> "Finalizer" #3 daemon prio=8 os_prio=1 tid=0x000000001c70e000 nid=0x5570 in Object.wait() [0x000000001eacf000]
>    java.lang.Thread.State: WAITING (on object monitor)
>         at java.lang.Object.wait(Native Method)
>         - waiting on <0x000000076b908ed8> (a java.lang.ref.ReferenceQueue$Lock)
>         at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:144)
>         - locked <0x000000076b908ed8> (a java.lang.ref.ReferenceQueue$Lock)
>         at java.lang.ref.ReferenceQueue.remove(ReferenceQueue.java:165)
>         at java.lang.ref.Finalizer$FinalizerThread.run(Finalizer.java:216)
> 
> "Reference Handler" #2 daemon prio=10 os_prio=2 tid=0x000000001e4f0800 nid=0x2e6c in Object.wait() [0x000000001e9cf000]
>    java.lang.Thread.State: WAITING (on object monitor)
>         at java.lang.Object.wait(Native Method)
>         - waiting on <0x000000076b906c00> (a java.lang.ref.Reference$Lock)
>         at java.lang.Object.wait(Object.java:502)
>         at java.lang.ref.Reference.tryHandlePending(Reference.java:191)
>         - locked <0x000000076b906c00> (a java.lang.ref.Reference$Lock)
>         at java.lang.ref.Reference$ReferenceHandler.run(Reference.java:153)
> 
> "VM Thread" os_prio=2 tid=0x000000001c70a000 nid=0x26f4 runnable
> 
> "GC task thread#0 (ParallelGC)" os_prio=0 tid=0x0000000002c99800 nid=0x1d84 runnable
> 
> "GC task thread#1 (ParallelGC)" os_prio=0 tid=0x0000000002c9b000 nid=0x5508 runnable
> 
> "GC task thread#2 (ParallelGC)" os_prio=0 tid=0x0000000002c9c800 nid=0x2c50 runnable
> 
> "GC task thread#3 (ParallelGC)" os_prio=0 tid=0x0000000002c9e000 nid=0x8a0 runnable
> 
> "GC task thread#4 (ParallelGC)" os_prio=0 tid=0x0000000002ca1000 nid=0x3578 runnable
> 
> "GC task thread#5 (ParallelGC)" os_prio=0 tid=0x0000000002ca2800 nid=0x1eec runnable
> 
> "GC task thread#6 (ParallelGC)" os_prio=0 tid=0x0000000002ca5800 nid=0x35e4 runnable
> 
> "GC task thread#7 (ParallelGC)" os_prio=0 tid=0x0000000002ca6800 nid=0x4cc8 runnable
> 
> "VM Periodic Task Thread" os_prio=2 tid=0x000000001e6fe800 nid=0x3210 waiting on condition
> 
> JNI global references: 12
> 
> 
> Found one Java-level deadlock:
> =============================
> "Thread-1":
>   waiting to lock monitor 0x0000000002d7e618 (object 0x000000076ba7aaa8, a java.lang.Object),
>   which is held by "Thread-0"
> "Thread-0":
>   waiting to lock monitor 0x0000000002d7d228 (object 0x000000076ba7aab8, a java.lang.Object),
>   which is held by "Thread-1"
> 
> Java stack information for the threads listed above:
> ===================================================
> "Thread-1":
>         at com.ayuan.daliy.therad.DeadThread$2.run(DeadThread.java:42)
>         - waiting to lock <0x000000076ba7aaa8> (a java.lang.Object)
>         - locked <0x000000076ba7aab8> (a java.lang.Object)
>         at java.lang.Thread.run(Thread.java:748)
> "Thread-0":
>         at com.ayuan.daliy.therad.DeadThread$1.run(DeadThread.java:26)
>         - waiting to lock <0x000000076ba7aab8> (a java.lang.Object)
>         - locked <0x000000076ba7aaa8> (a java.lang.Object)
>         at java.lang.Thread.run(Thread.java:748)
> 
> Found 1 deadlock.
> ```
>
> ##### 避免死锁
>
> 在系统设计上注意避免死锁的必要条件成立，也要防止进程处于等待状态的情况下占用资源。



