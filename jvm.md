内存分布
GC算法

#java.lang.ref包

[动机](https://github.com/openjdk-mirror/jdk7u-jdk/blob/master/src/share/classes/java/lang/ref/package.html)和[代码](https://github.com/openjdk-mirror/jdk7u-jdk/tree/master/src/share/classes/java/lang/ref)

```java
func(){
  String str = new String() //强引用
  //...
}
// 函数调用完，str从栈中删除，对象不存在引用，就会被gc
```
**强引用（默认）** 与对象生命周期强绑定

但是大家对gc回收对象有不同程度的需求，因此jdk1.2后增加以下**3种更弱**的引用类型，更加精确控制gc。

##软引用
```java
//share\classes\sun\nio\cs\AbstractCharsetProvider.java
Map<String,SoftReference<Charset>> cache;

SoftReference<Charset> sr = cache.get(csn);
if (sr != null) {
    Charset cs = sr.get();
    if (cs != null)
        return cs;
}
```
当堆中基本全是强引用，gc无法腾出更多的空间而抛出OOM之前，最后一招软引用可达的对象会被gc。**因此软引用适合非重要业务，对象过度占用内存**。比如各种cache使用。

##弱引用
```java
// 原理
WeakReference<Object> ref = new WeakReference<>(obj, queue);
obj = null;
System.gc(); // obj被gc了，ref.get()为null;

// 例子
WeakHashMap<TCPEndPoint, User> clientList = new WeakHashMap<>(); // 当EndPoint被回收时，对应的User被自动设置为null
```
每个对象可以有多个引用类型的组合，当多个**对象有依赖关系时**（比如socket被回收，与之对应的客户端信息需要关联删除），可以非常优雅地实现自动依赖回收

##虚引用
```java
//share\classes\sun\java2d\Disposer.java
ref = new PhantomReference(target, queue);
ref.get(); // 永远返回null
```
使用场景多是profiler/同弱引用

##引用队列与通知
```java
//share\classes\java\lang\ref\Reference.java
private static Reference pending = null;
private static class ReferenceHandler extends Thread {
```
后面2种引用类型基本无法直接使用，使用场景也基本是gc后通知。每个jvm维持一个线程负责一个pending单向列表保存回收对象的引用。

类加载器
transient
clone
异常和出错


