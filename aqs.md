# 动机
- 现有的jdk1.2中的并发控制构建块过于的低层次（ threading primitives, such as synchronized blocks, Object.wait and Object.notify），不容易写正确，甚至专家也会出错。

# 目标
- 环境上，在多核、多线程的环境下，一般性的并发竞争
- 高扩展性，`同步点O(1)时间通过`，平衡资源
- `平衡吞吐量和公平性`
- 提供监控和检查，以方便用于排查性能问题

# 缺陷
- 多个共享锁请求排队时，并没有按照资源请求数优先级队列
- 代码很多地方都有优化，造成可读性不高

# 解决方案
现有的Lea的util.concurrent库很适合。  
集成到J2SE中，标准化成一个简单且可扩展的小框架，形成一个包，供用户学习。  

![](https://upload-images.jianshu.io/upload_images/2615789-02449dc316fe1de6.png?imageMogr2/auto-orient/strip|imageView2/2/w/837/format/webp)

- 每个同步器API有自己的同步原语，没有定义统一的操作接口
- 阻塞和非阻塞
- 可选的超时机制
- 单个线程排他互斥和多个线程协同参与

# 细节

## 阻塞, 线程的挂起和唤醒
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

## CLH同步队列

```java
// 队列定义
public abstract class AbstractQueuedSynchronizer
    extends AbstractOwnableSynchronizer
    implements java.io.Serializable {

    // CLH同步队列
    // 头节点是个哑节点
    private transient volatile Node head;
    private transient volatile Node tail;

    // 同步状态，可以表示锁的数量限制
    private volatile int state;
}       
```

```java
// 节点定义
static final class Node {
        volatile int waitStatus;

        // 条件队列
        volatile Node prev;
        volatile Node next;
        volatile Thread thread;   
        Node nextWaiter;
}       
```

## 同步状态抢占

- 独占锁实现的是tryAcquire(int)、tryRelease(int)
- 共享锁实现的是tryAcquireShared(int)、tryReleaseShared(int)

由子类（CountDownLatch, ReentantLock）实现具体的同步抢占规则（公平/不公平）。  

## CLH队列排他锁
![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCE93db317107de3a039f257bb33010070d/136)


```java
// 排队过程
final boolean acquireQueued(final Node node, int arg) {
  for (; ; ) {
      if 获取到资源 && 队首 then
        setHead
        返回

      挂起   
  }  
}
```

```java
// 释放过程
// 先独占锁，才能释放锁
private void unparkSuccessor(Node node) {    
  if 第一个节点不是cancel || 找到最近的一个不是cancel状态的节点 then
    唤醒线程
    退出
}
```

## CLH队列用于共享锁

```java
// 请求过程
// 比排他锁多出来唤醒其他线程
private void doAcquireShared(int arg) {
    final Node node = addWaiter(Node.SHARED);//加入队列尾部
    boolean failed = true;//是否成功标志
    for (; ; ) {
      if 获取到资源 && 队首 then
        setHead
        唤醒其他线程
        返回

      挂起
    }    
}
```

```java
// 释放过程
private void doReleaseShared() {
  if 第一个节点.state=signal then
    unparkSuccessor
  else if state=0 then
    state=PROPAGATE
}
```

## 条件队列转移到同步队列
ConditionObject适用条件  
- 任何支持Lock接口的排他锁
- 只能持有锁的线程进行条件操作

```java
// signal
private void doSignal() {
  for(;;到下一个节点){
    移动第一个节点到同步队列，并唤醒    
  }
}
```


```java
// await
private void await() {
  创建节点，加入条件队列
  释放锁
  如果没有在同步队列中，就挂起自己
  在同步队列中排他获取资源
  释放资源
}
```


## 不公平，偷取线程
- 提高吞吐
- 减少入队时间

`在队列中第一个线程被唤醒之前，有大量的并发请求线程有机会获取资源`  

相对公平竞争环境：
用户来决定改写tryRequire的逻辑，结合队列的threadID来定义。  



## 节点状态
> 修改CLH自旋的同步等待==>阻塞的同步框架，线程的唤醒就需要额外的状态

waitStatus, 负值表示结点处于有效等待状态，而正值表示结点已被取消  
CANCELLED =  1;
SIGNAL    = -1;
CONDITION = -2;
PROPAGATE = -3;


# 性能
- 一个函数：进行简单的随机数计算
- 一个概率：进入锁的概率

线程：从无竞争（1个线程）到竞争饱和时（256个线程），分别调用函数，计算锁的开销。

开销结论：
1. 同步器的性能10x+好于sync
2. 比无竞争慢一半
3. 公平的同步器性能很差，差100x+。（作者猜测是由于多次的上下文切换）

吞吐结论：  
多核情况下，很快几个线程就会造成最差性能，之后随着线程增加，没有扩展性问题。

[aqs04](http://gee.cs.oswego.edu/dl/papers/aqs.pdf)  
[jsr166](https://jcp.org/en/jsr/detail?id=166)  
[A First Look at JSR 166: Concurrency Utilities Blog](https://community.oracle.com/docs/DOC-983326)  
[Overview of package util.concurrent Release 1.3.4](http://gee.cs.oswego.edu/dl/classes/EDU/oswego/cs/dl/util/concurrent/intro.html)  
[AbstractQueuedSynchronizer 详细解析 一切的基础](https://github.com/qiurunze123/threadandjuc/blob/master/docs/AQS.md)  
[从ReentrantLock的实现看AQS的原理及应用](https://tech.meituan.com/2019/12/05/aqs-theory-and-apply.html)  
[深入理解AbstractQueuedSynchronizer(AQS)](https://www.jianshu.com/p/cc308d82cc71)  

[package overview](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/package-summary.html)  
[Concurrency JSR-166 Interest Site](http://gee.cs.oswego.edu/dl/concurrency-interest/index.html)  
[DOC: Java Concurrency Utilities](https://docs.oracle.com/javase/8/docs/technotes/guides/concurrency/index.html)