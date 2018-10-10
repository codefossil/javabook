#时间复杂度

|复杂度|计算次数(1k)|迭代次数(1M)|
| ---- | ---- | ---- |
|O(1)|1|1|
|O(log(N))|7|14|
|O(N)|1000|1,000,000|
|O(NlogN)|7,000|14,000,000|
|O(logN^2)|1,000,000|1,000,000,000,000|
|O(logN^3)|1,000,000,000|1,000,000,000,000,000,000|

#事务管理 
WAL协议
2PL
内联/外联/笛卡尔乘积
索引
动态规划
贪心算法
2PC
事务隔离级别
数据库连接池
c3p0/druid
JDBC
Mybatis
union/union all区别
left join
索引的分类/区别
性能优化
dbms测试框架
外排算法
并发控制
rdms mpp hadoop nosql newsql
mysql teradata \* mongodb oceanbase
数据库为响应时间
数据库为高吞吐量
范式和非范式
mvcc
oom PermGen space
how to scale a database
table corruption
数据库监控/切换

#分库分表中间件
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


本文来自 朱小厮 的CSDN 博客 ，全文地址请点击：https://blog.csdn.net/u013256816/article/details/52769297?utm_source=copy 

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

