# 开发参考
* [tcp](https://tools.ietf.org/html/rfc793)
* [http/1.1](https://tools.ietf.org/html/rfc2616)
* [nginx](http://nginx.org/en/)
* [jdk](https://docs.oracle.com/javase/10/)
* [mysql 8.0](https://dev.mysql.com/doc/refman/8.0/en/)
* [mysql internal](https://dev.mysql.com/doc/internals/en/)
* [spring](https://docs.spring.io/spring/docs/)
* [dubbo](http://dubbo.apache.org/zh-cn/docs/user/quick-start.html)
* [maven](http://maven.apache.org/)
* [git](https://git-scm.com/docs)
* [amqp](https://www.rabbitmq.com/protocol.html)
* [cron](http://www.quartz-scheduler.org/documentation/quartz-2.x/tutorials/crontrigger.html)

# 源码
* [redis](https://github.com/antirez/redis)
* [spring](https://github.com/spring-projects/spring-framework)
* [jdk7-hotspot](https://github.com/openjdk-mirror/jdk7u-hotspot)
* [jdk7-jdk](https://github.com/openjdk-mirror/jdk7u-jdk)
* [mysql](https://github.com/mysql/mysql-server)
* [linux](https://github.com/torvalds/linux)
* [guava](https://github.com/google/guava)  
* [Azure Architecture Center](https://docs.microsoft.com/en-us/azure/architecture/)  
* [AWS Architecture Center](https://aws.amazon.com/architecture)  

# 通用企业架构设计
microservice/SOA/Lambda Architecture  

[后端架构师技术图谱](https://github.com/xingshaocheng/architect-awesome)



https://lethain.com/digg-v4-architecture-process/  
[程序员的呐喊](https://book.douban.com/subject/25884108/)  
https://www.w3.org/DesignIssues/  
https://firstround.com/review/the-rewards-of-creator-driven-cultures-and-the-engineers-that-can-deliver-them/    

[分布式Redis架构设计, 2015](https://mp.weixin.qq.com/s?__biz=MzAwMDU1MTE1OQ==&mid=208733458&idx=1&sn=691bfde670fb2dd649685723f7358fea)  
[亿级用户下的新浪微博平台架构](https://www.infoq.cn/article/weibo-platform-archieture)  

https://github.com/akullpp/awesome-java#science  
https://github.com/toutiaoio/awesome-architecture

# 工业会议

[ArchSummit](https://archsummit.infoq.cn/)   
[中国数据库技术大会](http://dtcc.it168.com/)  

# 阿里技术

[阿里中间件团队](http://jm.taobao.org/)

阿里技术参考图册  
不止代码  
阿里巴巴java开发手册  
9年双11：互联网技术超级工程  
阿里工程师的自我修养


# 基础技术

![](https://mmbiz.qpic.cn/mmbiz_png/eZzl4LXykQx32T1Fqfvo0e0icHicmMovRaQ9sdyWrBw7w4HmYD6zlbyujbkTZVKArrhVHTSVxBSURknFNr5zbTibA/640?wxfrom=5&wx_lazy=1&wx_co=1)  

![](https://mmbiz.qpic.cn/mmbiz/tMJtfgIIibWKLkJL93gDzibdJxDxJZTOy51zOzzIWL2SvgvJwBCXOkTWAIAtFjyrbPuGNKhvlTlGSia6MfuCXE7XQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

![](https://mmbiz.qpic.cn/mmbiz_png/tibrg3AoIJTvrh0Z5vHtxqYOiabwFsbaKibicuLEw0L4WdgxWajaic0GjcldZUYxnEeaUY87tzGiaJWTJVvSiaQSZVrbA/?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

![](https://mmbiz.qpic.cn/mmbiz_png/UicsouxJOkBff2mwXicG9duiaX09e9pKg4YWbZvZNJ4sTTvLj80JhAgiau2EW0mLYVMyYKIUZiaQH4D9pufqpPmVj6Q/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

[互联网后端基础设施](https://mp.weixin.qq.com/s/TSJ0QN2xJI-Tv_HHp_hgcg)  

https://mp.weixin.qq.com/s/bsuveX-E6E2fKZ24mj03nQ

https://mp.weixin.qq.com/s/CZstkP51T8vte6P7u-Ni1A

https://help.aliyun.com/product/29500.html?spm=a2c4g.11186623.6.540.1c66465dK4LT3j

## 接入、负载均衡  
https://help.aliyun.com/document_detail/27544.html?spm=a2c4g.11186623.6.546.2bb11d42IuEAbG  

## 服务治理、RPC

## 消息队列

![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCEd3bcffef5bb5a2be0d9301a768fde1e5/61)

https://mp.weixin.qq.com/s/Rjeyv-ZSLc10tdAnuKZ21w

http://rocketmq.apache.org/docs/motivation/  
http://rocketmq.apache.org/rocketmq/how-to-support-more-queues-in-rocketmq/  
https://engineering.linkedin.com/distributed-systems/  log-what-every-software-engineer-should-know-about-real-time-datas-unifying  
https://www.confluent.io/blog/how-choose-number-topics-partitions-kafka-cluster/  


rabbitmq  
SQS，对性能无太大要求时，做简单队列, availability超好 



## 数据库、搜索引擎

![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCEd5e21917088ed4ea8750da1541bf7f56/59)

|名称|类型|QPS单机|QPS集群|TPS|RT|存储|scan|get|join|
|--|--|--|--|--|--|--|--|--|--|
|redis|内存|100K+|1M+||1ms|TB
|HBase|列族|-|?|10M+|1ms|PB|more|less
|Cassandra|列族|-|?|10M+|1ms|PB|less|more
|Hive|列族|-|?|10M+|1ms|PB|less|more
|Greeplum|列式|-|?|||||
|S3|对象|-||||||
|MongoDB|文档||||||x|x|
|SQL|行|100K+|-|||GB|x|x|x
|?|图|100K+|-|||GB|x|x|x
|?|时序|100K+|-|||GB|x|x|x

https://www.martinfowler.com/bliki/PolyglotPersistence.html
http://mysql.rjweb.org/doc.php/limits
https://dev.mysql.com/doc/mysql-reslimits-excerpt/5.6/en/limits.html

http://www.voidcn.com/article/p-biggriil-bhz.html



## 统一调度、容器

![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCE010efe82339b9336a784ec3a409ce36e/55)


https://www.datadoghq.com/docker-adoption


## 分布式应用配置

https://help.aliyun.com/document_detail/59957.html?spm=a2c4g.11174283.6.545.5c07613600nrB8

## 工作流/规则引擎

[美团酒旅实时数据规则引擎应用实践](https://tech.meituan.com/2018/04/19/hb-rt-operation.html)

[复杂风控场景下，如何打造一款高效的规则引擎](https://tech.meituan.com/2020/05/14/meituan-security-zeus.html)

[从0到1：构建强大且易用的规则引擎](https://tech.meituan.com/2017/06/09/maze-framework.html)

webhook  
http://progrium.com/blog/2007/05/03/web-hooks-to-revolutionize-the-web/


https://sites.google.com/a/brown.edu/ugur-cetintemel/
https://data1030.github.io/
https://www.linkedin.com/pulse/big-data-velocity-plain-english-john-ryan/
https://www.allthingsdistributed.com/2018/06/purpose-built-databases-in-aws.html




# 核心基础服务

![](https://image.woshipm.com/wp-files/2017/02/eaiRbTvRmooOzRJY9va4.png)

http://www.woshipm.com/pd/586436.html  
[中国互联网业务研发体系架构指南](https://blog.csdn.net/Ture010Love/article/details/104381157)

分布式ID发号器、feed 系统、缓存系统、推荐系统、抢票系统  
社区类服务架构、云服务架构、O2O

[分布式、服务化的ERP系统架构设计](https://www.cnblogs.com/liuche/p/7955462.html)

## 推送系统

|名称|集群数量|CPU|内存|存储|网络|单机|集群长连接|消息下发|
|--|--|--|--|--|--|--|--|--|
|360push服务|9集群，400物理机，3000实例|-|128GB|-|-|800K长连接，20K QPS|10M|10M/分钟，百亿/天,
|京东云消息|-|-|-|-|-|1.18M长连接|-|-


[Netty 百万级推送服务设计要点](https://www.infoq.cn/article/netty-million-level-push-service-design-points)  


## 用户系统

1. 账户
三用户模型
http://doc.cocolian.cn/essay

## 交易系统

## 支付系统

## 营销系统

![](https://pic2.zhimg.com/v2-98839cd995c6f3e8190455c01dfa49c5_r.jpg)


1. 点券
http://www.woshipm.com/pd/913433.html
http://www.woshipm.com/pd/836586.html
https://juejin.im/post/5b06851251882538b82c3e1f
https://www.jianshu.com/p/bc56e676298f


## 身份认证
SSO  
登录系统  
权限系统

## 商品系统
商品管理  
订单系统  
下单流程  
库管  

[TableStore实战：亿量级订单管理解决方案](https://yq.aliyun.com/articles/656196?spm=a2c4e.11154837.920241.5.464642b2YuhDE6)  

秒杀系统  
https://mp.weixin.qq.com/s/y2XptJ3pTaMl3ogYQ6KjRg

https://mp.weixin.qq.com/s/RRRFkEUba0HHaJr5-EUF2Q

## 物流系统

## 计数系统


# 数据平台

## BI/经分系统

## 风控系统
[introduction to online payments risk management, samet2013](https://book.douban.com/subject/24807540/)

https://zhuanlan.zhihu.com/p/107975044

## 广告系统

## 推荐系统

## 数据采集

![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCEe77a627f8f9e6cdad8f387fac907ab80/52)

[Kafka: The Definitive Guide](https://book.douban.com/subject/26828527/)  

[日志采集agent技术](https://yq.aliyun.com/articles/204554)

[从日志统计到大数据分析](https://zhuanlan.zhihu.com/p/20390103)

https://help.aliyun.com/document_detail/48204.html
https://engineering.linkedin.com/distributed-systems/log-what-every-software-engineer-should-know-about-real-time-datas-unifying  
https://www.infoq.cn/article/2018/01/confluent-kafka-data  

[Kinesis](https://aws.amazon.com/cn/kinesis/)

https://docs.fluentd.org/quickstart/life-of-a-fluentd-event
https://zturn.cc/elkbook/

## 数据统一访问

# 内部管理平台
ID中心， LDAP打通jira, gitlab, confluence，nexus, OA，HRM等内部系统

# 运维平台
![](https://mmbiz.qpic.cn/sz_mmbiz_png/jxHgxicVs5Y1niaj0lsSciaDGiaicSico2nAU7Drs8vtbkIg0ERN14v3KV9MfiaHNhgOmafjkUoyRlcCOfoPiblDgu3siaA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

系统生命周期管理  
资源配置：机器、IP、虚拟机、网络  
系统部署：包管理、灰度发布、回滚  
资源监控：  
应急响应：故障下线  


# 测试平台
用例管理、测试结果分析

https://help.aliyun.com/document_detail/29262.html?spm=a2c4g.11174283.6.543.2df91b3aU8Fq6m



https://docs.spring.io/spring/docs/current/spring-framework-reference/overview.html\#spring-introduction  
[https://en.wikipedia.org/wiki/Aspect-oriented\_programming](https://en.wikipedia.org/wiki/Aspect-oriented_programming)  
[https://www.ibm.com/developerworks/cn/java/j-aop/index.html](https://www.ibm.com/developerworks/cn/java/j-aop/index.html)  
[https://zhuanlan.zhihu.com/p/24565766](https://zhuanlan.zhihu.com/p/24565766)  
[http://www.importnew.com/26951.html](http://www.importnew.com/26951.html)  
[http://kubicode.me/2015/07/30/Java Base/Java-AOP-Study/](http://kubicode.me/2015/07/30/Java Base/Java-AOP-Study/)


## 字符和编码
https://home.unicode.org/  
https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/  


redis
https://mp.weixin.qq.com/s/i06PkS3rDLfouzVjS6QXkg

# 研发规范

https://ncrcoe.gitbooks.io/java-for-small-teams/content/

## 持续集成规范
集成流水线  
代码管理  
代码审查  
编译  
代码评审  
单元测试  
集成测试  
系统测试  
构建  
部署环境  

## 工程规范
项目命名  
项目结构  
项目管理工具    

## 接口规范
接口知识库与网关  
发布平台    

## 数据库设计规范

## 代码规范
代码提交  
代码设计  
日志打印  
性能追踪

