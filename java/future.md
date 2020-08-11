# 动机
- 可取消的、异步的计算


# 解决方案


# 细节

```java
public class FutureTask<V> implements RunnableFuture<V> {
    private volatile int state;
    private static final int NEW          = 0;
    private static final int COMPLETING   = 1;
    private static final int NORMAL       = 2;
    private static final int EXCEPTIONAL  = 3;
    private static final int CANCELLED    = 4;
    private static final int INTERRUPTING = 5;
    private static final int INTERRUPTED  = 6;

    /** The underlying callable; nulled out after running */
    private Callable<V> callable;
    /** The result to return or exception to throw from get() */
    private Object outcome; // non-volatile, protected by state reads/writes
    /** The thread running the callable; CASed during run() */
    private volatile Thread runner;
    /** Treiber stack of waiting threads */
    private volatile WaitNode waiters;
}
```

## 执行任务
```java
public void run() {
    cas(runner, currentThread);
    result = c.call();
    cas(state, NEW, COMPLETING);
    cas(state, COMPLETING, NORMAL);
}
```

## Treiber栈用于获取任务结果线程排队

![](https://segmentfault.com/img/bVbiwFZ?w=231&h=422)

```java
private int awaitDone(boolean timed, long nanos) throws InterruptedException {
    WaitNode q = null;
    boolean queued = false;
    for (;;) {        
        int s = state;

        创建q = new WaitNode;
        cas(waiter, waiters, q); // Treiber无锁栈
        LockSupport.park();

        if (s > COMPLETING) then
            return s;            
    }
}
```

## 完成任务
```java
private void finishCompletion() {
    q = waiter;
    for (;;) {
        Thread t = q.thread;
        LockSupport.unpark(t);        
        q = next;
    }
}
```

# 参考

[The Incremental Garbage Collection of Processes(future design pattern), baker77](http://home.pipeline.com/~hbaker1/Futures.html)  
第一篇提及future这个关键词的（等同于promise和eventual）。  

[A Scalable Lock-free Stack Algorithm, hendler09-jpdc](http://people.csail.mit.edu/shanir/publications/Lock_Free.pdf)

[Java多线程进阶（四二）—— J.U.C之executors框架：Future模式](https://segmentfault.com/a/1190000016767676)


