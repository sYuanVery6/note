## Language Base

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

14. `java关键字` `锁` `线程安全` **Synchronized和volatile关键字及线程安全**

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

15. `锁` `死锁` **什么是死锁？怎样避免死锁？**

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

16. `锁` `synchronized` `Lock` **Lock和synchronized的区别？**

> | 区别点   | synchronized                                                 | Lock                                                         |
> | -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
> | 存在层次 | Java的关键字，在jvm层面                                      | 是一个接口                                                   |
> | 锁的释放 | 1. 以前获取锁的线程执行完同步代码，释放锁 2. 线程执行发生异常，jvm会让线程释放锁 | 在finally中必须释放锁，不然容易造成线程死锁                  |
> | 锁的获取 | 假设A线程获得锁，B线程等待。如果A线程阻塞，B线程会一直等待   | 分情况而定，Lock有多个锁获取的方式。lock等待过程中可以用interrupt来中断等待 |
> | 锁状态   | 无法判断                                                     | 可以判断,通过tryLock()方法获取锁状态                         |
> | 锁类型   | 可重入 不可中断 非公平                                       | 可重入 可判断 可公平                                         |
> | 性能     | 少量同步                                                     | 大量同步                                                     |

17. `原子类` `atomic` **说一下atomic的原理**

> Atomic包中的类基本的特性就是在多线程环境下，当有多个线程同时对单个（包括基本类型和引用类型）变量进行操作时，具有排他性，即当多个线程同时对该变量的值进行更新时，仅有一个线程能成功，而未成功的线程可以像自旋锁一样，继续尝试，一直等到执行成功
>
> Atomic系列的类中的核心方法都会调用unsafe类中的几个本地方法。我们需要先知道一个东西就是Unsafe类，全名为sun.misc.Unsafe，这个类包含了大量的对C代码的操作，包括很多直接内存分配以及原子操作的调用，而它之所以标记为非安全的，是告诉你这个里面大量的方法调用都会存在安全隐患，需要小心使用，否则会导致严重的后果，例如在通过unsafe分配内存的时候，如果自己指定某些区域可能会导致一些类似C++一样的指针越界到其他线程的问题

18. `锁` **锁的种类？**

> ##### 乐观锁与悲观锁
>
> 乐观锁和悲观锁是数据库引入的概念
>
> * 悲观锁：是指对数据被外界的修改持保守态度，认为数据很容易被其他线程修改，所以在数据被处理前先对数据进行加锁，并在整个数据处理过程中，使数据处于锁定状态。synchronized就是悲观锁的实现。
> * 乐观锁：乐观锁是相对悲观锁来说，他认为数据一般情况下不会造成冲突，所以在访问记录前不会加排它锁，而是在数据提交更新时，才会正式对数据冲突进行检测。乐观锁并不会使用数据库提供的锁机制，一般在表中添加version字段或者使用业务状态来实现。乐观锁直到提交时才锁定，所以不会产生任何死锁。
>
> ##### 公平锁与非公平锁
>
> 根据线程获取锁的抢占机制，锁可以分为公平锁和非公平锁
>
> * 公平锁表示线程获取锁的顺序是暗战线程请求锁的时间早晚来决定的，也就是最早请求锁的线程将最早获得锁
> * 非公平锁则在运行时闯入，也就是先来不一定先得
>
> synchronized是非公平锁，ReentrantLock提供了公平锁和非公平锁两种实现，默认是非公平锁。
>
> 在没有公平性要求的前提下尽量使用非公平锁，因为公平锁会带来性能开销
>
> ##### 独占锁和共享锁
>
> 根据锁只能被单个线程持有还是被多个线程共同持有，锁可以分为独占锁和共享锁
>
> * 独占锁：保证在任何时候都只有一个线程能获得到锁，ReentrantLock就是以独占方式实现的。
> * 共享锁则可以同时由多个线程持有，例如ReadWriteLock读写锁，它允许被多个线程同时进行读操作
>
> 独占锁是一种悲观锁，由于每次访问资源都先加上互斥锁，这限制了并发性。
>
> 共享锁则是一种乐观锁，它放宽了加锁的条件，允许多个线程同时进行读操作。
>
> ##### 可重入锁
>
> 当一个线程在次获取它自己已经获取的锁时，如果不被阻塞，那么我们说这个锁就是可重入的。
>
> 实际上synchronized内部锁是可重入锁，可重入锁的原理是在锁内部维护一个线程标识，用来标识该锁目前被哪个线程占用，然后关联一个计数器。一开始计数器值为0.说明该锁没有被任何线程占用。当一个线程获取了该锁时，计数器的值会变1，这时其他线程来获取锁时发现锁的所有者不是自己而被阻塞挂起
>
> ##### 自旋锁
>
> 自旋锁则是，当前线程在获取锁时，如果发现锁已经被其他线程占有，他不会马上来阻塞自己，在不放弃CPU使用权的情况下，多次尝试获取，很有可能在后面几次尝试中其他线程已经释放了锁

