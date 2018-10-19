#方法论
* 定义问题
解决/不解决什么问题？谁的问题？
* 分析问题
收集信息/关键路径/简化
* 解决问题
根据现有的时间/预算/知识/复杂度，利用最佳实践、技术、框架、工具、设备（工程/学习能力）

**整个过程就是一个动态规划问题**

https://www.w3.org/DesignIssues/
控制复杂度
单一职责原则  
开放封闭原则  
里氏替换原则  
最少知识原则  
接口隔离原则  
依赖倒置原则

常用的设计模式
类似AOP，是设计模式能够解决的吗

规模估算
大规模用户
大数据量
流量切换 sla
服务依赖/状态/降级
发布和灰度
扩容和缩容
Flume vs kafka(HA)
zookeeper

DDD/TDD/BDD/microservice/SOA/CQRS/DCI/Lambda Architecture/Functional Programming

发号器、设计 feed 系统、设计缓存系统、设计推荐系统、登录系统、抢票系统
Xpress， 解LP MIP

Kafka/Kinesis，分布式队列，分布式数据收集
SQS，对性能无太大要求时，做简单队列, availability超好


# spring

Spring初始化bean  
bean销毁  
mybatis$和\#的区别

## 依赖注入

## AOP原理

面向切面编程

[https://en.wikipedia.org/wiki/Aspect-oriented\_programming](https://en.wikipedia.org/wiki/Aspect-oriented_programming)  
[https://www.ibm.com/developerworks/cn/java/j-aop/index.html](https://www.ibm.com/developerworks/cn/java/j-aop/index.html)  
[https://zhuanlan.zhihu.com/p/24565766](https://zhuanlan.zhihu.com/p/24565766)  
[http://www.importnew.com/26951.html](http://www.importnew.com/26951.html)  
[http://kubicode.me/2015/07/30/Java Base/Java-AOP-Study/](http://kubicode.me/2015/07/30/Java Base/Java-AOP-Study/)

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

servlet与容器

dubbo
akka

https://docs.spring.io/spring/docs/current/spring-framework-reference/overview.html\#spring-introduction

