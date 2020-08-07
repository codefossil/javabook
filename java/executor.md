# 动机
- 


# 解决方案
![](https://segmentfault.com/img/bVbx7kE?w=746&h=425)

# 细节

```java
public class ThreadPoolExecutor extends AbstractExecutorService {
    /**
    * 保存线程池状态和工作线程数:
    * 低29位: 工作线程数
    * 高3位 : 线程池状态
    */
    private final AtomicInteger ctl = new AtomicInteger(ctlOf(RUNNING, 0));
    
    private static final int COUNT_BITS = Integer.SIZE - 3;
    
    // 最大线程数: 2^29-1
    private static final int CAPACITY = (1 << COUNT_BITS) - 1;  // 00011111 11111111 11111111 11111111
    
    // 线程池状态
    private static final int RUNNING = -1 << COUNT_BITS;        // 11100000 00000000 00000000 00000000
    private static final int SHUTDOWN = 0 << COUNT_BITS;        // 00000000 00000000 00000000 00000000
    private static final int STOP = 1 << COUNT_BITS;            // 00100000 00000000 00000000 00000000
    private static final int TIDYING = 2 << COUNT_BITS;         // 01000000 00000000 00000000 00000000
    private static final int TERMINATED = 3 << COUNT_BITS;      // 01100000 00000000 00000000 00000000

    /**
    * 工作线程集合.
    */
    private final HashSet<Worker> workers = new HashSet<Worker>();

    /**
     * 任务队列, 保存已经提交但尚未被执行的线程集合
     */
    private final BlockingQueue<Runnable> workQueue;
}
```


## 提交任务

```java
public void execute(Runnable command) {
    if (workerCountOf(c) < corePoolSize) then
        addWorker();
    
    if workQueue.offer() then
    else if !addWorker() then
        执行拒绝策略;    
}
```

## 添加任务到线程池
```java
private boolean addWorker(Runnable firstTask, boolean core) {
    创建worker w;
    添加到workers;
    启动线程，w.runWorker();
}
```

## 执行任务

```java
final void runWorker(Worker w) {
    task = w.firstTask;
    for(;;){
        不停的获取任务(null, task);
        task.run();        
    }
}
```

## 获取任务、超时
```java
private Runnable getTask() {
    boolean timed = allowCoreThreadTimeOut || wc > corePoolSize;
    Runnable r = timed ?
                    workQueue.poll(keepAliveTime, TimeUnit.NANOSECONDS) :
                    workQueue.take();
    return r;
}
```

## 任务异常、线程中断

[Java多线程进阶（四十）—— J.U.C之executors框架：ThreadPoolExecutor](https://segmentfault.com/a/1190000016629668)


