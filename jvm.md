https://en.wikipedia.org/wiki/Java_version_history  
[The Java® Language Specification](https://docs.oracle.com/javase/specs/jls/se8/html/index.html)  
[The Java® Virtual Machine Specification](https://docs.oracle.com/javase/specs/jvms/se8/html/index.html)  

[Java Platform, Standard Edition Tools Reference](https://docs.oracle.com/javase/9/tools/tools-and-command-reference.htm)

[Java Platform Standard Edition 8 Documentation](https://docs.oracle.com/javase/8/docs/)

[Programming Languages Research at UMD](https://plum-umd.github.io/projects/)  

[Software Analysis and Testing](https://www.cis.upenn.edu/~mhnaik/edu/cis700/index.html#reading)  

https://www.cc.gatech.edu/~harrold/6340/cs6340_fall2009/

# 类型系统
[JLS - Two type system](https://docs.oracle.com/javase/specs/jls/se7/html/jls-4.html)  
https://softwareengineering.stackexchange.com/questions/203970/when-to-use-primitive-vs-class-in-java  

[Effective Java](https://book.douban.com/subject/27047716/)  

# 内存模型和多核处理器
java是第一个在编程语言的层面规范内存访问模型。  

[JSR 133 (Java Memory Model) FAQ](http://www.cs.umd.edu/users/pugh/java/memoryModel/jsr-133-faq.html)  
什么是JAVA内存模型，为什么需要这个，C/C++为什么没有  

[The JSR-133 Cookbook for Compiler Writers](http://gee.cs.oswego.edu/dl/jmm/cookbook.html)  

[discussions about java memory model, UMD](http://www.cs.umd.edu/users/pugh/java/memoryModel/)  

[chapter 17 Memory Model, jls](https://docs.oracle.com/javase/specs/jls/se8/html/jls-17.html#jls-17.4)   

# 对象

![](https://img-blog.csdnimg.cn/20190115141050902.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1NDRE5fQ1A=,size_16,color_FFFFFF,t_70)

# 垃圾收集

![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCE98bf46481bc887a843546cbb68eb9c3d/123)

[The Garbage Collection Handbook, jones2011](https://book.douban.com/subject/6809987/)

[深入理解Java虚拟机, 2013](https://book.douban.com/subject/24722612/)  

[HotSpot JVM Performance Tuning Guidelines](https://ionutbalosin.com/2020/01/hotspot-jvm-performance-tuning-guidelines/#jit_tiered_mode)

[The Java HotSpot Performance Engine Architecture](https://www.oracle.com/technetwork/java/whitepaper-135217.html)

safepoint  
http://xiao-feng.blogspot.com/2008/01/gc-safe-point-and-safe-region.html  
http://blog.ragozin.info/2012/10/safepoints-in-hotspot-jvm.html  
https://shipilev.net/jvm/anatomy-quarks/22-safepoint-polls/  
http://psy-lob-saw.blogspot.com/2015/12/safepoints.html  


http://openjdk.java.net/groups/hotspot/docs/HotSpotGlossary.html  
https://www.javamex.com/tutorials/memory/object\_memory\_usage.shtml  
https://gist.github.com/arturmkrtchyan/43d6135e8a15798cc46c  
http://arturmkrtchyan.com/  


# 同步、锁优化

```txt
|--------------------|--------------------------------------------------------------------------------------------------------------|
|        State       |                                            Object Header (96 bits)                                           |
|--------------------|--------------------------------------------------------------------------------|-----------------------------|
|                    |                                  Mark Word (64 bits)                           |    Klass Word (32 bits)     |
|--------------------|--------------------------------------------------------------------------------|-----------------------------|
|       Normal       | unused:25 | identity_hashcode:31 | cms_free:1 | age:4 | biased_lock:1 | lock:2 |    OOP to metadata object   |
|--------------------|--------------------------------------------------------------------------------|-----------------------------|
|       Biased       | thread:54 |       epoch:2        | cms_free:1 | age:4 | biased_lock:1 | lock:2 |    OOP to metadata object   |
|--------------------|--------------------------------------------------------------------------------|-----------------------------|
| Lightweight Locked |                         ptr_to_lock_record                            | lock:2 |    OOP to metadata object   |
|--------------------|--------------------------------------------------------------------------------|-----------------------------|
| Heavyweight Locked |                     ptr_to_heavyweight_monitor                        | lock:2 |    OOP to metadata object   |
|--------------------|--------------------------------------------------------------------------------|-----------------------------|
|    Marked for GC   |                                                                       | lock:2 |    OOP to metadata object   |
|--------------------|--------------------------------------------------------------------------------|-----------------------------|
```

[Lock optimizations on the HotSpot VM, pool, 2014](https://www.semanticscholar.org/paper/Lock-optimizations-on-the-HotSpot-VM-Pool/edf954412a9b1ce955bea148199f325759779540)

[Evaluating and improving biased locking in the HotSpot virtual machine, LARSSON2014, MS Thesis](http://www.diva-portal.se/smash/get/diva2:754541/FULLTEXT01.pdf)  

[thin-lock-featherweight-synchronization-for-java-bacon98-sigplan](https://dl.acm.org/doi/10.1145/989393.989452)  

[Building FIFO and Priority-Queuing Spin Locks from Atomic Swap, craig93](http://citeseerx.ist.psu.edu/viewdoc/download;jsessionid=91D705288CA1399F51F38B2B50598A34?doi=10.1.1.38.7889&rep=rep1&type=pdf)


## 同步框架
[The java.util.concurrent Synchronizer Framework](/aqs.md)  
java5引入的最牛皮的同步器框架底层设计和分析。（结合源码和网友的分析）  

[Java Fork/Join, 2000](http://gee.cs.oswego.edu/dl/papers/fj.pdf)  
[Future, 1977](http://home.pipeline.com/~hbaker1/Futures.html)  


## synchronized

轻量级/thin-lock
>线程通过spin检查（减少fat-lock用户和内核态的切换）

``` cpp
>share/vm/runtime/synchronizer.cpp
00 has_locker()
```

重量级/fat-lock
>线程通过park/pending操作，让出CPU等待唤醒

```cpp
//os/windows/vm/os_windows.cpp
00 inflating
10 has_monitor()
objectMonitor = mark->monitor()
park: 调用系统的WaitForSingleObject等待event对象，不断尝试CAS
```

重入锁/偏向锁
> 线程通过线程ID检查（减少thin-lock的spin）  

当竞争时，需要撤销偏向锁

# 集合

[Collections Framework Overview](https://docs.oracle.com/javase/8/docs/technotes/guides/collections/overview.html)  
[Outline of the Collections Framework](https://docs.oracle.com/javase/8/docs/technotes/guides/collections/reference.html)


# 运算符优先级
https://docs.oracle.com/javase/tutorial/java/nutsandbolts/operators.html

# clone对象拷贝

# java.lang.ref包

[动机](https://github.com/openjdk-mirror/jdk7u-jdk/blob/master/src/share/classes/java/lang/ref/package.html)和[代码](https://github.com/openjdk-mirror/jdk7u-jdk/tree/master/src/share/classes/java/lang/ref)

```java
func(){
  String str = new String() //强引用
  //...
}
// 函数调用完，str从栈中删除，对象不存在引用，就会被gc
```
**强引用（默认）** 与对象生命周期强绑定

但是大家对gc回收对象有不同程度的需求，因此jdk1.2后增加以下**3种更弱**的引用类型，更加精确地与gc交互。

## 软引用
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

## 弱引用
```java
// 原理
WeakReference<Object> ref = new WeakReference<>(obj, queue);
obj = null;
System.gc(); // obj被gc了，ref.get()为null;

// 例子
WeakHashMap<TCPEndPoint, User> clientList = new WeakHashMap<>(); // 当EndPoint被回收时，对应的User被自动设置为null
```
每个对象可以有多个引用类型的组合，当多个**对象有依赖关系时**（比如socket被回收，与之对应的客户端信息需要关联删除），可以非常优雅地实现自动依赖回收

## 虚引用
```java
//share\classes\sun\java2d\Disposer.java
ref = new PhantomReference(target, queue);
ref.get(); // 永远返回null
```
使用场景多是profiler/同弱引用

## 引用队列与通知
```java
//share\classes\java\lang\ref\Reference.java
private static Reference pending = null;
private static class ReferenceHandler extends Thread {
```
后面2种引用类型基本无法直接使用，使用场景也基本是gc后通知。为了可用，jvm维持一个线程负责一个pending单向列表保存回收对象的引用。

# 数与码
10根手指数数，最习惯十进制
0-9就是码，也就是我们采用最少的符号，通过编码，完全表示所有数
进位是为了递归表示无限多的更大的数

## 负数和补码
- 原码。为了进行计算，需要引入符号，这就是二进制的原码，这也是最直观的编码方式
- 补码。为了简化加法器，负数编码成补码
- 移码。是符号位取反的一种补码。

## IEEE 754

```java
< System.out.println(Integer.toBinaryString(Float.floatToIntBits(0.1f)));
> 111101110011001100110011001101

< System.out.println(1e16 + 1.0 - 1e16);
> 0.0
```

> 就像十进制无法精确表达π和e一样，二进制也无法精确表达小数；
70’s的时候，程序员需要处理不同的浮点数模型。

https://people.eecs.berkeley.edu/~wkahan/ieee754status/754story.html
## 数字精确表示

**内存布局**

|存储类型 | 符号 | 指数（缩放） | 尾数（精度）|
|- | - | --- | ----|
|单精度 | 1bit（`0`） | 8bits(`01111011`) | 23bits(`10011001100110011001101`), 2*2^23=1.6777216e7(保证有7位有效数字)|
|双精度 | 1bit | 11bits | 52bits, 2*2^52=9.007199254740992e15(保证15位有效数字)|

> 同样是32位的整型，最大值是2^31-1=2.147483647e9，而float最大是3.4028235e38，可以想象有99%的小数是无法准确表示。

```java
Float f = 0.1f;
int base = 2;
System.out.println("float: " + f);
System.out.println("binary: " + Integer.toBinaryString(Float.floatToIntBits(f)));
System.out.println("exp: " + (Integer.parseInt("01111011", 2) - 127));
System.out.println("m: " + "10011001100110011001101");
double d = 0 * Math.pow(base, 0) + 0 * Math.pow(base, -1) + 0 * Math.pow(base, -2) + 0 * Math.pow(base, -3) +
        1 * Math.pow(base, -4) + 1 * Math.pow(base, -5);
System.out.println("1.100110011*2^(-4)=0.00011b=" + d);
```

http://tool.oschina.net/hexconvert
http://www.binaryconvert.com/
### 精度控制  
微分/差分方程稳定性

http://justjavac.com/codepuzzle/2012/11/11/codepuzzle-float-who-stole-your-accuracy.html  
https://people.eecs.berkeley.edu/~wkahan/  
https://docs.oracle.com/cd/E19957-01/806-3568/ncgTOC.html 
https://en.wikipedia.org/wiki/IEEE\_754-1985\#Comparing\_floating-point\_numbers
http://0.30000000000000004.com/


# hashcode

> 不是用来唯一判定对象本身，而是用来缩小查找范围

约定
- 如果equal()返回true，2个对象hashCode()必须相等
- 如果equal()返回false，对于hashCode()没有规定

https://www.jitendrazaa.com/blog/java/what-is-the-need-to-override-hashcode-and-equals-method/

## 默认实现

```cpp
//hotspot\src\share\vm\runtime\synchronizer.cpp
//0-jdk6/7
value = os::random();

//1
intptr_t addrBits = intptr_t(obj) >> 3 ;

//5-jdk8/9
//Marsaglia's xor-shift
```

https://srvaroa.github.io/jvm/java/openjdk/biased-locking/2017/01/30/hashCode.html  
http://g.oswego.edu/

## 原生wrapper实现

```cpp
//test\java\lang
check(    new Long(x).hashCode() == (int)((long)x ^ (long)x>>>32));
check(Integer.valueOf(x).hashCode() == x);
//...
return floatToIntBits(value);
```

## 0x61c88647

```java
//share\classes\java\lang\ThreadLocal.java
private static final int HASH_INCREMENT = 0x61c88647;
nextHashCode.getAndAdd(HASH_INCREMENT);
```

# 反汇编
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





