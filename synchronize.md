#同步/并发原语#
interlocked opteration
intrinsic function
lock add/dec/*
This instruction is not supported on Intel processors earlier than the Intel486 processors.
On most instructions a lock prefix must be explicitly used except for the xchg instruction where the lock prefix is implied if the instruction involves a memory address.

http://www.felixcloutier.com/x86/index.html
http://gee.cs.oswego.edu/dl/jmm/cookbook.html

#自旋锁#
[lock] cmpxchg reg, reg/mem
内核态自旋锁：关闭所有软中断(保证线程不被切走，并且响应硬中断)，以此来保证，临界代码尽快被释放掉。
用户态自旋锁：大问题是，锁的时间不被保证，特别是高并发下等待大量时间unlock.

对于自旋锁本身，目前的实现并不会有太大的问题和提升空间；
重要的是理解高并发用户态的线程同步必须要系统支持。

同步实现模式
1. 声明共享变量为volatile
2. 用CAS

synchronized

https://labs.oracle.com/pls/apex/f?p=labs:49:::::P49_PROJECT_ID:16

https://docs.oracle.com/javase/8/docs/
https://www.ibm.com/developerworks/java/library/j-jtp04223/index.html
https://www.ibm.com/developerworks/library/j-threads1/index.html
https://javainterview-mayank.blogspot.com/2011/04/synchronization-volatile-and-atomic.html

AQS
https://www.ibm.com/developerworks/library/j-jtp11234/
https://en.wikipedia.org/wiki/Non-blocking_algorithm
https://kukuruku.co/post/lock-free-data-structures-basics-atomicity-and-atomic-primitives/


thread和runnable的区别

JUC(java.util.concurrent)

https://docs.oracle.com/javase/1.5.0/docs/guide/concurrency/overview.html

线程池
executor
并行流/lambda
actor
同步器
AQS同步组件



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
偏向锁
悲观锁
乐观锁
单变量无锁无阻塞
死锁的原理和排查方法