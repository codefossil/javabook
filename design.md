![](http://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCEaa32470fa924b91662c25ba30a413530/167)

# 系统分析
![](http://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCEb0cc1b43e772d2c5fba39c1f0451a721/175)

> 理解系统应该做什么

[Systems Analysis and Design in a Changing World, Satzinger2015](https://www.amazon.com/Systems-Analysis-Design-Changing-World/dp/1305117204)  

[Systems Analysis and Design: An Object-Oriented Approach with UML](https://www.amazon.com/Systems-Analysis-Design-Object-Oriented-Approach/dp/1118804678/ref=zg_bs_602672_46?_encoding=UTF8&psc=1&refRID=PKYB5W8Q8TXME0HQZ945)

[Object-Oriented Software Engineering - An Agile Unified Methodology](http://www.doc88.com/p-24061870292509.html)

https://www.umsl.edu/~sauterv/analysis/488_f01_papers/quillin.htm#Top  
http://www.umsl.edu/~sauterv/analysis/analysis_links.html  

## 需求、干系人、需求引出

功能性需求=业务用途必要的活动。  
分析师需要学习用户的工作行为，了解业务知识，甚至变成业务专家。  
每个公司都有自己的一套规则业务规则和流程，有些很容易理解；有些则很难被发现。  

干系人=所有对成功实现系统感兴趣的人。  
操作干系人包括所有直接与系统交互的人。包括C端的customer/user, B端的operator/accountant/patient...   
执行干系人使用系统的生成的数据。他们掌握的信息在组织内部不容易获取，也不广为人知。  

采访干系人，学会提问引导出业务过程的细节；控制话题节奏，避免简单复述和错失重点。  
如果可能的话，使用第一原理重新审视业务问题。  
寻找异常和错误条件，就会发现隐藏的业务规则细节。  
散发和搜集问卷、复查现存文档、现场观察业务、研究友商解决方案。  
快速迭代，干系人参与早期版本，收集活跃用户评论和建议。  

模型是系统某方面的抽象表示。是分析师与用户和设计师交流的工具。

[Top risks, 2001](http://sunnyday.mit.edu/16.355/lawrence-requirements.pdf)  

[Requirements Engineering, 2000](http://mcs.open.ac.uk/ban25/papers/sotar.re.pdf)  

[Software Requirements (Developer Best Practices), wieger2013](https://www.amazon.com/Software-Requirements-Developer-Best-Practices-ebook/dp/B00JDMPMOA/ref=pd_sim_3?pd_rd_w=wKAhL&pf_rd_p=dc435707-6f1f-492e-b80d-8408db56abc9&pf_rd_r=S56C0MGWXZ88BWAF8NET&pd_rd_r=28ae2f52-e876-45d2-8c75-3771125ae848&pd_rd_wg=Exiv6&pd_rd_i=B00JDMPMOA&psc=1)

[Requirements Engineering: From System Goals to UML Models to Software Specifications, axel2011](https://www.amazon.com/Requirements-Engineering-System-Software-Specifications-ebook/dp/B00DWHU40E)

## 定义需求、确定用户故事和用例图
用户故事=<WHO>+<WHAT>+<WHY>+验收描述。更不形式化，倡导更快的到达程序分析师手上，鼓励直接与用户沟通，避免过多文档。  
用例=响应用户请求的一次活动。强调分析师优化和建模。  

用户目标技术=按功能角色分类用户+目标描述  
事件分解技术=外部事件+时序事件+内部事件
用例图突出了actor与系统的功能关系。  

[Applying UML and Patterns, larman04](https://book.douban.com/subject/1440149/)

[Object-Oriented Analysis and Design with Applications, booch07](https://book.douban.com/subject/2266843/)  

## 领域建模
![](http://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCEfb1b8e2ec2c2c32968ecc84d262cc4d8/177)

**实体是现实世界的抽象，具体有形的东西、一次事件或者交互活动**就能表示现实世界的种种用例。  
头脑风暴需要分析师通过与用户沟通，结合用例和5W提问，分析和提炼出来。  
名字技术需要列出用例中使用的所有名词，从现有系统、流程和表单中，增加更多的细节，提炼出实体、属性以及他们之间的关系。
实体之间的关系=数量+通用/特殊+整体/部分
确定实体的状态，以及业务逻辑控制状态转换。   

[DDD](https://book.douban.com/subject/1418618/)  

## 用例建模

**领域类图和用例图**最好就在项目的早期就完整确定下来，以便为设计和开发服务。  

# 系统设计

[Fundamentals of Software Architecture, ford2020](https://book.douban.com/subject/34464806/)

[archi vs design](https://www.slideshare.net/luctrudeau/architecture-vs-design)

[reactive design patterns](https://book.douban.com/subject/25870212/)

[Patterns of Enterprise Application Architecture, fowler02](https://book.douban.com/subject/1229954/)

[Foundations for the Study of Software Architecture, perry92, SIGSOFT](http://citeseer.ist.psu.edu/viewdoc/download?doi=10.1.1.135.5430&rep=rep1&type=pdf)

[New Tweets per second record, and how!](https://blog.twitter.com/engineering/en_us/a/2013/new-tweets-per-second-record-and-how.html)

[Software Architecture as a Set of Architectural Design Decisions, jansen05, WICSA05](http://www.ics.uci.edu/~andre/ics223w2006/jansenbosch.pdf)

[A Classification and Comparison Framework for Software Architecture Description Languages, medvidovic99, TOSE](https://www.ics.uci.edu/~andre/informatics223s2009/medvidovictaylor.pdf)


## 定义架构
- 高性能
读写分离、分库分表、缓存服务、单机架构、负载均衡

- 高扩展
分层、SOA、微内核

- 高可用
  双机备份、FMEA、异地多活、熔断、降级、限流

https://tech.meituan.com/2018/05/31/dp-account-high-avaliable-road.html

https://blog.csdn.net/ityouknow/article/details/81230412

https://www.jianshu.com/p/dfce30de7fe3

![](https://pubs.opengroup.org/architecture/archimate-doc/ts_archimate/ts_archimate_files/image008.png)

> OODA loop

- Part of the process of architecting a software system is about understanding **what is significant and why**
- Understanding **the speed at which your organisation or business changes** is important

业务规则=约束+原则  
结构=边界+接口  

> 架构=重要的系统设计=结构+愿景=构建成本最小化+效率最大化

https://docs.oracle.com/cd/E19263-01/817-5764/architecture.html

[康威定律, 1967](http://www.melconway.com/Home/Conways_Law.html)  

[Big Design Up Front](https://en.wikipedia.org/wiki/Big_Design_Up_Front)  

[What Every Engineer Should Know About Software Engineering, 07](https://book.douban.com/subject/2607747/)

[Software Architecture in Practice, bass2013](https://www.amazon.com/Software-Architecture-Practice-3rd-Engineering/dp/0321815734)  


[Building Microservice](https://book.douban.com/subject/25881698/)  

[Microservices Patterns: With Examples in Java, 2019](https://book.douban.com/subject/33425123/)  



https://docs.microsoft.com/en-us/azure/architecture/microservices/migrate-monolith  
http://www.mit.edu/~richh/writings/  
https://blog.pragmaticengineer.com/software-architecture-is-overrated/

[微服务架构设计, 互联网金融公司](https://gudaoxuri.gitbook.io/microservices-architecture/)

[架构漫谈, 2016](https://www.infoq.cn/article/an-informal-discussion-on-architecture-part01)  

[TOGAF](https://en.wikipedia.org/wiki/The_Open_Group_Architecture_Framework)

[archimate](https://pubs.opengroup.org/architecture/archimate31-doc/chap01.html#_Toc10045266)

[ISO/IEC/IEEE 42010/42020/42030](http://www.iso-architecture.org/42010/)  

[IEEE 1016](https://perso.univ-st-etienne.fr/jacquene/gl/articles/IEEE-1016-2009.pdf)

[Architectural Blueprints - The 4+1 View Model of Software Architecture, kruchten95, rational](https://www.cs.ubc.ca/~gregor/teaching/papers/4+1view-architecture.pdf)


[On the Criteria To Be Used in Decomposing Systems into Modules, parnas72](https://www.win.tue.nl/~wstomv/edu/2ip30/references/criteria_for_modularization.pdf)

[A Laboratory For Teaching Object-Oriented Thinking, beck89, oopsla](http://people.cs.pitt.edu/~chang/231/5spec/CRCcard/Beck-LaboratoryForTeachingOO.pdf)


[Clean Architecture](https://book.douban.com/subject/30333919/)  
提出以企业业务规则和应用业务规则为核心，满足外部系统为目的涉及的“插件系统”。底层离中心业务越远越易变，高层中心业务规则是赚钱的法宝比较不易变。 

[Architecting for scale, 2016](https://book.douban.com/subject/27071892/)  
[Software design for large system, 1988](https://web.njit.edu/~kirova/BC-SDP.pdf)  

[Building Evolutionary Architectures, 2017](https://book.douban.com/subject/27148120/)  
[Just Enough Software Architecture](https://book.douban.com/subject/24872314/)    
[Architectural and philosophical points](https://www.w3.org/DesignIssues/)  

[Software Architecture for Developers, 2014](https://book.douban.com/subject/26248182/)  
权衡BDUF和演变式设计，软件架构中的争论，怎样产出图/文档

[Domain-Specific Languages, fowler2010](https://book.douban.com/subject/4775030/)

https://web.njit.edu/~kirova/is663-s11.html  
https://handbookofsoftwarearchitecture.com/

https://book.douban.com/subject/30443578/


沉默成本（可用性）  
机会成本（兼容性）  
边际成本（扩展性）  
You Aren't Gonna Need It.  
If it ain't broke, don't fix it.    

[Internet-arch](https://trac.tools.ietf.org/html/rfc3439)  

  

[Stop Learning Frameworks, 2018](https://sizovs.net/2018/12/17/stop-learning-frameworks/)  
[TAOUP, 2003](https://book.douban.com/subject/5387401/)   


[worse is better](http://dreamsongs.com/WorseIsBetter.html)  
[The Rule of Least Power, 2001](https://www.w3.org/2001/tag/doc/leastPower.html)  

[Laws of Software Development](http://www.globalnerdy.com/2007/07/18/laws-of-software-development/)  
[方法论——程序员的阿喀琉斯之踵](http://mindhacks.cn/2008/10/29/methodology-for-programmers/)  
[PEP 20](https://www.python.org/dev/peps/pep-0020/)  
[system-desgin](https://github.com/donnemartin/system-design-primer)  

https://martinfowler.com/architecture/

https://www.d.umn.edu/~gshute/softeng/principles.html

## 设计用户接口

## 设计数据库表、系统组件、子系统架构


# 控制复杂度

> the discipline of **systems thinking** proves to be an invaluable tool in assessing exposure, opportunities, parametric sensitivities. 
> instrument–process–operand model

[the magic number seven, 1956](https://academic.microsoft.com/paper/1984314602/reference)

[Complexity, Mitchell2011](https://book.douban.com/subject/6749832/)

[控制论与科学方法论, 2005](https://book.douban.com/subject/1322336/)

[系统论，95](https://book.douban.com/subject/1008370/)

[System Architecture: Strategy and Product Development for Complex Systems](https://book.douban.com/subject/26938710/)  
分析了一种系统化的思考方式和识别方法，结合大量实例自顶向下剖析了架构复杂系统的过程，总结出系统分为形式和功能，通过分解和分层等方法破解复杂系统。