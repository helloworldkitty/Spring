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



3、在配置文件中创建程序所需的Bean

 <!-- bean节点的作用是创建对象，并把对象存储在IOC容器中。 -->
  <!-- class:表示某个类型 id：表示对象创建后在容器中的名称 -->
  <bean id="stu" class="com.icss.Student">
    <property name="name" value="李强"/>
    <property name="age" value="25"/>
    <property name="sex" value="男"/>
  </bean>
  
4.在程序中获取到IOC容器,从IOC容器中获取所需要的Bean
//获取IOC容器,当容器启动时，自动执行配置文件中的配置
ApplicationContext cxt = 	new ClassPathXmlApplicationContext("applicationcontext.xml");
	//根据容器中的Bean的ID属性值取对象
	Student student = (Student) cxt.getBean("stu");
	System.out.println(student);
  
  
  
  
8.XSD与DTD区别

1.DTD(Documnet Type Definition)
DTD即文档类型定义，是一种XML约束模式语言，是XML文件的验证机制,属于XML文件组成的一部分。
DTD 是一种保证XML文档格式正确的有效方法，可以通过比较XML文档和DTD文件来看文档是否符合规范，元素和标签使用是否正确。 一个 DTD文档包含：元素的定义规则，元素间关系的定义规则，元素可使用的属性，可使用的实体或符号规则。

DTD和XSD相比：DTD 是使用非 XML 语法编写的。
DTD 不可扩展,不支持命名空间,只提供非常有限的数据类型 .
2.XSD(XML Schemas Definition) 
XML Schema语言也就是XSD。XML Schema描述了XML文档的结构。 
可以用一个指定的XML Schema来验证某个XML文档，以检查该XML文档是否符合其要求。文档设计者可以通过XML Schema指定一个XML文档所允许的结构和内容，并可据此检查一个XML文档是否是有效的。XML Schema本身是一个XML文档，它符合XML语法结构。可以用通用的XML解析器解析它。
一个XML Schema会定义：文档中出现的元素、文档中出现的属性、子元素、子元素的数量、子元素的顺序、元素是否为空、元素和属性的数据类型、元素或属性的默认 和固定值。
XSD是DTD替代者的原因，一是据将来的条件可扩展，二是比DTD丰富和有用，三是用XML书写，四是支持数据类型，五是支持命名空间。
XML Schema的优点:
1) XML Schema基于XML,没有专门的语法 
2) XML Schema可以象其他XML文件一样解析和处理 
3) XML Schema比DTD提供了更丰富的数据类型.
4) XML Schema提供可扩充的数据模型。 
5) XML Schema支持综合命名空间 
6) XML Schema支持属性组。
ps：xml--》可扩展性标记语言


9、源码打开
如果需要查看源码，则需要把源码引用到程序中。如果是Maven项目，则会自动引用到源码。


10、Bean的获取
从IOC容器中获取Bean的方式有两种，
1.根据ID属性值或name属性值取对象，取出的对象是Object类型，需要强制类型的转换，不建议采用name属性给Bean命名。
实例：
//根据容器中的Bean的ID属性值取对象
Student student = (Student) cxt.getBean("stu");

2.根据类型取Bean对象，不需要强制类型的转换。注意，要求IOC容器中相同类型的对象是唯一，如果有多个同类型对象，就只能根据ID属性值取对象，否则抛异常：
//根据类型从IOC容器中获取对象，注意，必须保证容器中的对象是唯一。如果有多个相同类型对象，抛异常
Student student2 = cxt.getBean(Student.class);




11、Bean生命周期
Bean随着IOC容器的创建而创建，一旦创建就会一直存储在IOC容器中，直到IOC容器关闭或者程序关闭才会关闭，默认情况下，Bean对象的创建采用单例模式（？）
（ps：单例模式分为懒汉式和饿汉式，懒汉式就是要什么需求就给什么，但是会出现线程同步的问题，解决的方法就是加锁。饿汉式就是一次性给完）
容器的加载方式：
//获取IOC容器,当容器启动时，自动执行配置文件中的配置
ApplicationContext cxt = 	new ClassPathXmlApplicationContext("applicationcontext.xml");



