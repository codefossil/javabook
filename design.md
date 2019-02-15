[CS vs SE, Hoare09](https://reinout.vanrees.org/weblog/2009/07/01/ep-keynote.html)  
[什么是工程](https://en.wikipedia.org/wiki/Engineering)  
[CS != SE](http://www.cnblogs.com/buaashine/archive/2012/12/12/2813931.html)  
[We Are All Confident Idiots](https://www.guokr.com/article/439517/)  

[MIT 16.355](http://sunnyday.mit.edu/16.355/)  
[CMU-SEI](https://sei.cmu.edu/)  
[MIT-SAL](http://systemarchitect.mit.edu/index.php)  

# 基本问题
[Humphrey-SPA award](https://resources.sei.cmu.edu/news-events/events/watts/watts.cfm)  
[SE-history, 1996](https://www.dagstuhl.de/Reports/96/9635.pdf)  
https://en.wikipedia.org/wiki/Software_engineering  
https://en.wikipedia.org/wiki/Software_development  

[Engineering a Safer World, 2012](http://sunnyday.mit.edu/safer-world/index.html)  
[SE, 1968](http://homepages.cs.ncl.ac.uk/brian.randell/NATO/nato1968.PDF)  
[No Silver Bullet, 1986](http://sunnyday.mit.edu/16.355/BrooksNoSilverBullet2.html)  
[Software Engineering Economics, 1984](http://csse.usc.edu/TECHRPTS/1984/usccse84-500/usccse84-500.pdf)  
[SWEBOK, 2004](https://www.computer.org/web/swebok/index)  

[构建之法](https://book.douban.com/subject/27069503/)  
[A Multi-Decade Perspective, Scacchi, 2018](https://www.ics.uci.edu/~wscacchi/Papers/New/IEEE-Computer-Scacchi-2018.pdf)  
[自我评价](http://www.cnblogs.com/xinz/p/3852177.html)

# 开发流程
[Process Models, 2001](https://www.ics.uci.edu/~wscacchi/Papers/SE-Encyc/Process-Models-SE-Encyc.pdf)  
[Waterfall, 1970](http://www-scf.usc.edu/~csci201/lectures/Lecture11/royce1970.pdf)  
[Spiral, 1988](http://www-scf.usc.edu/~csci201/lectures/Lecture11/boehm1988.pdf)  
[PSP, 1996](http://www.star.cc.gatech.edu/documents/SpencerRugabear/psp.pdf)  
[CMM, 1991](http://sunnyday.mit.edu/16.355/cmm.pdf)  
[The Agile Methods Fray](http://www-scf.usc.edu/~csci201/lectures/Lecture11/demarco2002.pdf)  

https://en.wikipedia.org/wiki/Agile_software_development  

# 需求和规格
> 解决/不解决什么问题？谁的问题？
creator driven (问题分治还是工作分治)  
Be Zara, not Foxconn (从效率模式->快速响应式)  

* 逻辑（问题怎么解）  
  问题域分解/服务功能划分  
  输出：类/对象图、需求分析 
  
* 场景（验证能否走通）
  突出系统间依赖  
  输出：用例

第一原理  
[Top risks, 2001](http://sunnyday.mit.edu/16.355/lawrence-requirements.pdf)  
[Requirements Engineering, 2000](http://mcs.open.ac.uk/ban25/papers/sotar.re.pdf)  
[Clean Coder, 2011](https://book.douban.com/subject/11614538/)  
[软技能](https://book.douban.com/subject/26835090/)  
https://firstround.com/review/Responsiveness-New-Efficiency/  

https://simplicable.com/new/coding-principles  
https://about.gitlab.com/handbook/  
https://en.wikipedia.org/wiki/List_of_software_development_philosophies
http://blog.vgod.tw/
https://blog.youxu.info/
http://blog.54chen.com/
http://www.yankay.com
http://www.valleytalk.org

http://people.scs.carleton.ca/~deugo/Patterns/ospdg/
https://www.cs.cmu.edu/~aldrich/courses/413/

# 软件设计
> 收集信息/关键路径/简化

* 过程（数据怎么走）  
  接口/信息流/容错  
  输出：交互图、时序图  

* 物理（SRE怎么做）  
  网络/计算/存储/容器  
  可扩展/高可用/高性能  
  输出：基础设施 

how software evolution
[康威定律, 1967](http://www.melconway.com/Home/Conways_Law.html)  
[架构漫谈, 2016](https://www.infoq.cn/article/an-informal-discussion-on-architecture-part01)   

## 控制复杂度
DDD/TDD/BDD/CQRS/DCI/  
[DDD](https://book.douban.com/subject/1418618/)  
[System Architecture: Strategy and Product Development for Complex Systems](https://book.douban.com/subject/26938710/)  

## 控制规模

[Big data, 2015](https://book.douban.com/subject/10438832/)  
[Architecting for scale, 2016](https://book.douban.com/subject/27071892/)  
[Software design for large system, 1988](https://web.njit.edu/~kirova/BC-SDP.pdf)  
[排队论及其应用浅析](https://www.slideshare.net/frogd/ss-27959518)  
[构建高性能Web站点, 2009](https://book.douban.com/subject/3924175/)  

## 架构和模式
microservice/SOA/Lambda Architecture  

沉默成本（可用性）  
机会成本（兼容性）  
边际成本（扩展性）  
You Aren't Gonna Need It.
If it ain't broke, don't fix it.
飞轮效应

[Patterns of Enterprise Application Architecture, 2003](https://book.douban.com/subject/1230559/)  
[Agile Software Development, 2003](https://book.douban.com/subject/1140457/)  
[TAOUP, 2003](https://book.douban.com/subject/5387401/)  
[Code Architecture](https://book.douban.com/subject/30333919/)  
[Just Enough Software Architecture](https://book.douban.com/subject/24872314/)  
[亿级用户下的新浪微博平台架构](https://www.infoq.cn/article/weibo-platform-archieture)  

https://lethain.com/digg-v4-architecture-process/  
https://java-design-patterns.com/principles/  
https://web.njit.edu/~kirova/is663-s11.html  

[worse is better](http://dreamsongs.com/WorseIsBetter.html)  
[程序员的呐喊](https://book.douban.com/subject/25884108/)  
[rise of wib](http://dreamsongs.com/RiseOfWorseIsBetter.html)  
https://blog.codinghorror.com/worse-is-better/  
[wib-example](https://stackoverflow.com/questions/471544/worse-is-better-is-there-an-example)  

https://www.w3.org/DesignIssues/  
https://firstround.com/review/the-rewards-of-creator-driven-cultures-and-the-engineers-that-can-deliver-them/  
https://www.ibm.com/developerworks/cn/rational/r-4p1-view/index.html  

[The Rule of Least Power, 2001](https://www.w3.org/2001/tag/doc/leastPower.html)  
https://sourcemaking.com/refactoring/smells/speculative-generality  
https://medium.com/@jason.goodwin/the-rule-of-least-power-in-modern-technology-a4d9047e1063  
[Atwood's Law](https://blog.codinghorror.com/the-principle-of-least-power/)  
[Architectural and philosophical points](https://www.w3.org/DesignIssues/)  
[Laws of Software Development](http://www.globalnerdy.com/2007/07/18/laws-of-software-development/)  
[方法论、方法论——程序员的阿喀琉斯之踵](http://mindhacks.cn/2008/10/29/methodology-for-programmers/)  
http://www.lihaoyi.com/post/StrategicScalaStylePrincipleofLeastPower.html  
[PEP 20](https://www.python.org/dev/peps/pep-0020/)  

# 软件实现与质量
> 写诗还是写文档
根据现有的时间/预算/知识/复杂度，利用最佳实践、技术、框架、工具、设备（工程/学习能力）

[Clean Code](https://book.douban.com/subject/5442024/)  
[Refactoring](https://book.douban.com/subject/4262627/)  
[Code complete](https://book.douban.com/subject/1477390/)  

测试工具和方法  
[xUnit, 2007](https://book.douban.com/subject/1859393/)  
[TDD, 2003](https://book.douban.com/subject/1229924/)  
[OO tests, 2009](https://book.douban.com/subject/4156589/)  

[Agile Developer](https://book.douban.com/subject/4164024/)

# 软件发布和运维
流量切换 sla  
服务依赖/状态/降级  
发布和灰度   

[Continuous Delivery](https://book.douban.com/subject/6862062/)  
[Site Reliability Engineering](https://book.douban.com/subject/26875239/)  