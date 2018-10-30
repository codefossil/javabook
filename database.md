#并发控制
**事务是为了简化，解决数据库容错。为了HA/HP，事务可以丢弃**
* 当2个并发同时写一个数据
* 当读和写一个数据同时发生

如果不加以控制，会产生以下错误问题：
**脏写**
|T1|T2|T2结果|
| -- | -- | -- |
|W(A=50)||
||W(A=100)+commit|
|commit||A!=50|

**脏读**
|T1|T2|T2结果|
| -- | -- | -- |
||R(A)|72|
|W(A=96)|||
||R(A)|96|
|rollback|||

**更新丢失，经典汇款**
A=100, B=100
T1：A给B 50
T2：查看A和B总和

|T1|T2|T2结果|
| -- | -- | -- |
|R(A)|||
|A=A-50||
|W(A)|R(A)|50|
||R(B)|100|
|R(B)|返回A+B|150|
|B=B+50|commit|
|W(B)||
|commit||

原子写-counter
|T1|T2|T2结果|
| -- | -- | -- |
|R(A)=42|||
||R(A)|42|
|W(A+1)=43|||
||W(A+1)|43|

**不可重复读**
|T1|T2|T2结果|
| -- | -- | -- |
||R(A)|50|
|W(A=100)+commit|||
||R(A)+commit|100|

**幻读**
|T1|T2|T2结果|
| -- | -- | -- |
||MAX|50|
|ADD(A=100)+commit||**幻读和不可重复读的区别=添加**|
||MAX+commit|100|

##串行
###单线程实现
最简单的串行方式，比如Redis，
* 事务要数据量小，快速更新
* 或者内存可以装满数据，取消cache，允许直接读少量内存数据

但是性能被单个CPU核心限制

###内存锁实现
####2PL=悲观=lock + 协议
|变体|协议|脏读|脏写|不可重复读|更新丢失|幻读|评价|
| -- | -- | -- | -- | -- | -- | -- | -- |
|2PL|锁可以在事务中间释放|✅|✅|✅|✅|✅|可能死锁|
|C2PL|2PL+1阶段就获取所有锁|||✅|✅|✅|保守派，无死锁，有幻读|
|S2PL|X-lock在事务结束释放|||✅|✅|✅|死锁，偏向读，读已提交|
|SS2PL|S-lock/X-lock都必须在事务结束释放||||✅|✅|可重复读|
|SS2PL+predicate（索引锁）|条件查询/更新/删除时，需要检查predicate锁||||||串行|

####SI/SSI=乐观=mvcc
||事务开始|可见性规则|不可见|事务提交|
|--|--|--|--|--|
|SI|所有已经提交的数据+所有没有提交的删除||正在处理的写事务+已经终止的事务+之后开始的事务||
|SSI|同上|跟踪正在提交的数据|同上|检查查询结果改变，回滚并重试|

**SSI适合读写较短的事务，事务终止数量严重影响性能**

SGT

###TO
timestamp+dynamic locking

2PC
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
##B树的深度问题
* 假设sizeof(key)=sizeof(next_node)=4 byte，**节点最大占用m*(4+4)=8*m byte**
* 假设sizeof(page)=4KB，m=4*1024/(4+4)=512，即**B树就是个512叉树**
* 假如有10M行数据，**B树最大深度有log(512/2, 10M)=2.9006~=3**，avl的深度log(2, 10M)=23.25

##B树和LSM
|OP|B|LSM|
| ---- | ---- | ---- | ---- |
|写|1.REDO 2.getPage+**树分裂(可能)** 3. 1~3个页到disk|1.REDO+memtable 2.当达到阈值，后台线程合并segment|
|读|getPage+内存中查找row|memtable+**迭代查询其他SSTable索引**|
|更新|读操作+更新+disk|写操作+更新标记|
|删除||写操作+删除标记|

* LSM
![](https://images0.cnblogs.com/blog/312753/201304/16145934-37d2fd126af44802b8d372329b59ccb4.png)
segment的大小和合并策略
查询失效时，加速迭代查询
高并发锁

* B树
叶节点到底是存值（**聚集索引**），还是文件偏移
写入是随机的


##多列索引和R-tree
复杂的条件查询通常会包含多列，普通的索引查询只能用到前缀匹配

##布隆过滤

[SSTable](http://www.igvita.com/2012/02/06/sstable-and-log-structured-storage-leveldb/)

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
memcache 仅仅作为cache
redis
内存数据库，做高速响应queriable存储（其实是cache）
nvm

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