12、Bean创建的方式
1.使用类的构造器的方式
采用构造函数来创建，默认是无参构造函数
  <!-- 运用无参的构造函数来创建Bean, 
     class:表示某个类型 id：表示对象创建后在容器中的名称 -->
  <bean id="stu" class="com.icss.Student">
    <!-- 给对象的属性赋值 -->
    <property name="name" value="李强"/>
    <property name="age" value="25"/>
    <property name="sex" value="男"/>
  </bean>
  <!-- 应用有参的构造函数来创建Bean对象 -->
  <bean id="stu2" class="com.icss.Student">
    <!-- constructor-arg 构造器  index=""索引 name:是参数名，可以不按顺序来赋值， ref:引用另一个类型对象-->
    <constructor-arg index="0"  value="肖红"/>
    <constructor-arg name="age" value="20"/>
    <constructor-arg index="2"  value="男" />
  </bean>
  
  
  2.使用静态工厂方法实例化Bean对象
 写一个工厂类注意（static）
 public class OrderFactory {
	public static Order createOrder() {
		Order order = new Order();
		order.setPrice(100);
		order.setName("衣服");
		return order;
	}
}
主文件Bean配置：
!-- class:表示工厂类   factory-method：工厂类中的静态方法-->
  <bean id="order" class="com.icss.OrderFactory" 
     factory-method="createOrder">
    </bean>



3.使用实例工厂方法实例化Bean对象实例工厂创建
写一个类（没有static）：
public class OrderFactory {
	public Order createOrder() {
		Order order = new Order();
		order.setPrice(100);
		order.setName("衣服111");
		return order;
	}
}
工厂也是一个Bean
<Bean id="factory" class="com.icss.orderFactory"></Bean>
<!-- class:表示工厂类   factory-method：工厂类中的静态方法-->
<Bean id="order" class="com.icss.orderFactory"  factory-method="createOrder"></Bean>



13、Bean的作用域
1.延迟加载
默认情况下，Bean对象会在ICO容器启动时就自动加载，有时会浪费，所以可以在第一次使用Bean对象时，才加载对象。
默认lazy-init=“default” 修改为 lazy-init="true" 可以加在某个节点上，只对这个节点有用，也可以加在bean的根节点上，则在xml文件中的所有bean有效。

2.IOC容器默认创建的Bean是单例模式（singleton），每一次取到Bean对象是同一个，如果想产生新的对象，则可以改成（prototype）。 
<bean id="stu" class="com.icss.Student" scope="prototype">scope="prototype" 设置此属性值，则自动延迟加载。
  
  3.request，session，global session这几个属性值只适用于B/S结构项目。
  
  4.Bean的初始化方法和销毁
   <Bean id="stu" class="com.icss.Student" init-method="init" destory-method="destory"></bean>
  
// 获取IOC容器,当容器启动时，自动执行配置文件中的配置
		AbstractApplicationContext cxt = new ClassPathXmlApplicationContext("config/applicationcontext.xml");
		// 根据容器中的Bean的ID属性值取对象
		Student student = (Student) cxt.getBean("stu");
		System.out.println(student);
		//销毁IOC容器,容器销毁，则容器中所有的对象也销毁。
		cxt.close();  
    
    
    
    14、注入依赖对象
   1、 当一个对象有外键对象时应该如何构建？
    用ref属性
    <!-- 运用无参的构造函数来创建Bean, 
     class:表示某个类型 id：表示对象创建后在容器中的名称 -->
    <bean id="stu" class="com.icss.Student">
     <property name="name" value="李强"/>
    <property name="age" value="25"/>
    <property name="sex" value="男"/>
      <!-- ref属性引用外部对象 -->
     <property name="grade" ref="g"/>
    </bean>
<bean id="g" class="com.icss.Grade" p:gradeId=""  p:gradename=""></bean>

2、构造内部对象，内部对象的作用范围只局限于当前对象。



15、引入命名空间
引入p命名空间后，可以直接在bean 节点上加 p:属性名进行赋值,简化操作。
<bean id="g" class="com.icss.Grade" p:gradeId="1" p:gradeName="一年级">
</bean>
记得要在头头的地方引入命名空间鸭！




17、集合装配
  集合有：list ,set , map, Properties,如果要运用集合装配，必须引用util命名空间
  ！[image](https://github.com/helloworldkitty/Spring/blob/master/%E5%9B%BE%E7%89%873.png)
  
  
 
 
 
 （ps：三大集合）
 list ,set , map区别
 
List和Set是存储单列数据的集合，Map是存储键值对这样的双列数据的集合；
list 存储的数据是有顺序的，值允许重复。
set 存储数据无顺序，值不可重复。
map 存储数据是无序的，键不允许重复，但是值可以重复！！！











