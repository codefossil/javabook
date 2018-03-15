内存分布
GC算法
#引用
```java
//share\classes\java\lang\ref\Reference.java
private static Reference pending = null;
private static class ReferenceHandler extends Thread {
```
整个jvm维持一个线程负责一个pending单项列表gc回收入队列

##强引用
>对象生命周期与引用强绑定

##软引用
```java
//share\classes\sun\nio\cs\AbstractCharsetProvider.java
Map<String,SoftReference<Charset>> cache
```

>cached引用，完全由gc托管内存，不需要管理cached对象生命周期

##弱引用
```java
Map<WeakReference<Socket>, User> track;
```

>tracked引用，必须与一个（强引用+ReferenceQueue）关联使用。gc回收通知后，处理关联数据。

##虚引用
```java
//share\classes\sun\java2d\Disposer.java
ref = new WeakReference(target, queue);
```

> profiler引用，同弱引用使用方式，get直接返回null，完全用来评测gc性能。


类加载器
transient
clone
异常和出错


