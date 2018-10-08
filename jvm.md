# 内存分布
# object header

oopDesc -> object header\(mark + klass\)  
mark=hashcode/sync/gc

http://openjdk.java.net/groups/hotspot/docs/HotSpotGlossary.html
https://www.javamex.com/tutorials/memory/object\_memory\_usage.shtml
https://gist.github.com/arturmkrtchyan/43d6135e8a15798cc46c  
http://arturmkrtchyan.com/

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
后面2种引用类型基本无法直接使用，使用场景也基本是gc后通知。为了可用，jvm维持一个线程负责一个pending单向列表保存回收对象的引用。

#数与码
10根手指数数，最习惯十进制
0-9就是码，也就是我们采用最少的符号，通过编码，完全表示所有数
进位是为了递归表示无限多的更大的数

##负数和补码
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
##数字精确表示

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
###精度控制  
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

#GC算法



#类加载器
transient

#异常和出错


