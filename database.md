#事务管理 
WAL协议
2PC
事务隔离级别

#并发控制
mvcc
timestamp order
timestamp+dynamic locking
2PL
deterministic concurrency control
active-active

#数据建模和SQL
内联/外联/笛卡尔乘积
union/union all区别
left join
数据建模中的设计考虑
Generalization and Specialization
数据库为响应时间
数据库为高吞吐量
范式和非范式
how to scale a database
table corruption
数据库监控/切换
数据库连接池
c3p0/druid
JDBC
Mybatis

#索引
外排算法
索引的分类/区别

#查询管理
动态规划
贪心算法
iterator/volcano
materialization
vectorized

#批处理
Hadoop, Spark实现原理

#存储引擎
数据访问模式

##非结构化对象存储
s3实现原理

##列式存储
Vertica
Greenplum
Redshift 做海量数据queriable存储

##列族存储
HBase 做scan more， get less 存储

DynamoDB/Cassandra 做get more，scan less存储
HIVE

##全内存
memcache/redis 内存数据库，做高速响应queriable存储（其实是cache）

##经典行式存储
get少，scan少，低延迟
###关系模型
依赖多表join
单表10M~100M量级？
产品mysql, oracle

###文档模型
避免join
大多数据1对多
文档内查询弱
产品mongodb

###mysql分库分表中间件
单表5M，分表数=ceiling(N / (RDS 实例数 * 8) / 5,000,000)
N=100M行数据量

Cobar属于阿里B2B事业群，始于2008年，在阿里服役3年多，接管3000+个MySQL数据库的schema,集群日处理在线SQL请求50亿次以上(由此可以计算：Cobar的TPS=5,000,000,000/(3000*24*60*60)=20)

|特性|Cobar|MyCAT|DRDS|
| ---- | ---- | ---- | ---- |
|前端MySQL协议|✅|✅|✅|
|SQL||SQL92||
|事务|2PC|弱XA|强XA+2PC+柔性事务|
|读写分离||✅||
|分库路由||✅|hash|
|分表路由||✅|hash+时间|
|后端协议|MySQL|MySQL+JDBC||
|IO|NIO+BIO|AIO||
|join||库内任意+跨库2表|任意|
|子查询||1层|[支持列表](https://help.aliyun.com/document_detail/71295.html?spm=a2c4g.11186623.2.11.75093f68Qi2HQX)|
|聚合||✅|智能下推|

比如一个简单的AVG操作，对于一些比较初级的分布式数据库模型而言，常见做法是把AVG直接下发到所有存储节点，这样造成的结果就是语法兼容，语义不兼容，最终拿到的是错误结果。而DRDS的智能下推引擎，对SQL的语法做充分的语义兼容性适配，针对AVG操作，只能由引擎将逻辑AVG SQL解析优化为SUM和COUNT的SQL然后进行下推，由底层的数据库实例节点完成SUM和COUNT计算，充分利用底层节点的计算能力，在引擎层将各个存储节点的SUM和COUNT结果聚合计算，最终计算出AVG。

https://dev.mysql.com/doc/internals/en/date-and-time-data-type-representation.html
http://15721.courses.cs.cmu.edu/spring2017/schedule.html
http://www.cs.cmu.edu/~pavlo/datasets/index.html
https://sfu-db.github.io/dbsystems/
http://www.gpfeng.com/
http://troels.arvin.dk/db/rdbms/
https://en.wikipedia.org/wiki/Comparison_of_relational_database_management_systems
http://www.notedeep.com/note/38
http://www.redbook.io/
http://coding-geek.com/how-databases-work
https://dbmsmusings.blogspot.com/2010/03/distinguishing-two-major-types-of_29.html

Xpress， 解LP MIP
Hadoop MapReduce，Spark 做海量数据批处
Storm/trident，做实时分布式消息处理 
Flume, 海量数据收集with high availability
Hive/SparkSQL，做大数据在线分析 
专业数据库 ap 时间序列 文档 图表 数据处理工具 hadoop spark flink