### Java Collection

java集合，封装了一些常用的数据结构用于存储对象，是日常开发中最常使用的工具

![img](https://images2015.cnblogs.com/blog/595137/201511/595137-20151126193134202-1199713105.png)

------

1. `Collection` **常用的集合**

> * List列表：有序，可重复
> * Set集合：无序，不可重复
> * Map映射表：存储键值对，键不可重复，值可重复

2. `Collection` `List` **List常用的具体实现类**

> ##### ArrayList
>
> * 底层实现：数组
>
> * 特点：读取效率高，插入或者删除时引起扩容会效率变慢
>
>   ```java
>   // 插入元素
>   public void add(int index, E element) { 
>       //检查索引是否合法 
>       rangeCheckForAdd(index); 
>       //判断是否扩容 
>       ensureCapacityInternal(size + 1); 
>       // Increments modCount!! 
>       //native方法，将一个数组的0到index复制到一个新数组，索引区间为index+1到length-1也复制到一个新的数组。执行完后将新数组指向原数组对象。 
>       System.arraycopy(elementData, index, elementData, index + 1,size - index); 
>       //执行完arraycopy方法后，数组的index位置为空缺，将index位置赋值 
>       elementData[index] = element; size++; 
>   }
>   ```
>
>   ```java
>   // 删除
>   public E remove(int index) {    
>       rangeCheck(index);    
>       modCount++;    
>       E oldValue = elementData(index);    
>       int numMoved = size - index - 1;    
>       if (numMoved > 0)        
>           System.arraycopy(elementData, index+1, elementData, index,numMoved);    
>       elementData[--size] = null; 
>       // clear to let GC do its work    
>       return oldValue; 
>   }
>   ```
>
> * 扩容机制：
>
>   创建一个1.5倍长度的数组，然后利用Array.copyOf方法把旧数组的值全部复制到新数组中，在把内部的数组成员指向新创建的数组
>
>   ```java
>   private static final int MAX_ARRAY_SIZE = Integer.MAX_VALUE - 8; 
>   @param minCapacity： 插入当前元素后List的size属性 
>       private void grow(int minCapacity) {    
>       // overflow-conscious code    
>       int oldCapacity = elementData.length;   
>       //计算扩容后新数组的长度（原数组长度的1.5倍） 
>       int newCapacity = oldCapacity + (oldCapacity >> 1);    
>       if (newCapacity - minCapacity < 0)        
>           newCapacity = minCapacity;    
>       if (newCapacity - MAX_ARRAY_SIZE > 0)   
>           //当新扩容的数组长度超过2,147,483,647时（2的15次方减1），新数组的长度为2,147,483,647 
>           newCapacity = hugeCapacity(minCapacity);    
>       // minCapacity is usually close to size, so this is a win:    
>       elementData = Arrays.copyOf(elementData, newCapacity); 
>   } 
>   private static int hugeCapacity(int minCapacity) {    
>       if (minCapacity < 0) 
>           // overflow        
>           throw new OutOfMemoryError();  
>       return (minCapacity > MAX_ARRAY_SIZE) ? Integer.MAX_VALUE : MAX_ARRAY_SIZE; 
>   }
>   ```
>
>   
>
> * 适用场景：读多写少
>
> ##### LinkedList
>
> * 底层实现：链表，基于LinkedList的内部类Node用来存储每一个节点的元素和前后节点的元素的引用地址
>
>   ```java
>   private static class Node<E> { 
>       //节点元素 
>       E item;    
>       //前一个节点 
>       Node<E> next;  
>       //后一个节点 
>       Node<E> prev;    
>       Node(Node<E> prev, E element, Node<E> next) {        
>           this.item = element;        
>           this.next = next;        
>           this.prev = prev;    
>       } 
>   }
>   ```
>
> * 特点：比较高数组元素的插入和删除效率，但是查询操作比较慢
>
> * 适用场景：读少写多
>
> ##### ArrayList与LinkedList对比
>
> * ArrayList底层由数组实现，能通过索引下标直接获取元素，无需遍历整个集合。LinkedList底层由链表实现，通过索引查找指定元素时，需要遍历链表，直到找到为止
> * ArrayList每当数组容量被填满的时候就需要扩容，扩容的过程产生很大的消耗，随机插入或者删除时，ArrayList会将插入位置后的元素索引加1，删除时减1。而LinkedList因为基于链表实现，随机插入和删除元素只要改变前后的指针就可以实现
>
> ##### Vector与ArrayList对比
>
> 相同点：
>
> * 底层都是基于数组实现，相当于一种动态数组
> * 都继承了Collection接口，都是有序集合
>
> 不同点：
>
> * 同步性：Vector是线程安全的，它的方法由synchronized关键字修饰，ArrayList是线程不安全的
> * 数组增长：Vector扩容时，默认增长为原数组长度的两倍，ArrayList为原来的1.5倍，Vector可以设置增长空间的大小，而ArrayList不可以设置

3. `Collection` `Map` **Map的具体实现类**

> ##### HashMap
>
> * 底层实现
>
>   * 1.7：数组+链表
>   * 1.8：数组+链表+红黑树
>
> * HashMap如何解决Hash冲突
>
>   * 使用put方法向HashMap里面放元素时，会先计算key的hashcode，在通过putVal方法插入map
>
>     ```java
>     public V put(K key, V value) {    
>         //将元素通过putVal方法插入到map 
>         return putVal(hash(key), key, value, false, true); 
>     } 
>     // 计算要插入的key的Hash值 
>     static final int hash(Object key) {    
>         int h;    
>         return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16); 
>     }
>     ```
>
>   * putVal将元素插入map的逻辑
>
>     ```java
>     // map底层用来存储元素的数组
>     transient Node<K,V>[] table;
>                     
>     /** * Implements Map.put and related methods. 
>     * 
>     * @param hash hash for key 
>     * @param key the key 
>     * @param value the value to put 
>     * @param onlyIfAbsent if true, don't change existing value 如果为真，则不要更改现有值
>     * @param evict if false, the table is in creation mode. 如果为false，则表处于创建模式
>     * @return previous value, or null if none */
>     final V putVal(int hash, K key, V value, boolean onlyIfAbsent, boolean evict) {  
>                         
>         Node<K,V>[] tab; 
>         Node<K,V> p;
>         int n, i;
>                         
>         //判断table为空或者数组长度为0，将tab和n赋值（底层数组和数组长度）
>         if ((tab = table) == null || (n = tab.length) == 0)
>             //如果为空，则通过resize()方法为数组分配默认容量
>             n = (tab = resize()).length;
>             //判断数组中的hash位置的元素是否为null
>         if ((p = tab[i = (n - 1) & hash]) == null)
>             //如果数组中的hash位置的元素为Null，创建一个node对象放到数组
>             tab[i] = newNode(hash, key, value, null);
>         //如果数组不为空且数组中的hash位置元素不是Null,这时候向链表插入元素
>         else {        
>             Node<K,V> e; 
>             K k; 
>             //判断数组中的hash位置元素p的key与hash值与要插入的元素是否相等，相等的话，将数组中的hash位置赋值给e；顺便将k赋值
>             //这里就是判断新插入的元素的key是否存在于map中
>             if (p.hash == hash && ((k = p.key) == key || (key != null && key.equals(k))))            
>                 e = p;
>             //判断数组中的hash位置元素是否为TreeNode类型，如果是树节点类型，则调用树节点类型的put方法（putTreeVal）
>             else if (p instanceof TreeNode) 
>                 e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value); 
>             //如果新插入的元素不等于数组中的hash位置元素且数组尾元素不是树节点
>             else {
>                 //循环遍历整个链表
>                 for (int binCount = 0; ; ++binCount) {
>                     //判断tab[hash]的下一个链表节点是否为null
>                     if ((e = p.next) == null) {
>                         //tab[hash]不存在下一个节点的话，将新元素插入到下一个节点
>                         p.next = newNode(hash, key, value, null);                    
>                         if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st    
>                             //如果链表长度超过8，把链表转换为红黑树
>                             treeifyBin(tab, hash);                    
>                             break;                
>                         }
>                      //如果p的下一个节点和新插入的元素key，hash相同
>                      if (e.hash == hash && ((k = e.key) == key || (key != null && key.equals(k))))                    
>                          break;                
>                      p = e;            
>                 }        
>             }        
>             if (e != null) {// existing mapping for key            
>                 V oldValue = e.value; 
>                 //如果存在相同key的话，将新值赋给该key所属node的value，并返回旧value
>                 if (!onlyIfAbsent || oldValue == null)               
>                     e.value = value;           
>                 afterNodeAccess(e);//回调，允许LinkedHashMap的后操作            
>                 return oldValue;        
>             }    
>         }    
>         ++modCount;    
>         //判断是否需要扩容
>         if (++size > threshold)        
>             resize();    
>         afterNodeInsertion(evict);    
>         return null
>     }
>     ```

4. `Collection` **Collection和Collections有什么区别？**

> * Collection是集合工具的顶级接口
> * Collections封装了操作集合的工具类

5. `Map` **HashMap和HashTable有什么区别？**

> * 存储：HashMap允许key和value为null，而HashTable不允许
> * 线程安全：HashTable是线程安全的，而HashMap是非线程安全的
> * 推荐使用：在HashTable的类煮熟可以看到，HashTable是保留类不建议使用，推荐在单线程环境下使用HashMap替代，如果需要多线程使用则用ConcurrentHashMap替代

6. `Map` **如何决定使用HashMap和TreeMap？**

> ##### TreeMap
>
> TreeMap的key值时要求实现`java.lang.Comparable`，所以迭代的时候TreeMap默认是安照Key值升序排序的；TreeMap的实现是基于红黑树结构，适用于按自然顺序或自定义顺序遍历键
>
> ##### HashMap
>
> HashMap的key值实现散列hashCode()，分布式散列的、均匀的，不支持排序；数据结构主要是桶（数组），链表或红黑树。适用于在Map中插入、删除和定位元素
>
> ##### 结论
>
> 如果你需要得到一个有序的结果时就应该使用TreeMap。除此之外，由于HashMap有更好的性能，所以大多不需要排序的时候我们会使用HashMap

7. `Set` **HashSet的实现原理**

> HashSet的底层是基于hashMap实现的，所以HashSet的值都存储在底层的HashMap的键上

8. `array` `List` **如何实现数组和List之间的转换？**

> * 数组转List
>
>   ```java
>   List<String> l = Arrays.asList({"a","b","c"});
>   ```
>
> * List转数组
>
>   ```java
>   String[] arr = list.toArray(new String[list.size()]);
>   ```

9. `集合` `线程安全` **哪些集合时线程安全的？**

> * vector
> * hashTable
> * concurrentHashMap
> * CopyAndWriteArrayList

10. `设计模式` `迭代器模式` **迭代器iterator是什么？**

> ##### 迭代器模式
>
> 用于顺序访问集合对象的元素，无需知道集合对象的底层实现
>
> ##### Iterator
>
> 是可以遍历集合的对象，为各种容器提供了公共的操作接口，隔离对容器的遍历操作和底层实现，从而解耦。
>
> 缺点是增加新的集合类需要对应增加新的迭代器类，迭代器类与集合类成对增加。

11. `线程安全` `ConcurrentHashMap` **ConcurrentHashMap的底层结构和实现原理？**

> TODO
>
> https://blog.csdn.net/zengxiantao1994/article/details/89302583

12. **为什么我们需要ConcurrentHashMap和CopyOnWriteArrayList？**

> TODO

### Java Exception

------

1. `关键字` `throw` `throws` **throw和throws的区别？**

> ##### throw
>
> * 作用在方法内，表示抛出具体异常，由方法内的语句处理
> * 具体向外抛出的动作，所以它抛出的是一个异常实体类。若执行了throw一定是抛出了某种异常。
>
> ##### throws
>
> * 作用在方法的声明上，表示如果抛出异常，则由该方法的调用者来进行异常处理
> * 主要的声明这个方法会抛出某种类型的异常，让它的使用者知道捕获异常的类型
> * 出现异常是一种可能性，但不一定会发生异常
>
> ##### 区别
>
> * 作用的位置不一样，throws作用于方法头，throw用于方法内部
> * throws，表示一种可能性，不一定会抛出异常，可以一次性抛出多个异常；而throw只能一个，使用throw一定会抛出异常
> * throws抛出异常时，它的上级（调用者）也要申明抛出异常或者捕获，不然编译会报错。而throw的话，可以不申明或不捕获，但编译器不会报错

2. `关键字` `try-catch-finally` **try-catch-finally用法**

> 是java提供进行异常处理的关键字
>
> ```java
> try{
>     // 代码执行区域
> }catch(Exception e){
>     // 异常处理区域
> }finally{
>     // 无论如何，最终都会执行的区域
> }
> ```
>
> ##### 执行顺序
>
> * 当代码中未出现异常时
>
>   try-finally
>
> * 当代码中出现异常时
>
>   try-catch-finally
>
> * 当try-finally同时有返回值时，返回值为谁的？
>
>   finally中的返回值会被返回

3.  `关键字` `异常` **当catch中return了，finally中的代码还会执行吗？**

> 会执行，在return前执行。
>
> demo->https://blog.csdn.net/qq_40180411/article/details/81428382

4. `异常` **常见的异常类有哪些？**

> * 空指针-NullPointerException 
>
>   * 对象调用方法时，如果对象没初始化会报
>
> * 数组越界-IndexOutOfBoundsException
>
>   * 将字符串分割成数组时，操作不当会报
>
> * 数据库异常-SQLException 
>
>   * 连接数据库时，出问题会报（我不太常见）
>
> * IO异常-IOException
>
>   * 通过url下载文件时，由于请求参数包含未被编码的汉字会报
>   * 操作IO时会报
>
> * 参数不合法-IllegalArgumentException
>
>   * 方法接收的参数不合法
>
> * 运行时异常-RuntimeException
>
>   * 处理业务时，可自定义异常信息，在运行错误时抛出
>
> * 栈溢出-StackOverflowError
>
>   * 函数调用栈太深了，常见于递归方法。
>
>     场景：遍历有向带环图时，通过递归方式得出某一点开始的所有路径，因为带环原因，会出现无限递归，后来通过一个集合记录每次遍历过的两个点，遍历之前先去集合判断，避免重复
>
> * 内存溢出-OutOFMemory
>
>   * 线程池不停地创建线程，但是并为进行释放，导致线程对象过多导致内存溢出
>   * 读取大的IO文件，文件大小查过JVM分配内存大小

5. `异常链` **什么是异常链？**

> 异常链是指在进行一个异常处理时抛出另一个异常，由此产生了一个异常链条，大多用于将受检查异常封装成为非受检查异常或者RuntimeException。特别注意如果你因为一个异常而决定抛出另一个新的异常时，一定要包含原有的异常，这样处理程序才可以通过getCause()和inItCause()方法来访问异常的最终根源

6. `自定义异常` **java中如何编写自定义异常？**

> 可以通过继承Exception类或者其任何子类来实现自己的自定义异常类，自定义异常类可以有自己的变量和方法来传递错误代码或者其他异常相关信息来处理异常。

7. `异常处理` **关于异常处理的经验和心得？**

> * 方法返回值尽量不要使用Null，这样可以避免很多空指针异常
> * 避免在finally中使用return语句或者抛出异常，如果调用的其他代码可能抛出异常则应该捕获异常并进行处理，因为finally中的return不仅会覆盖try和catch内的返回值且还会掩盖try和catch内的异常，就像异常没发生一样
> * 尽量不要在catch块中压制异常，便于排查错误
> * 方法定义中throws尽量定义具体的异常列表
> * 不要使用异常控制程序的流程，影响性能

### Java Reflection

------

1. `反射` **什么是反射？你对反射的理解**

> Java反射机制是运行状态中，对于任意一个实体类，都能够知道这个类的所有属性和方法。
>
> ##### 理解
>
> java程序可以在运行时才得知名称的class，获悉其完整构造，并生成其对象实体、或者对其field设值，或执行其methods,使java拥有动态语言的特性

2. `序列化` **什么是java序列化？什么情况下需要序列化？**

> * 序列化：将java对象转换成字节流的过程
> * 反序列化：将字节流转换成java对象的过程
>
> 当java对象需要在网络上传输或者持久化存储到文件中时，就需要对java对象进行序列化处理
>
> ##### 序列化的实现
>
> 类实现Serializable接口，这个接口没有需要实现的方法。实现Serializable接口是为了告诉jvm这个类的对象可以被序列化
>
> * 某个类可以被序列化，则其子类也可以被序列化
> * 声明为static和transient的成员变量，不能被序列化。static成员变量时描述类级别的属性，transient表示临时数据
> * 反序列化读取序列化对象的顺序要保持一致

3. `反射` **反射的日常应用**

> * 框架常见的技术
>
>   * 结合SpringAOP和注解开发用户操作日志模块
>
>     注解存储接口要记录的操作和一些值，AOP通过反射获取被访问的接口及接口参数，然后进行日志插入操作
>
>   * Spring 注入属性
>
> * 动态代理
>
>   * 详见设计模式之动态代理

4. `序列化` **什么情况下需要使用序列化？**

> * 想把内存中的对象保存到一个文件中或者数据库中时
> * 想用套接字在网络上传送对象的时候
> * 想通过RMI（远程方法调用）传输对象的时候

5. `反射` **反射的优缺点**

> * 优点：可以动态执行，在运行期间根据业务功能动态执行方法，访问属性，最大限度发挥了java的灵活性
> * 缺点：对性能有影响，反射需要在内存中解析字节码，这类操作总是慢于直接执行java代码

6. `反射` **实现java反射的类有什么？**

> * Class：类
> * Field：字段
> * Method：方法
> * Constructor：构造方法

### Java8新特性

------

1. `java8` java8新特性简介？

> * 代码更少(lambda表达式，即箭头函数)
> * 强大的Stream API（分治方式操作集合）
> * 最大化减少空指针异常：Optional类
> * 接口的新特性
> * 注解的新特性
> * 集合的底层 源码实现（ArrayList的初始容量，HashMap散列表加红黑树）
> * 新的日期时间API
> * 使用元空间替代永久区

2. `Lambda` 什么是Lambda？日常开发在哪里用到了？

> * Lambda表达式，也可称为闭包，是推动java8发布的最重要新特性
> * lambda表达式允许把函数作为一个方法的参数
> * 使用Lambda表达式可以使代码变得更加简洁紧凑

3. `Lambda` 使用Lambda表达式的注意点

> * Lambda白到时主要用来执行行内执行的方法类型接口，例如一个简单方法接口
> * lambda表达式免去了使用匿名方法的麻烦
>
> ##### 变量作用域
>
> * Lambda表达式只能引用标记了final的外层局部变量，这就是说不能在lambda内部修改定义在域外的局部变量，否则会编译错误
> * lambda表达式的局部变量可以不用声明为final，但是必须不可被后面的代码修改
> * 在lambda表达式当中不允许声明一个与局部变量同名的参数或者局部变量

4. `函数式接口` 什么是函数式接口？

> * 函数式接口在java中是指：有且仅有一个抽象方法的接口
> * 函数式接口，即适用于函数式编程场景的接口。而java中的函数式编程体现就是lambda，所以函数式接口就是可以适用于lambda使用的接口。只有确保接口中仅有一个抽象方法，java中的lambda才能顺利地进行推导
>
> ##### 语法糖
>
> “语法糖”是指使用更加方便，但是原理不变的代码语法。例如在遍历集合时使用的for-each语法，其实底层的实现原理仍然是迭代器。这边是“语法糖”。从应用层面来讲，java中的lambda可以被当做是匿名内部类的语法糖，但是二者在原理上是不同的。

5. `函数式接口` java四大内置核心函数式接口

> | 函数式接口              | 参数类型 | 返回类型 | 用途                                                         |
> | ----------------------- | -------- | -------- | ------------------------------------------------------------ |
> | Consumer<T> 消费型接口  | T        | void     | 对类型为T的对象应用操作，包含方法：void accept(T t)          |
> | Supplier<T>供给型接口   | 无       | T        | 返回类型为T的对象，包含方法T get()                           |
> | Function<T,R>函数型接口 | T        | R        | 对类型为T的对象应用操作，并返回结果。结果是R类型的对象，包含方法R apply(T t) |
> | Predicate<T> 断言型接口 | T        | Boolean  | 确定类型为T的对象是否满足某种约束，并返回Boolean值。包含方法Boolean test(T t) |

6. `stream` 对Stream的认识

> Stream是对集合对象功能的增强，它专注于对集合对象进行各种非常便利、高效的聚合操作，或者大批量数据操作。Stream API借助于Lambda表达式，极大的提高编程效率和程序可读性。同时提供串行和并行两种模式进行汇聚操作，并发模式能够充分利用多核处理器优势，使用fork/join并行方式来拆分任务和加速处理过程
>
> Stream不是集合元素，不是数据结构并不保存数据，它是有关算法和计算的，它更像一个高级版本的Iterator。就如同一个迭代器，单向，不可重复，数据只能遍历一次，遍历过一次后即用尽了，就好比流水从前面流过，已去不复返

7. `stream` Stream的生命周期

> * 生成
> * 操作、变换（可以多次）
> * 消耗（只有一次）

8. `fork/join` Fork/Join框架

> 在必要情况下，将一个大任务进行拆分（fork）成若干个小任务（拆到不可在拆时），在将一个个的小任务运算的结果进行汇总（join）

9. `fork/join` Fork/Join与传统线程池的区别

> 当执行新的任务时它可以将其拆分成更小的任务执行，并将小任务加到线程队列中，然后在从一个随机线程的队列中偷一个并把它放在自己队列中。
>
> 相对于一般的线程池实现，fork/join框架的优势体现在对其中包含的任务的处理方式上，在一般的线程池中，如果一个线程正在执行的任务由于某些原因无法继续运行，那么该线程会处于等待状态，而在fork/join框架的实现中，如果某个子问题等待另一个子问题的完成而无法继续运行，那么处理该问题的线程会主动寻找其他尚未运行的子问题来执行，这种方式减少了线程的等待时间，提高了性能

