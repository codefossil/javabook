#线程同步/并发原语
##cpu缓存
```cpp
//os_cpu/windows_x86/atomic_windows_x86.inline.hpp
interlocked
lock add/dec/*
```
根据程序局部性原理，成本和功耗上的考虑，CPU读取和写入的请求，都会经过：

| RAM | cycle | price($) | hitrate|count
|-----|-------|--------|--------|--------|
|L1    |4       |        |90%|2 per core
|L2     | 15      |        |6%|1 per core
|L3     | 50      |        |3%|1 
|DRAM     | 80      |        |1%|1 


>伪共享
由于其他数据被写，造成所有core中的这条cache line“被无效”。

https://www.usenix.org/legacy/publications/library/proceedings/als00/2000papers/papers/full_papers/sears/sears_html/
http://cenalulu.github.io/linux/all-about-cpu-cache/
程序通过共享访问内存（多线程/内存映射），使得通信变得非常高效，但是会引入以下问题。

##原子性
thread interference/interleave 
>原子操作保证的是数据的完整性，不会出现中间状态

##可见性
```cpp
//x86
sfence/lfence/mfence
```
内存一致性错误（对于相同数据，不同线程看到的不一样）

##有序性
```cpp
//Processor #1:

 while (f == 0);
 // Memory fence required here
 print x;

//Processor #2:

 x = 42;
 // Memory fence required here
 f = 1;
```

- 编译/运行时重排影响，happen-before判定
- cpu流水线指令执行顺序

http://www.felixcloutier.com/x86/index.html
http://gee.cs.oswego.edu/dl/jmm/cookbook.html
http://preshing.com/20120515/memory-reordering-caught-in-the-act/

##反汇编
```cpp
//share/tools/hsdis/hsdis.h
void* decode_instructions(void* start, void* end,..
```

>在jre中，加载反汇编dll+jitwatch即可查看运行时的汇编代码。

注意：简单的方法无法不足以触发JIT
java -XX:+UnlockDiagnosticVMOptions -XX:+PrintAssembly -version

https://github.com/AdoptOpenJDK/jitwatch
https://sourceforge.net/projects/fcml
https://briangordon.github.io/
http://gee.cs.oswego.edu/dl/
http://g.oswego.edu/dl/jmm/cookbook.html

##volatile

```java
//1. 原子性
volatile long i=0;
volatile double j = 0;
```

```java
//2. 可见性和顺序性
//线程A执行的代码
int i = 0;
i = 10;

//线程B执行的代码
j = i;
```
使用场景
- 状态值

https://docs.oracle.com/javase/tutorial/essential/concurrency/atomic.html
http://blog.vinceliu.com/2010/05/difference-between-atomic-and-volatile.html
https://www.ibm.com/developerworks/java/library/j-jtp06197/

##悲观锁
>修改数据之前就独占

##乐观锁
>直到数据修改时才验证冲突（一般是通过对比数据版本号）
wait-free/lock-free

##CAS和自旋锁
``` cpp
//os_cpu/windows_x86/atomic_windows_x86.inline.hpp
[lock] cmpxchg reg, reg/mem
//This instruction is not supported on Intel processors earlier than the Intel486 processors.
```

直到486，x86才有了实现
到2013年，基本上所有多核CPU都实现了硬件CAS

内核态自旋锁：关闭所有软中断(保证线程不被切走，并且响应硬中断)，以此来保证，临界代码尽快被释放掉。
用户态自旋锁：大问题是，锁的时间不被保证，特别是高并发下等待大量时间unlock.

对于自旋锁本身，目前的实现并不会有太大的问题和提升空间；
重要的是理解高并发用户态的线程同步必须要系统支持。

同步实现模式
1. 声明共享变量为volatile
2. 用CAS

虽然CAS由CPU保证，但整个CAS过程（取值、比较）需要消耗大概500个时钟周期（大概相当于500个普通指令），同步的算法优化大都用来减少CAS操作

