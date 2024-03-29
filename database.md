- 学术  
[SIGMOD](https://dl.acm.org/event.cfm?id=RE227&tab=pubs)  
[VLDB](http://vldb.org/pvldb)  
[daslab](http://daslab.seas.harvard.edu/)   

- 课程  
[SFU CMPT843](https://sfu-db.github.io/dbsystems/)   
[UMICH eecs584](http://web.eecs.umich.edu/~mozafari/fall2018/eecs584/)  
[WATERLOO cs848](https://cs.uwaterloo.ca/~tozsu/courses/CS848/W19/weekly.html)     
[CMSC 724](http://www.cs.umd.edu/class/spring2017/cmsc724/schedule.html)   
[CMU 15-721](http://15721.courses.cs.cmu.edu/spring2017/schedule.html)  
[WISC CS744](http://pages.cs.wisc.edu/~akella/CS744/S19/papers.html)
[HARVARD cs265](http://daslab.seas.harvard.edu/classes/cs265/)  
[CMU 15-445/645](https://15445.courses.cs.cmu.edu/fall2018/schedule.html)  
[MIT 6.830](http://people.csail.mit.edu/tdanford/6830papers/)  

http://cs.brown.edu/courses/csci2270/previous.html  
http://people.csail.mit.edu/tdanford/6830papers/  
https://people.eecs.berkeley.edu/~brewer/cs262/  

- 工业  
[Momjian-PostgreSQL](https://momjian.us/main/faq.html)  
[Comparison of different SQL implementations](http://troels.arvin.dk/db/rdbms/)  
[dbms wiki](https://en.wikipedia.org/wiki/Comparison_of_relational_database_management_systems)  
[淘宝数据库内核](http://mysql.taobao.org/monthly/)  
[db-rank](https://db-engines.com/en/ranking)  
[kaggle](http://www.kaggle.com)  


# 基本问题

![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCE1362f1c5f134120408969075ff62785b/88)

[Turing81, Codd](https://amturing.acm.org/award_winners/codd_1000892.cfm)  
[Turing98, Gray](https://amturing.acm.org/award_winners/gray_3649936.cfm)  
[Turing04, Stonebraker](https://amturing.acm.org/award_winners/stonebraker_1172121.cfm)  
 
[ddia](https://book.douban.com/subject/26197294/)  
从工程的角度，系统的，全面地讲解数据处理的各种问题。并且还有论文指南，深入浅出  

[redbook](http://redbook.io)  
从88年开始，每隔10年，由stonebraker组织，对数据这几年的发展进行总结和预测。 

[database system concept, silberschatz2020](https://www.db-book.com/db7/index.html)  
帆船书。简直是教材界的典范。  
本书是面向教学用的教材。经过作者精心编排和系统性的解读。  
概念讲得很透彻和精确，重点明确，没什么废话。   
另外理论部分的符号和公理引用都很严谨。  
有习题，工具，引用，还有精读文献。  
最关键的是，本书还在更新最新的进展。    

https://blog.victoriaholt.co.uk/2012/07/database-landscape.html

# 数据建模

> 一种精确的，独立的概念工具，描述数据本身，数据关系，数据的语义和一致性约束，以反映`现实业务的对象和事件`。  

![](https://conceptualmodeling.org/erlogo.png)

[Peter P. Chen Awardees](https://conceptualmodeling.org/PeterP.Chen_Awardees.html)

[The history of conceptual modeling](http://cs-exhibitions.uni-klu.ac.at/index.php?id=185)

`ch1, ch2, db concept`  
抽象是一种非常重要的手段，隐藏细节，简化交互。  
数据库系统主要目的就是通过**抽象数据视图**，来隐藏某些存储和维护细节。 

[what goes around, stonebraker05](https://15721.courses.cs.cmu.edu/spring2016/papers/whatgoesaround-stonebraker.pdf)  
总结了70-05这35年的数据模型得失 

[Relational Model, codd70](http://cs.brown.edu/courses/cs295-11/2006/codd.pdf)  
坚持数据展示和存储需要分离。  
提出关系数据模型，关系代数，数据语言概念。  

[E-R model, chen76, vldb](https://harrymoreno.com/assets/greatPapersInCompSci/7.3_-_The_Entity_Relationship_Model_-_Towards_A_Unified_View_of_Data-Peter_Pin-Shan_Chen.pdf)  
真实的业务需求怎样映射到数据库中。  
通过实体集合、关系集合来描述物理世界。  
在概念设计领域影响非常大。  

[Entity-Relationship Modeling, Thalheim00](https://book.douban.com/subject/18010984/)  


https://conceptualmodeling.org/

[RelaX - relational algebra calculator](https://dbis-uibk.github.io/relax/index.htm)  

https://en.wikipedia.org/wiki/Dimensional_modeling  
https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model

# 查询

index condition pushdown

`ch2~ch5, db concept`  
关系型查询语言SQL

[query optimization overview, Chaudhuri98](https://www.microsoft.com/en-us/research/publication/an-overview-of-query-optimization-in-relational-systems-paper/)   
查询优化器必读  
从查询空间、统计成本评估，枚举框架到分布式并行，作者列举了优化器领域当时的进展和遇到的难题。  
(DP优化的效果从O(n!)->O(n*2^n-1)???/Bushy join算法???)  

[MySQL optimization](https://dev.mysql.com/doc/refman/8.0/en/optimize-overview.html)

[critique of sql, 83](https://www2.cs.duke.edu/courses/spring03/cps216/papers/date-1983.pdf)

[access path, selinger-79](http://courses.cs.vt.edu/~cs4604/Spring13/lectures/selinger-qopt-paper.pdf)  
System-R里面关于sql处理的说明，结合统计信息，基于代价模型计算join顺序和嵌套查询。   

[query optimization, ioannidis96](http://infolab.stanford.edu/~hyunjung/cs346/ioannidis.pdf)  

[query evaluation, graefe93](https://www.csd.uoc.gr/~hy460/pdf/query.pdf)  


[algorithms for the join ordering problem, ict09](http://www.acad.bg/rismim/itc/sub/archiv/Paper6_1_2009.PDF)  

[self-tuning, vldb07](http://www.vldb.org/conf/2007/papers/special/p3-chaudhuri.pdf)  

[qp distributed, tods81](https://people.eecs.berkeley.edu/~wong/wong_pubs/wong73.pdf)  

[rule-based, sigmod87](http://www.dblab.ece.ntua.gr/~nikos/edith/qopt_bibl/papers/rule_based/freytag_sigmod87_rule_based_qopt.pdf) 

http://cgi.di.uoa.gr/~ad/MDE519.DOCS/  
https://www.csd.uoc.gr/~hy460/2019-2020-fall/  
http://avid.cs.umass.edu/courses/645/s2018/  
http://www.inf.ed.ac.uk/teaching/courses/ad/  
https://www.csd.uoc.gr/~hy460/2019-2020-fall/#portfolio  
http://infolab.stanford.edu/~hyunjung/cs346/  
http://pages.cs.wisc.edu/~nil/764/  


# 事务与并发控制

![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCE988bc0b146770b77bd9fb4f96948816f/145)

`ch17~ch18, db concept`  
17章是事务管理的理论指导。  
一个个执行事务当然可以，更好的是并发地执行，以提高吞吐、利用率，同时能够加快用户响应。  
通过构建一个简单的事务模型，抽象出R(A), W(B)，研究并发造成的各种现象。  
隔离是目的，Serializability是保证正确性的基石，并发控制就是研究怎样编排可串行化的事务组。  
`PS：这里又涉及时序、happen before等类似问题。并发|分布式基本问题可以提炼出来。`  
数据库领域，喜欢把内部锁叫做latch。  

[transaction processing, gray92](https://book.douban.com/subject/2586390/)

## 可串行性、悲观锁、时序
![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCE845bbb498fc383b00521772ee9fed46f/152)

[The Notions of Consistency and Predicate Locks in a Database System, eswaran76](http://people.csail.mit.edu/tdanford/6830papers/eswaran-notions-of-consistency.pdf)  
Serializability, 2PL

[occ, tods81](http://sites.fas.harvard.edu/~cs265/papers/kung-1981.pdf)    

[Concurrency Control in Distributed Database Systems, bernstein81](http://portal.acm.org/citation.cfm?id=356842.356846)  
细节描述MVCC

[Naming and Synchronization in a Decentralized Computer System, reed79](https://dspace.mit.edu/handle/1721.1/16279)  
首次MVCC

[granularity of locks and degree of consistency, gray75](http://jimgray.azurewebsites.net/papers/granularity%20of%20locks%20and%20degrees%20of%20consistency%20rj%201654.pdf)  
锁的粒度。

[InnoDB locking](https://dev.mysql.com/doc/refman/5.7/en/innodb-locking.html)  
意向锁用来表示当前表已经有行锁，减少表锁与行锁的扫描判断，造成锁表的性能损失。  


## 并发异常、隔离级别
![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCEb5c5a08a8353d9b91972a7fbc857fcb5/155)

[critique isolation level, sigmod95](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-95-51.pdf)  

[innodb - 15.7.2.1 Transaction Isolation Levels](https://dev.mysql.com/doc/refman/8.0/en/innodb-transaction-isolation-levels.html)  

|隔离级别|S|RR(default)|RC|RU|
|---|---|---|---|---|
select|自动转换成共享锁|一致性无锁读|一致性无锁读|无锁
select...for update/share|同RR|索引锁，间隙和next key锁|索引锁|无锁
update/delete|同RR|同上|行锁+where启发式解锁|同上
MVCC||✓|✓|

[Innodb中的事务隔离级别和锁的关系](https://tech.meituan.com/2014/08/20/innodb-lock.html)

[数据库事务隔离发展历史 | CatKang的博客](https://catkang.github.io/2018/08/31/isolation-level.html)  

[MySQL多版本并发控制机制(MVCC)-源码浅析](https://my.oschina.net/alchemystar/blog/1927425)  

[MySQL · 源码分析 · InnoDB Repeatable Read隔离级别之大不同](http://mysql.taobao.org/monthly/2017/06/07/)  
innoDB RR实现会出现幻读，postgrel和SQL Server不会，不过也符合sql标准

**MySQL使用MVCC+2PL，实现不同的隔离级别**  
innoDB的一致性读仅仅针对select语句。 insert/update/delete/select...for update等均使用锁的方式，不走一致性读。      
对于读写事务，普通的select无法保护其他事务修改和删除数据。 需要用户自行选择使用select...for update锁读。  

https://blog.csdn.net/earthhour/article/details/105585695

## 持久化、可恢复性与日志

[A way to do atomic writes](https://lwn.net/Articles/789600/)   
在存储系统应用中，为了保证原子写入，通常有2种方式，内存锁和rename()。  

[再探Linux内核write系统调用操作的原子性](https://blog.csdn.net/dog250/article/details/78879600)

[ARIES,tods92 ](https://people.eecs.berkeley.edu/~brewer/cs262/Aries.pdf)  

[voltdb recovery, icde2014](https://hstore.cs.brown.edu/papers/voltdb-recovery.pdf)

[5.4 MySQL服务器日志](https://dev.mysql.com/doc/refman/5.7/en/server-logs.html)

https://stackoverflow.com/questions/1154446/is-file-append-atomic-in-unix

# 存取方法

> 不访问不必要的数据  
> Is an index the best solution?

full text index
three-star index

[ORGANIZATION AND MAINTENANCE OF LARGE ORDERED INDICES, bayer70, icomod](https://infolab.usc.edu/csci585/Spring2010/den_ar/indexing.pdf)  
首次提出b树的定义，增/删/查的算法，形式化分析了算法的最小、最大和平均成本。  
分析了存储利用率。  
根据当时的磁盘性能，给出了k的最优解。  
结论的推论数据不知道是怎么来的：9tps/15k-->2tps/1.5M, ???  

[r-trees, 84](http://pages.cs.wisc.edu/~nil/764/Relat/7_rtree.pdf)

[lsm-tree, 96](https://www.cs.umb.edu/~poneil/lsmtree.pdf)  

[improved query performance with variant indexes, icomod97](http://cs.brown.edu/courses/cs227/archives/2008/mitchpapers/required5.pdf)  

[The Ubiquitous B-Tree, 79](http://cs.kangwon.ac.kr/~ysmoon/courses/2005_1/dwnolap/Comer79-U-B-trees.pdf)

[Relational Database Index Design and the Optimizers, 2005](https://book.douban.com/subject/26419771/)  

[SSTable](http://www.igvita.com/2012/02/06/sstable-and-log-structured-storage-leveldb/)  


http://smalldatum.blogspot.com/  
https://github.com/jarulraj/databaseology#access-methods

https://web.stanford.edu/class/cs245/
http://cs.brown.edu/courses/cs227/papers.html

[B+Tree index structures in InnoDB – Jeremy Cole](https://blog.jcole.us/2013/01/10/btree-index-structures-in-innodb/)

# 数据库哲学

![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCEd46192c545253eddd765cd4f182b7cc7/90)


[Architecture of a Database system, hellerstein07](http://db.cs.berkeley.edu/papers/fntdb07-architecture.pdf)  
[db-how](http://coding-geek.com/how-databases-work)  

[The physical structure of InnoDB index pages – Jeremy Cole](https://blog.jcole.us/2013/01/07/the-physical-structure-of-innodb-index-pages/)

[MySQL技术内幕](https://book.douban.com/subject/24708143/) 

## 经典数据库 (before 2000)
[system-r, 76](http://daslab.seas.harvard.edu/reading-group/papers/astrahan-1976.pdf)

[postgres, 86](https://sfu-db.github.io/dbsystems/Papers/postgres.pdf)

[gamma, 90](http://pages.cs.wisc.edu/~dewitt/includes/paralleldb/ieee90.pdf)

[parallel db, 92](https://people.eecs.berkeley.edu/~brewer/cs262/5-dewittgray92.pdf) 

[Providing OLAP to User-Analysts, codd93](http://www.uniriotec.br/~tanaka/SAIN/providing_olap_to_user_analysts.pdf) 

[one size fit all do not work with DSS, sigmod95](http://omega.sp.susu.ru/books/acm_sigmod/vol1/is1/SIGMOD95/P449.PDF)   

## 经典数据仓库和OLAP
[data warehousing and olap overview, chaudhuri97, sigmod](https://cs.nju.edu.cn/zhouzh/zhouzh.files/course/dm/reading/reading02/chaudhuri_sigmodrec97.pdf)  

[data cube, gray96, ieee](http://web.stanford.edu/class/cs345d-01/rl/olap.pdf)  

## NewSQL

![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCEceea69677d59e94487683cecd2a6904a/69)

[end of an architecture era, stonebaker07, vldb](http://www.cs.umd.edu/~abadi/papers/vldb07hstore.pdf)  
OLTP的需求变了，用户不在是交互终端的专家用户，而是各种WEB用户和IOT设备。  
20台32GB的机器，就可以装下TPC-C的工作数据；  
老的RDBMS架构不再适合集群、高可用、高度自动化运维的需求。  
新的方向：内置HA+2PC+单线程无锁-redo/undo日志-lock/latch

续集[hstore demo, vldb08](http://db.csail.mit.edu/pubs/final_hstore.pdf)给出了具体的实现选择。
分布式+行存+shared nothing集群+内存执行器
单线程/核+事务协调器/节点  
假设大多数的事务负载都是集中在预定义的存储过程中  

`原型需要斟酌的问题仍然是分布式基本问题`，[Mordern Main-Memory DB, larson2016, vldb](http://www.vldb.org/pvldb/vol9/p1609-larson.pdf)给出了MMDB的概览。

[oltp through the looking glass, sigmod08](http://www.cs.umd.edu/~abadi/papers/oltpperf-sigmod08.pdf)  
全内存数据库性能。通过把数据库子系统一个个去掉的方式，从内部看传统数据架构性能问题。

[这里](http://cs.brown.edu/courses/cs227/archives/2012/slides/dtxn/hstore-architecture.pdf)专门在介绍实操hstore

## 列式数据库
![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCE593514ae27acef5bbaeda0a1cde838a5/71)
[c-store, vldb2005](http://www.cs.umd.edu/~abadi/papers/vldb.pdf)  
数据仓库/CRM/电子图书馆类目，需要成批的大量数据加载，然后长期进行即席查询。这类工作负载需要读优化。  
而围绕着数据Cube而构建的聚合预计算，对于一些无法提前参与的实时查询，没有更多的进步。 
cpu越来越快，而磁盘的带宽却涨幅不大，因此多用cpu来换磁盘IO比较划算。  
`目标：同时完成更新和即席查询工作负载。`  

- 数据模型。逻辑上还是关系数据库，通过projection、水平分segment、多排序键和索引(sid, sk)组成物理布局。
- 数据编码。多格式编码。
- 索引。加速tuple的重建。
- 读写分离。WS+RS+tuple mover。`WS是B-tree+大缓存`。RS逻辑上与WS保持1比1的索引和segment。tuple mover负责追平WS和RS之间的差异。
- 存储管理。segment分布。
- 分布式的事务。只读事务遵循快照隔离基于epoch IV+DRV+授时算法。更新事务遵循2PL+WAL。授时服务负责协调有效时间[HWM, LWM]。
- 容错恢复。
- 查询优化器和计划。基于成本估算的计划，选择最优projections组合。

结论：c-store其实是多技术的创新结合体，包括数据压缩、物化视图、快照隔离、事务管理、高可用。

[Column-Stores vs. Row-Stores: How Different Are They Really?, sigmod08](https://15721.courses.cs.cmu.edu/spring2019/papers/09-storage/p967-abadi.pdf)  


https://docs.aws.amazon.com/redshift/latest/dg/c_columnar_storage_disk_mem_mgmnt.html
[digg v4](https://knowyourmeme.com/memes/events/digg-v4)  
https://www.memsql.com/blog/why-nosql-databases-wrong-tool-for-modern-application/
https://dzone.com/articles/nosql-vs-sql-differences-explained
https://www.gartner.com/doc/reprints?id=1-5N2H2SM&ct=181024&st=sb
[don't use mongodb](https://news.ycombinator.com/item?id=3202081)  
http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/  
https://laptrinhx.com/apache-hawq-next-step-in-massively-parallel-processing-3942821226/  

## 时间序列数据库

https://www.francosolleza.com/CS227/

https://www.elastic.co/blog/elasticsearch-as-a-time-series-data-store

https://www.influxdata.com/blog/influxdb-markedly-elasticsearch-in-time-series-data-metrics-benchmark/

## 图数据库


# todo

[presto](http://prestodb.github.io/)  
[antlr](https://www.antlr.org)  
[innodb架构](https://dev.mysql.com/doc/refman/5.7/en/innodb-architecture.html)    

https://github.com/mysql/mysql-server/blob/5.7/sql/sql_optimizer.cc
https://tech.meituan.com/2014/06/16/presto.html
https://www.cockroachlabs.com/blog/join-ordering-pt1/
http://idke.ruc.edu.cn/reading/index.htm#phd

http://hyper-db.com/

https://www.linkedin.com/pulse/100-open-source-big-data-architecture-papers-anil-madan
https://www2.cs.duke.edu/courses/fall18/compsci516/
https://www.inf.unibz.it/~artale/DB2/db2-course.htm
https://sites.google.com/site/cs186fall17/home/schedule-and-notes
https://www.ibmbigdatahub.com/blog/celebrating-db2-s-25-years-awesome
http://daslab.seas.harvard.edu/classes/cs165/#

https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-830-database-systems-fall-2010/readings/

https://www.svds.com/data-architecture-reading-list/



http://www.gpfeng.com/  
http://www.notedeep.com/note/38  
http://www.redbook.io/  
https://fgiesen.wordpress.com/category/papers/  
http://blog.yufeng.info/  

https://qw4990.gitbooks.io/nyadb/content/index.html



