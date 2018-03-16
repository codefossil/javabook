#object header#
oopDesc -> object header(mark + klass)
mark=hashcode/sync/gc

http://openjdk.java.net/groups/hotspot/docs/HotSpotGlossary.html
https://www.javamex.com/tutorials/memory/object_memory_usage.shtml
https://gist.github.com/arturmkrtchyan/43d6135e8a15798cc46c
http://arturmkrtchyan.com/

对象拷贝

#hashing
##hashcode
> 用来缩小查找范围

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