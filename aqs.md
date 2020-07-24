# 动机
- 现有的jdk1.2中的并发控制构建块过于的低层次（ threading primitives, such as synchronized blocks, Object.wait and Object.notify），不容易写正确，甚至专家也会出错。

# 目标
- 环境上，在多核、多线程的环境下，一般性的并发竞争
- 高扩展性，`同步点O(1)时间通过`，平衡资源
- `平衡吞吐量和公平性`
- 提供监控和检查，以方便用于排查性能问题

# 解决方案
现有的Lea的util.concurrent库很适合。  
集成到J2SE中，标准化成一个简单且可扩展的小框架，形成一个包，供用户学习。  

![](https://upload-images.jianshu.io/upload_images/2615789-02449dc316fe1de6.png?imageMogr2/auto-orient/strip|imageView2/2/w/837/format/webp)

- 每个同步器API有自己的同步原语，没有定义统一的操作接口
- 阻塞和非阻塞
- 可选的超时机制
- 单个线程排他互斥和多个线程协同参与

# 细节

## 阻塞, 线程的挂起和恢复
- 原来的Thread.suspend和Thread.resume有顺序性，如果resume先于suspend调用，会忽略掉resume，造成同步存活性问题。
- 超时和可中断

```c++
// Parkers are used by JSR166-JUC park-unpark.
//
// 每个线程都有一个parker类
// 
//src/share/vm/runtime/thread.hpp
class Thread: public ThreadShadow {
    // JSR166 per-thread parker
private:
  Parker*    _parker;
  ...
}

// 线程开始就初始化
void JavaThread::initialize() {
    // Initialize fields
    _parker = Parker::Allocate(this) ;
}
```

```c++
// windows的park很简单，就是靠win32的同步对象
//
//src/share/vm/runtime/park.hpp
//src/os/windows/vm/os_windows.cpp
void Parker::park(bool isAbsolute, jlong time) {
  guarantee (_ParkEvent != NULL, "invariant") ;
  
  // Don't wait if interrupted or already triggered
  if (Thread::is_interrupted(thread, false) ||
    WaitForSingleObject(_ParkEvent, 0) == WAIT_OBJECT_0) {
    ResetEvent(_ParkEvent);
    return;
  }
  else {
    ThreadBlockInVM tbivm(jt);
    OSThreadWaitState osts(thread->osthread(), false /* not Object.wait() */);
    jt->set_suspend_equivalent();

    WaitForSingleObject(_ParkEvent,  time);
    ResetEvent(_ParkEvent);
  }
}

void Parker::unpark() {
  guarantee (_ParkEvent != NULL, "invariant") ;
  SetEvent(_ParkEvent);
}
```

## CLH队列用于排他锁
![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCE93db317107de3a039f257bb33010070d/136)

```java
// 队列定义
public abstract class AbstractQueuedSynchronizer
    extends AbstractOwnableSynchronizer
    implements java.io.Serializable {

    private transient volatile Node head;
    private transient volatile Node tail;
    private volatile int state;
}       
```

```java
// 节点定义
static final class Node {
        volatile int waitStatus;

        volatile Node prev;
        volatile Node next;
        volatile Thread thread;
   
        Node nextWaiter;
}       
```

## CLH队列用于共享锁

## 等待队列用于条件变量

## 公平性

## 同步状态机
> 修改CLH自旋的同步等待==>阻塞的同步框架，线程的恢复就需要额外的状态

# 性能


[aqs04](http://gee.cs.oswego.edu/dl/papers/aqs.pdf)  
[jsr166](https://jcp.org/en/jsr/detail?id=166)  
[A First Look at JSR 166: Concurrency Utilities Blog](https://community.oracle.com/docs/DOC-983326)  
[Overview of package util.concurrent Release 1.3.4](http://gee.cs.oswego.edu/dl/classes/EDU/oswego/cs/dl/util/concurrent/intro.html)  
[AbstractQueuedSynchronizer 详细解析 一切的基础](https://github.com/qiurunze123/threadandjuc/blob/master/docs/AQS.md)  
[从ReentrantLock的实现看AQS的原理及应用](https://tech.meituan.com/2019/12/05/aqs-theory-and-apply.html)  
[深入理解AbstractQueuedSynchronizer(AQS)](https://www.jianshu.com/p/cc308d82cc71)  