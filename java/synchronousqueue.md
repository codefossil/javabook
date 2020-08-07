# 动机
双排队队列

# 目标


# 解决方案


# 缺陷


# 细节

## 非公平模式内部栈

![](https://www.javazhiyin.com/wp-content/uploads/2019/09/java2-1569407005.png)

```java
// FILO 内部数据结构
static final class TransferStack<E> extends Transferer<E> {
      	/** 表示这是个请求节点 */
        static final int REQUEST    = 0;
        /** 数据节点 */
        static final int DATA       = 1;
        /** 匹配成功后设置的节点 */
        static final int FULFILLING = 2;
                
        static final class SNode {
            volatile SNode next;        // next node in stack
            volatile SNode match;       // the node matched to this
            volatile Thread waiter;     // to control park/unpark
            Object item;                // data; or null for REQUESTs
            int mode;  //0表示请求节点，1表示数据节点
        }            
        //栈顶部指针
        volatile SNode head;
```

```java
// 找到配对线程
E TransferStack.transfer(E e, boolean timed, long nanos) {
    // 判断生产者还是消费者        
    int mode = (e == null) ? REQUEST : DATA;

    for(;;){
        SNode h = head;        
        if h.mode != mode then   
            入栈s且s.mode |= FULFILLING;     
            唤醒配对线程
            一对匹配节点同时出栈
            return mode == REQUEST ? m.item : s.item;
        end
        else 
            入栈
            挂起当前线程
    }
}
```

## 公平模式内部队列


```java
// FIFO内部结构
static final class TransferQueue<E> extends Transferer<E> {
        
        static final class QNode {
        	//下一个节点
            volatile QNode next;          // next node in queue
            //数据
            volatile Object item;         // CAS'ed to or from null
            //等待线程
            volatile Thread waiter;       // to control park/unpark
            //判断数据类型
            final boolean isData;
        }

        /** 头指针 */
        transient volatile QNode head;
        /** 尾指针 */
        transient volatile QNode tail;
		
        transient volatile QNode cleanMe;		
}
```

```java
// 找到配对线程
E TransferQueue.transfer(E e, boolean timed, long nanos) {
    // 判断生产者还是消费者        
    boolean isData = (e != null);

    for(;;){
        QNode t = tail;
        QNode h = head;

        if t.isData != isData then        
            QNode m = h.next;
            m.item = e;
            出队列首部
            唤醒线程m
            return m.item!=null ? m.item : e;
        end
        else
            入队列尾
            挂起当前线程 
            
    }
}
```

# 性能



[Nonblocking Concurrent Data Structures with Condition Synchronization, Scherer04, DISC](http://www.cs.rochester.edu/u/scott/papers/2004_DISC_dual_DS.pdf)

[SynchronousQueue原理详解-公平模式](https://www.cnblogs.com/dwlsxj/p/Thread.html)