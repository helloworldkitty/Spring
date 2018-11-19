1、是什么：
Spring是一个开放源代码的设计层面框架，他解决的是业务逻辑层和其他各层的松耦合问题，因此它将面向接口的编程思想贯穿整个系统应用。（轻量级框架）

2、spring框架特征：
轻量
控制反转：对象的控制权交给了外部容器。控制反转也叫依赖注入（DI）。程序中所需要的对象依赖IOC容器，把IOC容器中的对象注入到程序中。（白菜归属权的问题）
面向切面
容器（IOC）
框架
MVC

3、常用框架
企业开发涉及到的整合如下：
SSH (Spring Struts2  Hibernate) 过时了
SSM (Spirng SpringMVC  Mybatis)  流行时
SSH2 (Spring  SpringMVC  Hibernate) 用的比较少
SpringBoot  理念是：零配置。它不是一个新的框架，而是把现有的框架进行了整合


4、特点
方便解耦，简化开发
AOP编程的支持
声明式事务的支持
方便程序的测试
方便集成各种优秀框架
降低Java EE API的使用难度
Java 源码是经典学习范例

5、基本框架
核心容器：主要组件（BeanFactroy）
Spring 上下文
Spring AOP
Spring DAO
Spring ORM
Spring Web 模块
Spring MVC 框架

6、下载
下载资源包后解压：
![image](https://github.com/helloworldkitty/Spring/blob/master/%E5%9B%BE%E7%89%871.png)


项目中引用libs目录下的jar包，第一个jar包都有3个文件（Jar源文件，帮助文档，源码文件）
![image](https://github.com/helloworldkitty/Spring/blob/master/%E5%9B%BE%E7%89%872.png)




7、应用Spring
1.导入所需要的jar包
commons-logging-1.1.3.jar  这个包不属于Spring框架。
spring-beans-4.3.10.RELEASE.jar
spring-context-4.3.10.RELEASE.jar
spring-core-4.3.10.RELEASE.jar
spring-expression-4.3.10.RELEASE.jar
2.添加xml 配置文件,文件名建议用applicationcontext.xml。
![image](https://github.com/helloworldkitty/Spring/blob/master/%E5%9B%BE%E7%89%873.png)










