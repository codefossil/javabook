> Design of concurrent systems often entails finding reliable techniques for coordinating their execution, data exchange, memory allocation, and execution scheduling to minimize response time and maximise throughput.

*Performance and scalability are sensitive to platform factors such as CPU, processor count, cache size, and JVM characteristics, all of which can change over time* 

# 基本问题
[Concurrency-Early](http://cncc.bingj.com/cache.aspx?q=turing-lecture-the-computer-science-of-concurrency&d=4816567142126678&mkt=en-US&setlang=en-US&w=zm1S2Bj9n1OOUjUWX536fFC20hviKyz_)  
[Turing2013-Lamport](https://amturing.acm.org/award_winners/lamport_1205376.cfm)

# 排他互斥
[Solution of a Problem in Concurrent Programming Control, 1965](http://www.faculty.idc.ac.il/gadi/MyPapers/2008T-mutex.pdf)  
[Bakery, 1974](https://lamport.azurewebsites.net/pubs/bakery.pdf)  

[Recognizing Safety and Liveness](https://www.cs.cornell.edu/fbs/publications/RecSafeLive.pdf)  

[Equivalence of the Arbiter, the Synchronizer, the Latch, and the Inertial Delay, 1983](https://www.researchgate.net/publication/3048280_Equivalence_of_the_Arbiter_the_Synchronizer_the_Latch_and_the_Inertial_Delay)  

死锁的排查方法

# 生产者-消费者同步
[Co-operating sequential processes, 1968](https://pure.tue.nl/ws/files/4279816/344354178746665.pdf)  
[Reader and Writer, 1971](https://dl.acm.org/citation.cfm?id=362813)  

[Wait-free synchronization, 1991](https://cs.brown.edu/~mph/Herlihy91/p124-herlihy.pdf)  
[Algorithms for scalable synchronization on shared-memory multiprocessors](https://dl.acm.org/citation.cfm?doid=103727.103729), 各种同步原语check-then-act, compare-and-swap  , test-and-set, read-modify-write  
[Monitor, 1974](http://www.cs.ubc.ca/~norm/508/2009W1/summaries/monitors.pdf)，总结定义了monitor和条件变量  
[Barrier,1988](https://link.springer.com/article/10.1007/BF01379320)  

[The little book of semaphores, 2005](http://alumni.cs.ucr.edu/~kishore/papers/semaphores.pdf)  
[synchronization primitives survey, 2008](http://www.enseignement.polytechnique.fr/informatique/INF431/X09-2010-2011/AmphiTHC/SynchronizationPrimitives.pdf)  

# 顺序一致性

[How to Make a Correct Multiprocess Program Execute Correctly on a Multiporcessor, 1979](https://people.eecs.berkeley.edu/~culler/cs252-s03/lamport93how.pdf)  
[Linearizability, 1990](https://cs.brown.edu/~mph/HerlihyW90/p463-herlihy.pdf)  

[JSR133](http://www.cs.umd.edu/~pugh/java/memoryModel/jsr133.pdf)  
[Shared Memory](http://www.hpl.hp.com/techreports/Compaq-DEC/WRL-95-7.pdf)  
[The Java Memory Model](https://dl.acm.org/citation.cfm?id=1040336)  

# 形式化和验证
[The temporal logic of programs, 1976](http://dimap.ufrn.br/~richard/pubs/dim0436/papers/pnueli_temporal_1977.pdf)  
[CCS, 1980](https://moodle.risc.jku.at/pluginfile.php/6230/mod_resource/content/0/ccs.pdf)  
[Principles of Concurrent Programming](http://www.cse.chalmers.se/edu/year/2017/course/TDA384_LP1/lectures/)  
[Software Testing and Verification](http://www.cs.toronto.edu/~chechik/courses18/csc410/readings.html)  

http://www.ru.is/faculty/luca/IMTCOURSE/  
https://moodle.risc.jku.at/course/view.php?id=143  
http://www.cs.cornell.edu/gries/July2016/  

# 并发编程
[CPIJ, 1999](https://book.douban.com/subject/1440218/)  
[Software and the Concurrency Revolution, 2005](https://dl.acm.org/citation.cfm?id=1095421)  
[Parallel Programming, 2011](https://www.kernel.org/pub/linux/kernel/people/paulmck/perfbook/perfbook.2011.01.02a.pdf), 很多关于CPU缓存和一致性问题  
[OS Three Easy pieces, 2015](http://pages.cs.wisc.edu/~remzi/OSTEP/)  
[Multiprogramming, 1968](https://link.springer.com/content/pdf/10.1007%2F978-1-4757-3510-9_12.pdf)  
[JCIP, 2006](https://book.douban.com/subject/10484692/)  

[reactive design patterns](https://book.douban.com/subject/25870212/)

[Thread programming, 1989](https://www.cs.ubc.ca/~norm/508/2009W1/summaries/birrell%20paper%2003.pdf)  
[HYDRA, 1974](http://research.cs.wisc.edu/areas/os/Qual/papers/hydra.pdf)  
[Threads bad, 1995](https://www.cs.ubc.ca/~norm/508/2009W1/summaries/Conc-4/index.html)  
[Event bad, 2003](https://www.cs.ubc.ca/~norm/508/2009W1/summaries/Even-2/index.html)  
[Actor, 2016](http://dist-prog-book.com/chapter/3/message-passing.html)  

https://en.wikipedia.org/wiki/Concurrent_computing  
https://www.irif.fr/~mellies/mpri/mpri-ens/articles/winskel-nielsen-models-for-concurrency.pdf

## 计算模型
[Timesharing, 1962](http://www.eecs.harvard.edu/~margo/cs261/papers/corbato62.pdf)  
[The Working Set Model for Program Behavior, 1968](https://www.cs.rutgers.edu/~zz124/cs671_fall2013/lectures/fan_workingset.pdf)  
[NPTL, 2002](https://www.akkadia.org/drepper/nptl-design.pdf)  
[Task, 1996](http://www.evanjones.ca/software/threading-linus-msg.html)  
[Transactional memory, 1999](http://cs.brown.edu/~mph/HerlihyM93/herlihy93transactional.pdf)  

## 性能
[Imbench, 1996](http://mcvoy.com/lm/bitmover/lmbench/lmbench-usenix.pdf) ，线程切换 = 状态转换(~n us) + `cache missing`(~n 10ns), https://news.ycombinator.com/item?id=13930305  
[Why pthread](https://computing.llnl.gov/tutorials/pthreads/#WhyPthreads), fork(~n 100ns) = ~10x pthread_create(~n 10ns)  
[The Free Lunch Is Over, 2005](http://www.gotw.ca/publications/concurrency-ddj.htm)

[The Problem with Threads, 2006](https://www2.eecs.berkeley.edu/Pubs/TechRpts/2006/EECS-2006-1.pdf)  
[Thin Locks, 1998](http://cseweb.ucsd.edu/classes/fa05/cse231/Hubble.pdf)  

[System performance, 2014](https://book.douban.com/subject/26586598/)  
http://pages.cs.wisc.edu/~bart/736/f2017/paper1.html  
https://www.cse.iitb.ac.in/~mythili/os/notes/notes-perf.txt

[排队论及其应用浅析](https://www.slideshare.net/frogd/ss-27959518)  
[构建高性能Web站点, 2009](https://book.douban.com/subject/3924175/)  

> Performance is all about code path

* 优化问题，把所有访问路径列出来
* 各种cache/各种延迟影响很大

[我对后端优化的一点想法](https://www.slideshare.net/jamestong/2012-12552732)  
[5-minute rule](http://www.hpl.hp.com/techreports/tandem/TR-86.1.pdf)  
[Think Clearly About Performance](https://method-r.com/wp-content/uploads/2018/07/TCAP-from-MOTD2.pdf)
https://carymillsap.blogspot.com/2010/09/my-otn-interview-at-oow2010-which-hasnt.html


## 执行框架

[Java synchronizer, csjp04](http://gee.cs.oswego.edu/dl/papers/aqs.pdf)  
[Java Fork/Join, 2000](http://gee.cs.oswego.edu/dl/papers/fj.pdf)  
[Future, 1977](http://home.pipeline.com/~hbaker1/Futures.html)  

# 并行计算

![PPL](https://ppl.stanford.edu/)

https://www.cs.uky.edu/~jzhang/CS621/cs621.html

**并行限制**  
[Amdahl's law in the Multicore Era, 2008](http://www.eng.auburn.edu/~agrawvd/COURSE/E6270_Spr09/READ/Amdahls%20Law%20in%20Multicore%20Era.pdf)  
[Gustafson's law, 1988](http://www.johngustafson.net/pubs/pub13/amdahl.htm) 

http://www.cs.cmu.edu/~418
http://cs149.stanford.edu/winter19/

# 分布式系统
[分布式](ds/ds.md)  

[Distributed Computing, Kshemkalyani08](https://book.douban.com/subject/4182222/)

https://cis.temple.edu/~jiewu/teaching/Spring2018/distributed-computing-2018.pdf
https://books.google.ae/books?id=fEq2_vq-RGwC&pg=PP21&source=gbs_selected_pages&cad=2#v=onepage&q&f=false

**todo**

http://www.cs.cornell.edu/courses/cs6410/2018fa/sched.htm
https://www.cs.ubc.ca/~norm/508/2009W1/readinglist.html  
http://pages.cs.wisc.edu/~swift/classes/cs736-sp07/reading-list.html

http://www.scs.stanford.edu/17sp-cs240/syllabus/

https://www.cs.rutgers.edu/~zz124/cs671_fall2013/
http://blog.sina.com.cn/s/articlelist_1685243084_7_1.html
https://groups.csail.mit.edu/cag/ps3/schedule.shtml
https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-189-multicore-programming-primer-january-iap-2007/syllabus/
https://steve-yegge.blogspot.com/2006/03/moores-law-is-crap.html
https://www.extremetech.com/extreme/203031-moores-law-at-50-its-past-and-its-future
http://www.cs.cmu.edu/~418/schedule.html

http://www.newsmth.net/nForum/#!article/CSArch/43360）

http://www.cs.cmu.edu/afs/cs/academic/class/15712-s99/www/
https://www.cs.cmu.edu/~15712/syllabus.html
https://www.cs.cmu.edu/~410/lecture.html
http://www.eecs.harvard.edu/~margo/cs261/syllabus.html

https://blog.tsunanet.net/2010/11/how-long-does-it-take-to-make-context.html  
http://www.cis.upenn.edu/group/systems/slides/SystemsLunchSept09_Threads.pdf



http://cs.brown.edu/courses/cs176/lectures.shtml
https://en.wikipedia.org/wiki/Concurrency_pattern

http://www.cs.umd.edu/~pugh/java/memoryModel/jsr-133-faq.html
https://emeryberger.com/teaching/grad-systems/
https://en.wikipedia.org/wiki/Out-of-order_execution

https://stackoverflow.com/questions/6319146/c11-introduced-a-standardized-memory-model-what-does-it-mean-and-how-is-it-g
https://brooker.co.za/blog/
https://docs.microsoft.com/en-us/windows-hardware/drivers/kernel/acquire-and-release-semantics
https://preshing.com/20120930/weak-vs-strong-memory-models/
https://bartoszmilewski.com/2008/12/01/c-atomics-and-memory-ordering/
https://www.theregister.co.uk/2011/06/11/herb_sutter_next_c_plus_plus?page=1
https://stackoverflow.com/questions/44374614/vc-volatilems-on-x86




https://courses.physics.illinois.edu/cs533/sp2018/
http://web.mit.edu/6.173/
http://homepages.math.uic.edu/~jan/mcs572/
http://web.stanford.edu/~ouster/cgi-bin/cs140-spring14/lectures.php
https://github.com/angrave/SystemProgramming/wiki
https://learn.saylor.org/course/resources.php?id=94
https://pdos.csail.mit.edu/6.828/2018/schedule.html
https://www.scss.tcd.ie/~jones/CS4021/
http://www.doc88.com/p-6098166737073.html
https://dwheeler.com/secure-programs/Secure-Programs-HOWTO/index.html
https://www.eecs.wsu.edu/~hauser/teaching/Concurrent-S10/lectures/calendar.html
https://en.wikipedia.org/wiki/Concurrency_pattern
https://en.wikipedia.org/wiki/Concurrency_(computer_science)
https://en.wikipedia.org/wiki/Java_concurrency
https://en.wikipedia.org/wiki/Java_collections_framework
https://www.csd.uoc.gr/~hy486/old_websites/2011_2012/material.html
http://www.scs.stanford.edu/nyu/04fa/
http://web.mit.edu/6.005/www/fa16/
http://pages.cs.wisc.edu/~bart/537/lecturenotes/titlepage.html

https://en.wikipedia.org/wiki/List_of_important_publications_in_concurrent,_parallel,_and_distributed_computing
https://github.com/papers-we-love/papers-we-love/tree/master/concurrency
https://cis.temple.edu/~ingargio/cis307/readings/
https://bryanpendleton.blogspot.com/2015/06/weekend-reading-list.html




http://www.cnblogs.com/xkfz007/archive/2012/10/08/2715163.html
https://www.usenix.org/legacy/publications/library/proceedings/als00/2000papers/papers/full_papers/sears/sears_html/
http://cenalulu.github.io/linux/all-about-cpu-cache/




[TAMP](https://book.douban.com/subject/3901836/)
[History of Computing Project](http://www.thocp.net/)
https://www.cs.cmu.edu/~213/schedule.html  
https://www.multicians.org/
https://users.cs.duke.edu/~chase/cps196/topics.html
https://www.udacity.com/wiki/ud156-readings
https://cseweb.ucsd.edu/classes/wi01/cse221/
https://www.cc.gatech.edu/~rama/CS6210-External/class-schedule.pdf
https://www.cc.gatech.edu/classes/AY2010/cs4210_fall/#lectures
http://www.javapractices.com/topic/TopicAction.do?Id=248
http://gee.cs.oswego.edu/dl/concurrency-interest/index.html
https://docs.oracle.com/javase/6/docs/api/java/util/concurrent/package-summary.html
http://www.cs.cmu.edu/~418/schedule.html
http://csg.csail.mit.edu/6.823/lecnotes.html

https://docs.oracle.com/javase/tutorial/essential/concurrency/atomic.html
http://blog.vinceliu.com/2010/05/difference-between-atomic-and-volatile.html
https://www.ibm.com/developerworks/java/library/j-jtp06197/

https://www.cnblogs.com/dennyzhangdd/p/6734638.html
https://toutiao.io/posts/cv2q7t/preview
https://www.jianshu.com/p/c5058b6fe8e5
http://www.cnblogs.com/zhenyimo/p/6738210.html
https://cloud.tencent.com/developer/article/1013062

https://labs.oracle.com/pls/apex/f?p=labs:49:::::P49_PROJECT_ID:16
https://docs.oracle.com/javase/8/docs/
https://www.ibm.com/developerworks/java/library/j-jtp04223/index.html
https://www.ibm.com/developerworks/library/j-threads1/index.html
https://javainterview-mayank.blogspot.com/2011/04/synchronization-volatile-and-atomic.html

https://mechanical-sympathy.blogspot.com/2011/11/java-lock-implementations.html
https://flex4java.blogspot.com/2015/03/is-multi-threading-really-worth-it.html
https://baptiste-wicht.com/posts/2010/09/java-synchronization-mutual-exclusion-benchmark.html
https://mailinator.blogspot.com/2008/03/how-fast-is-java-volatile-or-atomic-or.html
https://blog.takipi.com/java-8-longadders-the-fastest-way-to-add-numbers-concurrently/

https://www.ibm.com/developerworks/library/j-jtp11234/
https://en.wikipedia.org/wiki/Non-blocking_algorithm
https://kukuruku.co/post/lock-free-data-structures-basics-atomicity-and-atomic-primitives/
http://winterbe.com/posts/2015/05/22/java8-concurrency-tutorial-atomic-concurrent-map-examples/

http://ifeve.com/enhanced-cas-in-jdk8/
https://cloud.tencent.com/developer/article/1021132
http://blog.leanote.com/tag/linckye/%E5%B9%B6%E5%8F%91




https://docs.oracle.com/javase/1.5.0/docs/guide/concurrency/overview.html


http://wiki.jikexueyuan.com/project/java-memory-model/lock.html
http://blog.csdn.net/qyp199312/article/details/70598480
http://mishadoff.com/blog/java-magic-part-4-sun-dot-misc-dot-unsafe/
https://blogs.oracle.com/dave/atomic-fetch-and-add-vs-compare-and-swap
https://brooker.co.za/blog/2013/01/06/volatile.html
https://github.com/torvalds/linux/blob/master/arch/x86/include/asm/cmpxchg.h
https://www.quora.com/Why-does-the-Java-API-not-give-control-over-thread-scheduling-to-application-programmers



http://www.oracle.com/technetwork/java/tuning-139912.html
http://www.oracle.com/technetwork/java/5-136747.html
http://www.oracle.com/technetwork/java/6-performance-137236.html
