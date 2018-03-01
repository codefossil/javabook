# Java

标签（空格分隔）： 未分类

---

程序语言设计
语言的本质
信息系统
类型系统
流程控制机制
代码组织机制

写起来舒服，读起来容易，管起来方便
http://www.cppblog.com/vczh/archive/2013/04/27/199765.html

## 1. 基本语法 ##

static
final
transient
volatile及其底层实现原理
clone
异常和出错

## 2. 集合 ##
List, Map, Set的底层原理实现
CopyOnWrite容器
ConcurrentHashMap

 - 锁分段技术
 - 读是否要加锁
 - 迭代器的一致性

## 3. 设计模式 ##
单一职责原则
开放封闭原则
里氏替换原则
最少知识原则
接口隔离原则
依赖倒置原则

常用的设计模式
设计模式UML图
类似AOP，是设计模式能够解决的吗


## 5. IO ##
阻塞/非阻塞IO
同步/异步IO
多路复用IO
NIO的三大组成
Netty
selector/poll/epoll/iocp/kqueue

## 6. JDK源码 ##
java.util.concurrent所有代码
string.hashCode源码
list/map/set源码
ReentrantLock/AQS源码
AtomicInteger原理/CAS机制
线程池原理
object源码

## 7. 框架 ##
Spring初始化bean
bean销毁
mybatis$和#的区别

###依赖注入###

###AOP原理###
面向切面编程


https://en.wikipedia.org/wiki/Aspect-oriented_programming
https://www.ibm.com/developerworks/cn/java/j-aop/index.html
https://zhuanlan.zhihu.com/p/24565766
http://www.importnew.com/26951.html
http://kubicode.me/2015/07/30/Java%20Base/Java-AOP-Study/

IOC原理

HTTP的携带状态问题

 - 锁分段技术
 - URL参数
 - cookies
 - session

SpringSession默认用cookie保存和传递sessionid

 - 共享
 - 复制
 - 一致性

## 8. 数据库 ##
事务管理
事务隔离级别
数据库连接池
c3p0/druid
JDBC
Mybatis
union/union all区别
left join
索引的分类/区别
性能优化

## 9. 数据结构和算法 ##
AVL
红黑
索引的实现
collection.sort实现

## 10. java虚拟机 ##
内存分布
GC算法
类加载器
happens-before规则

## 11. web ##
系统各种连接数限制
数据库连接
操作系统连接数
tomcat连接数

Servlet
分布式session
filter/servlet/listener
soa/rpc
面向服务体系
大型分布式架构

## 12. 项目管理 ##
团队协作工具
项目管理工具
项目版本工具
如何测试
如何上线

5，技术实现细节，独挡一面
10， 行业认识，技术认识，TOP，系统架构
可以不使用语言，但是不能不关心语言的演进



