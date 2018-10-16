Codd-70

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



#对象存储
s3实现原理

#批处理
Hadoop, Spark实现原理

#海量存储
HBase
DynamoDB
Cassandra
HIVE

#经典存储(手动扩容)
mysql
mongo

##分库分表中间件
单库强一致性，多库2PC
Cobar属于阿里B2B事业群，始于2008年，在阿里服役3年多，接管3000+个MySQL数据库的schema,集群日处理在线SQL请求50亿次以上(由此可以计算：Cobar的TPS=5,000,000,000/(3000*24*60*60)=20)

|能力|Cobar|MyCAT|
| ---- | ---- | ---- |
|前端|MySQL协议|MySQL协议|
|事务|2PC|弱XA|
|读写分离||:ballot_box_with_check:|
|HASH分片||:ballot_box_with_check:|
|后端|||
|协议|MySQL|MySQL+JDBC|
|聚合||:ballot_box_with_check:|

比如一个简单的AVG操作，对于一些比较初级的分布式数据库模型而言，常见做法是把AVG直接下发到所有存储节点，这样造成的结果就是语法兼容，语义不兼容，最终拿到的是错误结果。而DRDS的智能下推引擎，对SQL的语法做充分的语义兼容性适配，针对AVG操作，只能由引擎将逻辑AVG SQL解析优化为SUM和COUNT的SQL然后进行下推，由底层的数据库实例节点完成SUM和COUNT计算，充分利用底层节点的计算能力，在引擎层将各个存储节点的SUM和COUNT结果聚合计算，最终计算出AVG。

#单机存储
Oracle Berkeley DB
LevelDB

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

