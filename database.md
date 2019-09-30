- 学术  
[SIGMOD](https://dl.acm.org/event.cfm?id=RE227&tab=pubs)  
[VLDB](http://vldb.org/pvldb)  
[daslab](http://daslab.seas.harvard.edu/)   

- 课程  
[SFU CMPT843](https://sfu-db.github.io/dbsystems/)   
[UMICH eecs584](http://web.eecs.umich.edu/~mozafari/fall2018/eecs584/)  
[WATERLOO cs848](https://cs.uwaterloo.ca/~tozsu/courses/CS848/W19/weekly.html)     
[CMSC724](http://www.cs.umd.edu/class/spring2017/cmsc724/schedule.html)   
[CMU 15-721](http://15721.courses.cs.cmu.edu/spring2017/schedule.html)  


- 工业  
[Momjian-PostgreSQL](https://momjian.us/main/faq.html)  
[Comparison of different SQL implementations](http://troels.arvin.dk/db/rdbms/)  
[dbms wiki](https://en.wikipedia.org/wiki/Comparison_of_relational_database_management_systems)  

# 基本问题

[Turing81, Codd](https://amturing.acm.org/award_winners/codd_1000892.cfm)  
[Turing98, Gray](https://amturing.acm.org/award_winners/gray_3649936.cfm)  
[Turing04, Stonebraker](https://amturing.acm.org/award_winners/stonebraker_1172121.cfm)  
 
[ddia](https://book.douban.com/subject/26197294/)  
从工程的角度，系统的，全面地讲解数据处理的各种问题。并且还有论文指南，深入浅出  
[redbook](http://redbook.io)  
从88年开始，每隔10年，由stonebraker组织，对数据这几年的发展进行总结和预测。 
  
# 数据建模

https://blog.victoriaholt.co.uk/2012/07/database-landscape.html
https://blog.sqlizer.io/posts/sql-43/
https://en.wikipedia.org/wiki/Relational_algebra
https://en.wikipedia.org/wiki/Tuple_relational_calculus
https://blog.codinghorror.com/maybe-normalizing-isnt-normal/

> 一种精确的，独立的，抽象方式数据结构，用来描述现实业务的对象和事件。  
initial requirement->use case->object/relation  
normalization->business rule (Relational)

宽表和纵表
EAV模型
父表子表
汇总表/计数器表
物化视图
范式和非范式
事实表和维度表

[what goes around, stonebraker05](https://15721.courses.cs.cmu.edu/spring2016/papers/whatgoesaround-stonebraker.pdf)  
总结了70-05这35年的数据模型得失 

[Relational Model, codd70](http://cs.brown.edu/courses/cs295-11/2006/codd.pdf)  
坚持数据展示和存储需要分离，第一次提出关系数据模型，关系代数，数据语言概念。    
[E-R model, chen76](https://harrymoreno.com/assets/greatPapersInCompSci/7.3_-_The_Entity_Relationship_Model_-_Towards_A_Unified_View_of_Data-Peter_Pin-Shan_Chen.pdf)  
[ch4, High Performance MySQL, 2012](https://book.douban.com/subject/10443458/)  

http://cs.brown.edu/courses/cs295-11/2006/schedule.html  
http://cs.brown.edu/courses/csci2270/previous.html

http://www.databaseanswers.org/data_models/

# 数据库哲学
[system-r, 76](http://daslab.seas.harvard.edu/reading-group/papers/astrahan-1976.pdf)

[postgres, 86](https://sfu-db.github.io/dbsystems/Papers/postgres.pdf)

[gamma, 90](http://pages.cs.wisc.edu/~dewitt/includes/paralleldb/ieee90.pdf)

[c-store, vldb2005](http://www.cs.umd.edu/~abadi/papers/vldb.pdf) 

[oltp, sigmod08](http://www.cs.umd.edu/~abadi/papers/oltpperf-sigmod08.pdf)  
全内存数据库性能。通过把数据库子系统一个个去掉的方式，从内部看传统数据架构性能问题。

[olap, sigmod97](https://cs.nju.edu.cn/zhouzh/zhouzh.files/course/dm/reading/reading02/chaudhuri_sigmodrec97.pdf)


[data cube, ieee96](http://web.stanford.edu/class/cs345d-01/rl/olap.pdf)

[column vs row, sigmod08](https://15721.courses.cs.cmu.edu/spring2019/papers/09-storage/p967-abadi.pdf)  
 
[architecture db, 2007](http://db.cs.berkeley.edu/papers/fntdb07-architecture.pdf) 

[db-how](http://coding-geek.com/how-databases-work)  

[column-oriented vs column-family](https://dbmsmusings.blogspot.com/2010/03/distinguishing-two-major-types-of_29.html)   
[digg v4](https://knowyourmeme.com/memes/events/digg-v4)
https://www.memsql.com/blog/why-nosql-databases-wrong-tool-for-modern-application/
https://dzone.com/articles/nosql-vs-sql-differences-explained
https://www.gartner.com/doc/reprints?id=1-5N2H2SM&ct=181024&st=sb
[don't use mongodb](https://news.ycombinator.com/item?id=3202081)
http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/


# 查询

[critique of sql, 83](https://www2.cs.duke.edu/courses/spring03/cps216/papers/date-1983.pdf)

[access path, selinger-79](http://courses.cs.vt.edu/~cs4604/Spring13/lectures/selinger-qopt-paper.pdf)  
System-R里面关于sql处理的说明，结合统计信息，基于代价模型计算join顺序和嵌套查询。    

[overview, 98](https://www.microsoft.com/en-us/research/publication/an-overview-of-query-optimization-in-relational-systems-paper/)  
[algorithms for the join ordering problem, ict09](http://www.acad.bg/rismim/itc/sub/archiv/Paper6_1_2009.PDF)  
[query evaluation techniques, 93](http://infolab.stanford.edu/~hyunjung/cs346/graefe.pdf)  
[query optimization, ioannidis96](http://infolab.stanford.edu/~hyunjung/cs346/ioannidis.pdf)  
[qp distributed, tods81](https://people.eecs.berkeley.edu/~wong/wong_pubs/wong73.pdf)  
[rule-based, sigmod87](http://www.dblab.ece.ntua.gr/~nikos/edith/qopt_bibl/papers/rule_based/freytag_sigmod87_rule_based_qopt.pdf)  

# 日志与恢复

[ARIES,tods92 ](https://people.eecs.berkeley.edu/~brewer/cs262/Aries.pdf)

[voltdb recovery, icde2014](https://hstore.cs.brown.edu/papers/voltdb-recovery.pdf)



# 事务与并发控制

> 事务是为了简化，解决数据库容错

* 当2个并发同时写一个数据
* 当读和写一个数据同时发生
* 多个数据同时写

> 数据库事务保证数据不被破坏（AID），其局限是数据库无法维护业务的**并发不可变条件**

[critique isolation level, sigmod95](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-95-51.pdf)  
[granularity of locks and degree of consistency, ibm75](http://jimgray.azurewebsites.net/papers/granularity%20of%20locks%20and%20degrees%20of%20consistency%20rj%201654.pdf)  
[occ, tods81](http://sites.fas.harvard.edu/~cs265/papers/kung-1981.pdf)  

[cmu 15-445/645](https://15445.courses.cs.cmu.edu/fall2018/schedule.html)  
[2pl](https://en.wikipedia.org/wiki/Two-phase_locking) 

确定性
deterministic concurrency control  
view serialization的条件是什么?  
死锁、SGT闭环  
DAG Directed acyclic graph

# 存取方法

> 不访问不必要的数据
> Is an index the best solution?

hash index
b+tree index
lsm index
spatial index
full text index
selectivity/cardinality
three-star index
covering index
index-organized table

index-covered query
range query
how to sort

[The Ubiquitous B-Tree, 79](http://cs.kangwon.ac.kr/~ysmoon/courses/2005_1/dwnolap/Comer79-U-B-trees.pdf)
[Relational Database Index Design and the Optimizers, 2005](https://book.douban.com/subject/26419771/)  
[SSTable](http://www.igvita.com/2012/02/06/sstable-and-log-structured-storage-leveldb/)  
[MySQL索引背后的数据结构及算法原理](http://blog.codinglabs.org/articles/theory-of-mysql-index.html)  
[浅谈MySQL的B树索引与索引优化](https://monkeysayhi.github.io/2018/03/06/%E6%B5%85%E8%B0%88MySQL%E7%9A%84B%E6%A0%91%E7%B4%A2%E5%BC%95%E4%B8%8E%E7%B4%A2%E5%BC%95%E4%BC%98%E5%8C%96/)  


https://github.com/jarulraj/databaseology#access-methods

https://web.stanford.edu/class/cs245/
http://cs.brown.edu/courses/cs227/papers.html





# 实时大数据分析

[variant index, sigmod97](http://cs.brown.edu/courses/cs227/archives/2008/mitchpapers/required5.pdf)  

[Hive, icde10](http://infolab.stanford.edu/~ragho/hive-icde2010.pdf)

[MapReduce survey, sigmodrec2011](https://www2.cs.arizona.edu/~bkmoon/papers/sigmodrec11.pdf)

[big data, 2015](https://book.douban.com/subject/10438832/)

[big data at LinkedIn, icomod2013](http://web.cs.wpi.edu/~cs525/f13b-EAR/cs525-homepage/lectures/PAPERS/p1125-sumbaly.pdf)

web数据处理  

http://barbie.uta.edu/~jli/mmwc.html

# 复杂大数据分析

[计算广告, 2015](https://book.douban.com/subject/26596778/)

[统计学习方法，2012](https://book.douban.com/subject/10590856/)

[prml, 2007](https://book.douban.com/subject/2061116/)

[learning from data, 2012](https://book.douban.com/subject/11026330/)
数据挖掘  
数据科学
推荐系统
用户画像
知识图谱  
[Introduction to information retrieval, 2008](https://book.douban.com/subject/3059637/)  
机器学习  

[ML at Twitter, sigmod2012](http://web.cs.wpi.edu/~cs525/f13b-EAR//cs525-homepage/lectures/PAPERS/Lin_Kolcz_SIGMOD2012.pdf)


# todo

------
[presto](http://prestodb.github.io/)  
[antlr](https://www.antlr.org)  
[innodb架构](https://dev.mysql.com/doc/refman/5.7/en/innodb-architecture.html)    

https://github.com/mysql/mysql-server/blob/5.7/sql/sql_optimizer.cc
https://tech.meituan.com/2014/06/16/presto.html
https://www.cockroachlabs.com/blog/join-ordering-pt1/
http://idke.ruc.edu.cn/reading/index.htm#phd

iterator/volcano  
materialization  
vectorized  
地理位置查询/多维查询



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




