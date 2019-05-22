# 通用架构设计
microservice/SOA/Lambda Architecture  

[Patterns of Enterprise Application Architecture, 2003](https://book.douban.com/subject/1230559/)  
[Building Microservice](https://book.douban.com/subject/25881698/)  

https://lethain.com/digg-v4-architecture-process/  
[程序员的呐喊](https://book.douban.com/subject/25884108/)  
https://www.w3.org/DesignIssues/  
https://firstround.com/review/the-rewards-of-creator-driven-cultures-and-the-engineers-that-can-deliver-them/  

分布式ID发号器、feed 系统、缓存系统、推荐系统、抢票系统  
社区类服务架构、云服务架构、O2O  

[分布式Redis架构设计, 2015](https://mp.weixin.qq.com/s?__biz=MzAwMDU1MTE1OQ==&mid=208733458&idx=1&sn=691bfde670fb2dd649685723f7358fea)  
[亿级用户下的新浪微博平台架构](https://www.infoq.cn/article/weibo-platform-archieture)  
[Azure Architecture Center](https://docs.microsoft.com/en-us/azure/architecture/)  
[AWS Architecture Center](https://aws.amazon.com/architecture)  

# 企业级架构设计

## 用户系统
三用户模型

http://doc.cocolian.cn/essay

## 支付系统
第三方支付
优惠券
积分

## 电商服务架构
商品管理
订单系统
下单流程
库管  
[TableStore实战：亿量级订单管理解决方案](https://yq.aliyun.com/articles/656196?spm=a2c4e.11154837.920241.5.464642b2YuhDE6)
[分库分表技术演进](https://mp.weixin.qq.com/s/3ZxGq9ZpgdjQFeD2BIJ1MA)

## 即时消息
消息推送
IOT设备MQTT

## 身份认证
用户系统
SSO
登录系统
权限系统

# 实战工具箱
## web框架/容器
servlet/tomcat
依赖注入
AOP原理
spring/springmvc
Spring初始化bean  
bean销毁  
面向切面编程
SpringSession默认用cookie保存和传递sessionid

https://docs.spring.io/spring/docs/current/spring-framework-reference/overview.html\#spring-introduction  
[https://en.wikipedia.org/wiki/Aspect-oriented\_programming](https://en.wikipedia.org/wiki/Aspect-oriented_programming)  
[https://www.ibm.com/developerworks/cn/java/j-aop/index.html](https://www.ibm.com/developerworks/cn/java/j-aop/index.html)  
[https://zhuanlan.zhihu.com/p/24565766](https://zhuanlan.zhihu.com/p/24565766)  
[http://www.importnew.com/26951.html](http://www.importnew.com/26951.html)  
[http://kubicode.me/2015/07/30/Java Base/Java-AOP-Study/](http://kubicode.me/2015/07/30/Java Base/Java-AOP-Study/)

## 远程通信
dubbo/thrift

## 持久化框架
jdbc/mybatis
mybatis$和\#的区别
job框架/shiro

## 消息队列
rabbitmq
SQS，对性能无太大要求时，做简单队列, availability超好 

## 数据流

confluent  
[Kafka: The Definitive Guide](https://book.douban.com/subject/26828527/)  
https://engineering.linkedin.com/distributed-systems/log-what-every-software-engineer-should-know-about-real-time-datas-unifying  
https://www.infoq.cn/article/2018/01/confluent-kafka-data  

aws  
[Kinesis](https://aws.amazon.com/cn/kinesis/)

elastic  
https://zturn.cc/elkbook/

## 大数据
http://www.voidcn.com/article/p-biggriil-bhz.html

## 工作流/规则引擎

## 数据搜索
分词器
索引规则

webhook
http://progrium.com/blog/2007/05/03/web-hooks-to-revolutionize-the-web/