#程序执行的模式
- [x] 80%的程序都是低竞争
- [x] 有那么一小部分是相同线程嵌套锁定

>Thin Locks: An Implementation of Synchronization for Java

#轻量级/thin-lock
>线程通过spin检查（减少fat-lock用户和内核态的切换）

``` cpp
>share/vm/runtime/synchronizer.cpp
00 has_locker()
```

#重量级/fat-lock
>线程通过park/pending操作，让出CPU等待唤醒

```cpp
//os/windows/vm/os_windows.cpp
00 inflating
10 has_monitor()
objectMonitor = mark->monitor()
park: 调用系统的WaitForSingleObject等待event对象，不断尝试CAS
```

#重入锁/偏向锁
>线程通过线程ID检查（减少thin-lock的spin）
当竞争时，需要撤销偏向锁

- synchronized实现分析
https://www.cnblogs.com/dennyzhangdd/p/6734638.html
https://toutiao.io/posts/cv2q7t/preview
https://www.jianshu.com/p/c5058b6fe8e5
http://www.cnblogs.com/zhenyimo/p/6738210.html
https://cloud.tencent.com/developer/article/1013062

- 参考
https://labs.oracle.com/pls/apex/f?p=labs:49:::::P49_PROJECT_ID:16
https://docs.oracle.com/javase/8/docs/
https://www.ibm.com/developerworks/java/library/j-jtp04223/index.html
https://www.ibm.com/developerworks/library/j-threads1/index.html
https://javainterview-mayank.blogspot.com/2011/04/synchronization-volatile-and-atomic.html

- 性能测试
https://mechanical-sympathy.blogspot.com/2011/11/java-lock-implementations.html
https://flex4java.blogspot.com/2015/03/is-multi-threading-really-worth-it.html
https://baptiste-wicht.com/posts/2010/09/java-synchronization-mutual-exclusion-benchmark.html
https://mailinator.blogspot.com/2008/03/how-fast-is-java-volatile-or-atomic-or.html
#ReentrantLock
https://blog.takipi.com/java-8-longadders-the-fastest-way-to-add-numbers-concurrently/

#AQS
https://www.ibm.com/developerworks/library/j-jtp11234/
https://en.wikipedia.org/wiki/Non-blocking_algorithm
https://kukuruku.co/post/lock-free-data-structures-basics-atomicity-and-atomic-primitives/
http://winterbe.com/posts/2015/05/22/java8-concurrency-tutorial-atomic-concurrent-map-examples/

#fps

http://ifeve.com/enhanced-cas-in-jdk8/https://cloud.tencent.com/developer/article/1021132http://blog.leanote.com/tag/linckye/%E5%B9%B6%E5%8F%91

thread和runable的区别
公平锁
共享锁
读写锁
分段锁


JUC(java.util.concurrent)

https://docs.oracle.com/javase/1.5.0/docs/guide/concurrency/overview.html

线程池
executor
并行流/lambda
actor
同步器



多线程同步和锁
high contention
http://wiki.jikexueyuan.com/project/java-memory-model/lock.html
http://blog.csdn.net/qyp199312/article/details/70598480
http://mishadoff.com/blog/java-magic-part-4-sun-dot-misc-dot-unsafe/
https://blogs.oracle.com/dave/atomic-fetch-and-add-vs-compare-and-swap
https://brooker.co.za/blog/2013/01/06/volatile.html
https://github.com/torvalds/linux/blob/master/arch/x86/include/asm/cmpxchg.h
https://www.quora.com/Why-does-the-Java-API-not-give-control-over-thread-scheduling-to-application-programmers

reentrantlock
死锁的原理和排查方法

http://www.oracle.com/technetwork/java/tuning-139912.html
http://www.oracle.com/technetwork/java/5-136747.html
http://www.oracle.com/technetwork/java/6-performance-137236.html