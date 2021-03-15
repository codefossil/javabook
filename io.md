
# 延迟
> 响应时间 = 服务时间（性能） + 排队时间

![](http://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCEbf029d15a4f0fb456ca9c6b9a7eed73e/173)

[Latency Numbers Every Programmer Should Know](https://people.eecs.berkeley.edu/~rcs/research/interactive_latency.html)

|||
|---|---|
同机房|0.05ms
同城|0.5ms
异地|50ms

## 常用中间件性能评估
|名称|机器配置|性能|客户端|延迟|数据来源
|---|---|---|---|---|---|
haproxy|16c,64GB|2.4M CPS,30MB/s,20 clients|900 qps/c|[haproxy1.6](https://www.freecodecamp.org/news/how-we-fine-tuned-haproxy-to-achieve-2-000-000-concurrent-ssl-connections-d017e61a4d27/)
nginx|36c,40Gbps,16GB|760K QPS/250K CPS, 730K/10K|10KB/r|[nginx 1.9](https://www.nginx.com/blog/testing-the-performance-of-nginx-and-nginx-plus-web-servers/)
kafka|6c,1Gbps,32GB,7200 SATA| 820K TPS|100B/r，78MB/s，NIC基本打爆了|AVG 2ms,TP99 3ms|[kafka 0.8](https://engineering.linkedin.com/kafka/benchmarking-apache-kafka-2-million-writes-second-three-cheap-machines)
zookeeper|2c|20K~80K/3severs QPS|200ms/elect|[Zookeeper3.x](https://zookeeper.apache.org/doc/r3.6.2/zookeeperOver.html)
RabbitMQ|4c,40GB|44K TPS|serval B/r|1ms-500ms|[rabbitMQ 2.8](https://www.rabbitmq.com/blog/2012/04/25/rabbitmq-performance-measurements-part-2/)

## 常见数据库性能评估
|名称|机器配置|TPC-C|延迟|数据来源
|---|---|---|---|---|
MySQL|24c,4TGB,SSD,25Gbps|380K tpmC|TP90 100ms|[tpcc TTA](http://tpc.org/results/fdr/tpcc/tta~tpcc~as-1124us-tnrp~fdr~2020-08-16~v01.pdf)

## 常见服务性能评估
|名称|机器配置|性能|客户端|延迟|数据来源
|---|---|---|---|---|---|
微信||14M QPS/635台服务器, 月活540M|40M/600=66K QPS/server|[100亿次红包](https://developer.51cto.com/art/202003/613210.htm)


# 性能
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


# 并发编程

[Software and the Concurrency Revolution, 2005](https://dl.acm.org/citation.cfm?id=1095421)  
[Parallel Programming, 2011](https://www.kernel.org/pub/linux/kernel/people/paulmck/perfbook/perfbook.2011.01.02a.pdf), 很多关于CPU缓存和一致性问题  
[OS Three Easy pieces, 2015](http://pages.cs.wisc.edu/~remzi/OSTEP/)  
[Multiprogramming, 1968](https://link.springer.com/content/pdf/10.1007%2F978-1-4757-3510-9_12.pdf)  

[Thread programming, 1989](https://www.cs.ubc.ca/~norm/508/2009W1/summaries/birrell%20paper%2003.pdf)  
[HYDRA, 1974](http://research.cs.wisc.edu/areas/os/Qual/papers/hydra.pdf)  
[Threads bad, 1995](https://www.cs.ubc.ca/~norm/508/2009W1/summaries/Conc-4/index.html)  
[Event bad, 2003](https://www.cs.ubc.ca/~norm/508/2009W1/summaries/Even-2/index.html)  
[Actor, 2016](http://dist-prog-book.com/chapter/3/message-passing.html)  

http://web.cecs.pdx.edu/~walpole/class/cs510/winter2018/home.html

https://en.wikipedia.org/wiki/Concurrent_computing  

https://www.irif.fr/~mellies/mpri/mpri-ens/articles/winskel-nielsen-models-for-concurrency.pdf

https://wiki.rice.edu/confluence/display/PARPROG/COMP322

https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-189-multicore-programming-primer-january-iap-2007/lecture-notes-and-video/


# C10K/C10M problem
http://www.kegel.com/c10k.html

|机器配置|客户端|客单价|总价|数据来源|
|--|--|--|--|--|
1GHz,2GB,Gbps $1200 | 20K client, 50Kb/s/c | $0.08/c | $100|2001
24c,3GHz,100GB | 2M client |10KB/socket? | |2012, [Whatapp](https://qunfei.wordpress.com/2016/09/20/from-c10k-to-c100k-problem-push-over-1000000-messages-to-web-clients-on-1-machine-simultaneously/)
12c,2.66GHz,96GB,10Gbps | 10M client, 512Kb/s/c |3.2KB/socket | |2015, [MigrateoryData](https://migratorydata.com//2015/05/20/how-migratorydata-solved-the-c10m-problem-10-million-concurrent-connections-on-a-single-commodity-server/)

I/O策略 1:1线程 VS M:N 线程

[SEDA: An Architecture for Well-Conditioned,Scalable Internet Services, welsh01, SOSP](http://www.sosp.org/2001/papers/welsh.pdf)

https://cs.uwaterloo.ca/~brecht/servers/readings.html
https://pages.cs.wisc.edu/~remzi/Classes/739/Fall2018/
https://github.com/smallnest/C1000K-Servers
http://highscalability.com/blog/2013/5/13/the-secret-to-10-million-concurrent-connections-the-kernel-i.html

# Nginx
http://www.aosabook.org/en/nginx.html

# Nodejs
[Node 之父 Ryan Dahl：我不想被定义, 2017](https://www.infoq.cn/article/2017%2F09%2FNode-Ryan-Dahl)  
[Design Mistakes in Node, 2018](https://tinyclouds.org/jsconf2018.pdf)  

http://www.gevent.org/

https://people.csail.mit.edu/rinard/teaching/osnotes/
https://pdos.csail.mit.edu/6.828/2018/schedule.html
https://www.cs.cmu.edu/~15712/syllabus.html
https://www.cc.gatech.edu/~rama/CS6210-External/

# Netty
[Netty in Action, maurer2015](https://book.douban.com/subject/24700704/)  


# UNIX network
![Figure 6.6. Comparison of the five I/O models.](https://www.masterraghu.com/subjects/np/introduction/unix_network_programming_v1.3/files/06fig06.gif)

https://github.com/JackJiang2011/MobileIMSDK

[Unix Network Programming, Volume 1](https://book.douban.com/subject/4859464/)

# RAW字节、编解码、序列化

## TCP网络数据编解码
原始字符流|  半包| 粘包| 粘包
|---|---|---|---|
AB CD|A BCD  |ABC D  |ABCD  

## 应用层数据编解码格式
![](http://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCE9a6a724d25fc64f2a2476428b09f9891/162)

[msgpack](https://msgpack.org/)  
[Protocol Buffers](https://developers.google.com/protocol-buffers)

[Serialization Performance comparison](https://maxondev.com/serialization-performance-comparison-c-net-formats-frameworks-xmldatacontractserializer-xmlserializer-binaryformatter-json-newtonsoft-servicestack-text/)
从编码空间、序列化和反序列化速度上面，比较了流行的编解码工具的性能。  

https://blog.mbedded.ninja/programming/serialization-formats/a-comparison-of-serialization-formats/