#object header#
oopDesc -> object header(mark + klass)
mark=hashcode/sync/gc

http://openjdk.java.net/groups/hotspot/docs/HotSpotGlossary.html
https://www.javamex.com/tutorials/memory/object_memory_usage.shtml
https://gist.github.com/arturmkrtchyan/43d6135e8a15798cc46c
http://arturmkrtchyan.com/

对象拷贝

##IEEE 754
```java
< System.out.println(Integer.toBinaryString(Float.floatToIntBits(0.1f)));
> 111101110011001100110011001101

< System.out.println(1e16 + 1.0 - 1e16);
> 0.0
```
>就像十进制无法精确表达π和e一样，二进制也无法精确表达小数；

精确度
>假如double能够精确表达的离散点记为S，不能表达的记为s'，s'>>s

精度控制
微分/差分方程稳定性

http://justjavac.com/codepuzzle/2012/11/11/codepuzzle-float-who-stole-your-accuracy.html
https://people.eecs.berkeley.edu/~wkahan/
https://docs.oracle.com/cd/E19957-01/806-3568/ncgTOC.html
https://en.wikipedia.org/wiki/IEEE_754-1985#Comparing_floating-point_numbers
http://0.30000000000000004.com/

#hashing
##hashcode
> 用来缩小查找范围

https://www.jitendrazaa.com/blog/java/what-is-the-need-to-override-hashcode-and-equals-method/
###默认实现
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
https://srvaroa.github.io/jvm/java/openjdk/biased-locking/2017/01/30/hashCode.html
http://g.oswego.edu/

###原生wrapper实现
```cpp
//test\java\lang
check(    new Long(x).hashCode() == (int)((long)x ^ (long)x>>>32));
check(Integer.valueOf(x).hashCode() == x);
//...
```

##0x61c88647
```java
//share\classes\java\lang\ThreadLocal.java
private static final int HASH_INCREMENT = 0x61c88647;
nextHashCode.getAndAdd(HASH_INCREMENT);
```