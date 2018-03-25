# object header

oopDesc -> object header\(mark + klass\)  
mark=hashcode/sync/gc

http://openjdk.java.net/groups/hotspot/docs/HotSpotGlossary.html
https://www.javamex.com/tutorials/memory/object\_memory\_usage.shtml
https://gist.github.com/arturmkrtchyan/43d6135e8a15798cc46c  
http://arturmkrtchyan.com/

对象拷贝

##计算
##数与码
10根手指数数，最习惯十进制
0-9就是码，也就是我们采用最少的符号，通过编码，完全表示所有数
进位是为了递归表示无限多的更大的数

###负数和补码
- 原码。为了进行计算，需要引入符号，这就是二进制的原码，这也是最直观的编码方式
- 补码。为了简化加减器，负数编码成补码

## IEEE 754

```java
< System.out.println(Integer.toBinaryString(Float.floatToIntBits(0.1f)));
> 111101110011001100110011001101

< System.out.println(1e16 + 1.0 - 1e16);
> 0.0
```

> 就像十进制无法精确表达π和e一样，二进制也无法精确表达小数；


内存结构

|存储类型  | 符号 | 指数 | 尾数 | 
|----     |-----|-------|--------|
|单精度    |1       |8   |23     |
|双精度    |1       |11   |52  |

精确度

> 假如double能够精确表达的离散点记为S，不能表达的记为s'，s'&gt;&gt;s

精度控制  
微分/差分方程稳定性

http://justjavac.com/codepuzzle/2012/11/11/codepuzzle-float-who-stole-your-accuracy.html  
https://people.eecs.berkeley.edu/~wkahan/  
https://docs.oracle.com/cd/E19957-01/806-3568/ncgTOC.html 
https://en.wikipedia.org/wiki/IEEE\_754-1985\#Comparing\_floating-point\_numbers
http://0.30000000000000004.com/

# hashing

## hashcode

> 不是用来唯一判定对象本身，而是用来缩小查找范围

约定
- 如果equal()返回true，2个对象hashCode()必须相等
- 如果equal()返回false，对于hashCode()没有规定

https://www.jitendrazaa.com/blog/java/what-is-the-need-to-override-hashcode-and-equals-method/

### 默认实现

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

### 原生wrapper实现

```cpp
//test\java\lang
check(    new Long(x).hashCode() == (int)((long)x ^ (long)x>>>32));
check(Integer.valueOf(x).hashCode() == x);
//...
```

## 0x61c88647

```java
//share\classes\java\lang\ThreadLocal.java
private static final int HASH_INCREMENT = 0x61c88647;
nextHashCode.getAndAdd(HASH_INCREMENT);
```



