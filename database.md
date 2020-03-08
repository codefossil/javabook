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

`ch6~ch7, db concept`  
数据库schema的设计，从ER模型到范式，保证数据不冗余。

[Entity-Relationship Modeling, Thalheim00](https://book.douban.com/subject/18010984/)  


https://conceptualmodeling.org/

[RelaX - relational algebra calculator](https://dbis-uibk.github.io/relax/index.htm)  

https://en.wikipedia.org/wiki/Dimensional_modeling  
https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model

# 查询

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

> 事务是为了简化，解决数据库容错

[The Notions of Consistency and Predicate Locks in a Database System, eswaran76](http://people.csail.mit.edu/tdanford/6830papers/eswaran-notions-of-consistency.pdf)


[ARIES,tods92 ](https://people.eecs.berkeley.edu/~brewer/cs262/Aries.pdf)

[occ, tods81](http://sites.fas.harvard.edu/~cs265/papers/kung-1981.pdf)  

[granularity of locks and degree of consistency, ibm75](http://jimgray.azurewebsites.net/papers/granularity%20of%20locks%20and%20degrees%20of%20consistency%20rj%201654.pdf)  

[transaction processing, gray92](https://book.douban.com/subject/2586390/)

[critique isolation level, sigmod95](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-95-51.pdf)  

[voltdb recovery, icde2014](https://hstore.cs.brown.edu/papers/voltdb-recovery.pdf)


# 存取方法

> 不访问不必要的数据  
> Is an index the best solution?

full text index
three-star index

[b-trees, icomod70](https://infolab.usc.edu/csci585/Spring2010/den_ar/indexing.pdf)  
给出b树的定义，增/删/查的算法，形式化分析了算法的最小、最大和平均成本。  
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


# 数据库哲学

![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCEd46192c545253eddd765cd4f182b7cc7/90)


[Architecture of a Database system, hellerstein07](http://db.cs.berkeley.edu/papers/fntdb07-architecture.pdf)  
[db-how](http://coding-geek.com/how-databases-work)  

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



# 数据分析

[anomaly survey, ACS09](https://cs.brown.edu/courses/csci2270/papers/anomaly-detection-survey.pdf)

[计算广告, 2015](https://book.douban.com/subject/26596778/)

[统计学习方法，2012](https://book.douban.com/subject/10590856/)

[prml, 2007](https://book.douban.com/subject/2061116/)

## 数据挖掘
https://ocw.mit.edu/courses/sloan-school-of-management/15-062-data-mining-spring-2003/lecture-notes/Lecture1Slides.pdf  

[learning from data, 2012](https://book.douban.com/subject/11026330/)  
http://personal.psu.edu/jol2/course/stat557/material.html  
https://wiki.illinois.edu/wiki/display/cs412/2.+Course+Syllabus+and+Schedule  
https://en.wikipedia.org/wiki/Data_mining  
http://www.stat.cmu.edu/~cshalizi/dm/19/  
https://docs.microsoft.com/en-us/analysis-services/data-mining/data-mining-concepts  
https://www.britannica.com/technology/data-mining  
https://developer.ibm.com/articles/ba-data-mining-techniques/  

数据科学
推荐系统
用户画像
知识图谱  
[Introduction to information retrieval, 2008](https://book.douban.com/subject/3059637/)  
机器学习  

[ML at Twitter, sigmod2012](http://web.cs.wpi.edu/~cs525/f13b-EAR//cs525-homepage/lectures/PAPERS/Lin_Kolcz_SIGMOD2012.pdf)

http://www.nlpir.org/wordpress/
https://jeffhuang.com/best_paper_awards.html
http://www.nltk.org/book/

http://staff.ustc.edu.cn/~zwp/teach/Prob-Stat/probstat.htm
https://github.com/metrofun/machine-learning-surveys


# 大数据

[clouds berkeley view, 2009](http://home.cse.ust.hk/~weiwa/teaching/Fall16-COMP6611B/reading_list/AboveTheClouds.pdf)

[big data, 2015](https://book.douban.com/subject/10438832/)

## 集群管理
[yarn, socc2013](http://web.eecs.umich.edu/~mosharaf/Readings/YARN.pdf)  
[mesos, nsdi2011](https://people.eecs.berkeley.edu/~alig/papers/mesos.pdf)  
[Borg, 2015](https://pdos.csail.mit.edu/6.824/papers/borg.pdf)  

## 分布式存储
[GFS, sosp03](https://static.googleusercontent.com/media/research.google.com/en//archive/gfs-sosp2003.pdf)  
[hdfs, 2010](http://pages.cs.wisc.edu/~akella/CS744/S19/838-CloudPapers/hdfs.pdf)  
[VL2, sigcomm09](http://bnrg.eecs.berkeley.edu/~randy/Courses/CS268.F09/papers/14_vl2.pdf)  

## 执行引擎
[MapReduce survey, sigmodrec2011](https://www2.cs.arizona.edu/~bkmoon/papers/sigmodrec11.pdf)  
[Spark, nsdi2012](https://www.usenix.org/system/files/conference/nsdi12/nsdi12-final138.pdf)  
[Spark SQL, sigmod2015](http://home.cse.ust.hk/~weiwa/teaching/Fall16-COMP6611B/reading_list/SparkSQL.pdf)  
[Tez, sigmod2015](http://web.eecs.umich.edu/~mosharaf/Readings/Tez.pdf)  
[Dryad, EuroSys07](http://www.cs.cmu.edu/afs/cs.cmu.edu/Web/People/15712/papers/isard07.pdf)  
[dataflow, vldb2015](http://www.vldb.org/pvldb/vol8/p1792-Akidau.pdf)    

## 分析框架
[Storm, sigmod2014](https://cs.brown.edu/courses/csci2270/archives/2015/papers/ss-storm.pdf)

[Kafka, NetDB2011](http://pages.cs.wisc.edu/~akella/CS744/S19/838-CloudPapers/Kafka.pdf)

[Flink, 2015](http://pages.cs.wisc.edu/~shivaram/cs744-slides/cs744-akshaya-flink.pdf)

[GraphX, osdi2014](https://amplab.cs.berkeley.edu/wp-content/uploads/2014/09/graphx.pdf)

[variant index, sigmod97](http://cs.brown.edu/courses/cs227/archives/2008/mitchpapers/required5.pdf)  

[Hive, icde10](http://infolab.stanford.edu/~ragho/hive-icde2010.pdf)

## 分布式任务调度
[Sparrow, sosp03](http://home.cse.ust.hk/~weiwa/teaching/Fall16-COMP6611B/reading_list/Sparrow.pdf)

## 数据中心网络
[jupiter, 2015](http://home.cse.ust.hk/~weiwa/teaching/Fall16-COMP6611B/reading_list/Jupiter.pdf)


[big data at LinkedIn, icomod2013](http://web.cs.wpi.edu/~cs525/f13b-EAR/cs525-homepage/lectures/PAPERS/p1125-sumbaly.pdf) 

http://barbie.uta.edu/~jli/mmwc.html  
http://c.biancheng.net/big_data/  
https://amplab.cs.berkeley.edu/benchmark/#  
https://www.infosysblogs.com/oracle/2018/08/oracle_exadata_mpp_databases_o.html  
https://dwarehouse.wordpress.com/2012/12/28/introduction-to-massively-parallel-processing-mpp-database/  
http://ece757.ece.wisc.edu/#betabook



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




