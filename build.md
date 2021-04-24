# 代码复杂度、结构度量
![](https://www.synopsys.com/blogs/software-security/wp-content/uploads/LinesOfCodeInMillions.png)


http://faculty.cse.tamu.edu/ritchey/courses/csce431/winter20/  
https://alan-turing-institute.github.io/rsd-engineeringcourse/ch05construction/

[The Humble Programmer, turing lecture](https://dl.acm.org/doi/10.1145/355604.361591)

[cmu17-214, Principles of Software Construction](https://www.cs.cmu.edu/~charlie/courses/17-214/2020-spring/)  
到目前为止看到的关于软件开发最棒的课程。Josh Bloch是导师。  
现代软件开发已经过渡到需要理解和利用现成的构建块来构件软件系统。  
软件质量的度量是什么，编写代码之前需要想想这些度量是否需要满足。  
设计过程=整理工作+结构化理解+方便沟通，通过设计目标来评估设计、设计原则来描述最佳实践、设计模式来积累经验。 
class=类型+API+实现。  
怎样为易变的代码做设计=接口用来处理易改的部分+信息隐藏/封装是设计好坏最重要的因素。  
怎样为复用代码做设计=继承+代理组合+设计模式

[COMP 310](https://www.clear.rice.edu/comp310/f19/)

[programming principles](https://github.com/webpro/programming-principles)  
[Code as Design: Three Essays](https://www.developerdotstar.com/mag/articles/reeves_design_main.html)  

https://www.google.com/books/edition/Object_Oriented_Construction_Handbook/4edsQ97mEwUC?hl=en&gbpv=0

http://squall.cs.ntou.edu.tw/cpp/103spring/slides/CPP16-DisciplinedCodingStyles.pdf

http://www.revision-zero.org/reuse

https://cmu-17-356.github.io/

https://www.coursicle.com/cmu/courses/ISR/17480/

# 分析模型到设计模型
![](http://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCE7d38c424dc9f719a17b83d9ebec429f7/183)

[ch12, Systems Analysis and Design in a Changing World, Satzinger2015](https://www.amazon.com/Systems-Analysis-Design-Changing-World/dp/1305117204)  
对于OO来说，OOD大部分工作就是扩展分析模型，丰富实现细节。  
程序员编写程序的行为是单线程的，一次只能针对一个用例，设计模型需要提供类和流程。  
OOD是一种用例驱动，通过确定各种类、方法和之间的消息来执行用例，这个过程与程序员写程序的行为一致。    
对于简单的用例来说，直接编码合适；对于复杂的用例来说，建模便于思考、更直观。  
每次用例设计完，会有更多的类、更多的属性和方法被定义，设计类图就会变得充实。  

[Laws of Software Development](http://www.globalnerdy.com/2007/07/18/laws-of-software-development/)  

# 编程实践、接口、契约化
api设计
契约式设计、防御式编程

![](https://note.youdao.com/yws/public/resource/8f83e1297252c926e45efa55a901a1d2/xmlnote/WEBRESOURCE72667b09c11acd0f0b7b9c81b84cd30f/114)

[Refactoring, fowler2000](https://book.douban.com/subject/4262627/)  

[Agile Software Development, martin03](https://book.douban.com/subject/1140457/)  
定义了软件开发工程师的行规。  
完整展示OOAD，通过分析用户故事，到用例分析，产出软件的静态结构和动态结构。  
需求促使开发人员执行敏捷实践从而发现问题，通过设计原则诊断问题后，最后选择合适的设计模式解决问题。  
编写测试用例首次上升到开发人员的一等公民。   
演进式设计模式，每个模式都有维护成本，可能会把事情弄复杂。  
代码抽象度量令人印象深刻。  

[Clean Code, martin09](https://book.douban.com/subject/5442024/)  
写代码就是写诗。好的命名就是用来代替文档的。    
全书精华在第12章。    
我们需要一个迭代过程，测试用例写得越多，设计需要越简单。  
通过使用DI、接口和抽象等工具，实现低耦合+高内聚。   

[A Philosophy of Software Design, Ousterhout2018](https://book.douban.com/subject/30218046/)  
系统功能越多->就越复杂->理解越困难。  
复杂度解法=简化消除+分解封装。    
**抽象**则是一种实体的简化理解，忽略了不重要的细节。  
好的软件就是要最小的依赖、最少的认识负担。  
策略编程，投入10%的时间来思考好的设计。（敏捷弄不好就是直觉编程）  
接口要薄，要通用，实现要深。  

[pragmatic programmer, hunt99](https://book.douban.com/subject/1417047/)

[Code complete, McConnell04](https://book.douban.com/subject/1477390/)  

[Structure and Interpretation of Computer Programs, abelson96](https://book.douban.com/subject/1451622/)

[Concepts, Techniques, and Models of Computer Programming, roy04](https://book.douban.com/subject/1782316/)  
编程还是手艺吗？  

[how to design programs, felleisen2018](https://www.amazon.com/How-Design-Programs-Introduction-Programming/dp/0262534800)
 
[Working Effectively with Legacy Code, feather05](http://www.amazon.com/exec/obidos/ISBN=0131177052/theinternationscA/)

[The Practice of Programming, Kernighan99](https://book.douban.com/subject/1459281/)

[The Art of UNIX Programming (TAOUP), 2003](https://book.douban.com/subject/5387401/)   

[Expert One-on-One J2EE Development without EJB, johnson04](https://book.douban.com/subject/1426848/)  

[software foundation](https://softwarefoundations.cis.upenn.edu/)

[A Discipline of Programming, Dijkstra76](https://book.douban.com/subject/24841112/)  

https://ngte-se.gitbook.io/  
https://github.com/xingshaocheng/architect-awesome 
https://java-design-patterns.com/principles/  

# 单元测试、集成测试

[ch13, Systems Analysis and Design in a Changing World, Satzinger2015](https://www.amazon.com/Systems-Analysis-Design-Changing-World/dp/1305117204)  
单元测试=在集成其他组件之前，测试单个方法/类/组件。  


[growing object-oriented software guided by tests, beck09](https://book.douban.com/subject/4156589/)  

[Agile Developer](https://book.douban.com/subject/4164024/)

[关于单元测试](https://techsingular.net/2012/09/04/%E5%85%B3%E4%BA%8E%E5%8D%95%E5%85%83%E6%B5%8B%E8%AF%95/)  

[ten years tdd](http://wiki.c2.com/?TenYearsOfTestDrivenDevelopment)  

[Mock Objects](http://media.pragprog.com/articles/may_02_mock.pdf)

[Mock Roles, not Objects, freeman04, oopsla](http://jmock.org/oopsla2004.pdf)

[xUnit Test Patterns, 2007](https://book.douban.com/subject/1859393/)  

[test driven development by example, beck02](https://book.douban.com/subject/1771049/)

[A New Look at Test Driven Development, astels05](http://daveastels.com/a-new-look-at-test-driven-development.html)

http://jaoo.dk/dl/qcon-london-2009/slides/MichaelFeathers_TestDrivenDevelopmentTenYearsLater.pdf  
http://badsoftware.com/chapter1.htm  
http://wiki.c2.com/?JavaIdioms  
https://dhh.dk/2014/tdd-is-dead-long-live-testing.html  

https://github.com/actiontech/slides/blob/master/201807-MySQL%E4%B8%AD%E9%97%B4%E4%BB%B6%E6%80%A7%E8%83%BD%E6%B5%8B%E8%AF%95I-%E9%BB%84%E7%82%8E-IMG.pdf

# 代码库、持续构建
https://ohshitgit.com/  

[GNU make](https://www.gnu.org/software/make/manual/html_node/index.html#SEC_Contents)

[Continuous Integration: Improving Software Quality and Reducing Risk, duvall07](https://book.douban.com/subject/2159442/)

# 系统测试、压测、验收测试

[Requirements and Testing: Seven Missing-Link Myths, graham02](http://www.eng.auburn.edu/~kchang/comp6710/readings/RequirementsandTesting_SevenMissing_LinkMyths_Graham.IEEE_Software.2002Sept.pdf)

[What is Software Testing? And Why Is It So Hard?, whittaker2000](http://www.win.tue.nl/~wstomv/edu/sep/ieee/testing-is-hard.pdf)

https://www.istqb.org/  

[Testing in Scrum, linz2014](https://book.douban.com/subject/33319435/)  

[Endo-Testing: Unit Testing with Mock Objects, mackinnon01, xp2000](https://www2.ccs.neu.edu/research/demeter/related-work/extreme-programming/MockObjectsFinal.PDF)  

[comp6710](http://www.eng.auburn.edu/~kchang/comp6710/Presentation.Schedule.htm)  

# 软件发布和运维

![](https://pic1.zhimg.com/80/v2-4106a010bb1f53cf88f3e8173bff07e4_1440w.jpg)

发布和灰度   

[Kubernetes In Action, 2017](https://book.douban.com/subject/26997846/)  
[Continuous Delivery](https://book.douban.com/subject/6862062/)  
[Site Reliability Engineering](https://book.douban.com/subject/26875239/)  
[Infrastructure as Code](https://d1.awsstatic.com/whitepapers/DevOps/infrastructure-as-code.pdf)  

https://lpd-ios.github.io/2017/05/08/Git-Work-Flow/  
https://docs.gitlab.com/ee/README.html  
https://ohshitgit.com/  
www.conventionalcommits.org  
https://www.atlassian.com/git/tutorials  
https://github.com/GetMyle/Guides/wiki/MYLE-GitHub-Flow  
https://about.gitlab.com/2016/03/08/gitlab-tutorial-its-all-connected/  