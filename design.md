# 方法论
* 定义问题
解决/不解决什么问题？谁的问题？
* 分析问题
收集信息/关键路径/简化
* 解决问题
根据现有的时间/预算/知识/复杂度，利用最佳实践、技术、框架、工具、设备（工程/学习能力）

**整个过程就是一个动态规划问题**

# 康威定律
软件系统架构，反映了公司的组织架构  
[架构漫谈](https://www.infoq.cn/article/an-informal-discussion-on-architecture-part01)

# worse is better
KISS和正确之间需要平衡

[程序员的呐喊](https://book.douban.com/subject/25884108/)  
[worse is better](http://dreamsongs.com/WorseIsBetter.html)  
[rise of wib](http://dreamsongs.com/RiseOfWorseIsBetter.html)  
https://blog.codinghorror.com/worse-is-better/  
[wib-example](https://stackoverflow.com/questions/471544/worse-is-better-is-there-an-example)  

# 架构视图
* 开发 
流程：源码 -> 源码仓库 -> 发布系统  
测试：单元测试 -> 系统测试 -> QA -> 预发布 -> 线上  
组件：配置中心/链路追踪/统一日志/消息（基础架构怎么做）  
输出：产品展示/服务交互API

* 物理（SRE怎么做）  
网络/计算/存储/容器  
可扩展/高可用/高性能  
输出：基础设施 

* 逻辑（问题怎么解）  
问题域分解/服务功能划分  
输出：类/对象图、需求分析  

* 过程（数据怎么走）  
接口/信息流/容错  
输出：交互图、时序图  

* 场景（验证能否走通）
突出系统间依赖  
输出：用例

https://www.w3.org/DesignIssues/  
https://firstround.com/review/the-rewards-of-creator-driven-cultures-and-the-engineers-that-can-deliver-them/  
https://www.ibm.com/developerworks/cn/rational/r-4p1-view/index.html  

控制复杂度  
单一职责原则  
开放封闭原则  
里氏替换原则  
最少知识原则  
接口隔离原则  
依赖倒置原则

CQRS and event sourcing  

常用的设计模式  
类似AOP，是设计模式能够解决的吗

# Immutable

瀑布->Agile->DevOps演变  
规模估算  
大规模用户  
大数据量  
流量切换 sla  
服务依赖/状态/降级  
发布和灰度  
容量规划，扩容和缩容  
Flume vs kafka(HA)  

creator driven  
DDD/TDD/BDD/microservice/SOA/CQRS/DCI/Lambda Architecture/Functional Programming

发号器、设计 feed 系统、设计缓存系统、设计推荐系统、登录系统、抢票系统  
Xpress， 解LP MIP  

Kafka/Kinesis，分布式队列，分布式数据收集  
SQS，对性能无太大要求时，做简单队列, availability超好  

无状态服务器  
分布式队列  
https://simplicable.com/new/coding-principles  