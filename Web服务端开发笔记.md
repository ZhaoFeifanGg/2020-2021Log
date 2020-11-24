# 2020.9.17 第一周

## 需要学习的知识

Spring Boot 2.3.x

Mybatis 3.x

Spring 5.x

Vue

## 开发框架模式

m - model

c - controller

v -view

## 注解

减少xml配置，如Bean配置文件applicationContext.xml

```java
@Controller 处理http请求
@RestController 返回json数据=@ResponseBody+@Controller
@GetMapping 组合注解
@RequestParam 获取请求参数的值
```

## IDEA

开发工具 

## Postman

调试

# 2020.9.24 第二周

## MVC模式

### MVC介绍

Model模型-View视图-Controller控制器

对应JSP-Servlet-JavaBean

视图层View用户交互界面

控制层Controller不做任何数据处理，接受完成用户请求

MVC核心：Model模型设计，即业务逻辑处理及指定数据模型

### 建议

Web前端开发页面设计失业-核心放在Js或改行

后端开发重点在模型M层

### MVC开发底线

所有请求，流程控制都由控制器完成

视图部分不能有任何业务逻辑

### 优势

最大化重用代码：多个视图共享一个模型

易更新改变：三层分离更容易改变应用程序的数据层和业务逻辑

更好的分工：工程更好的进行，结构清晰易维护，代码更易管理

## MVC初体验

### 顺序

domain、utils->mapper->service->conroller

### 问题

1.警告Class XXX is never used，成功编译运行

File---->Settings—>Editor---->Code Style---->Inspections---->java—>Declaration redundancy——>unused declaration---->去掉勾

2.Post发送Json数据

Post-Body-Json

## 课后思考

### MVC模式的Web开发和嵌入式Web开发的差别

MVC将业务逻辑分为控制层和模型层，物理性垂直方向划分位3层，嵌入式开发则是水平方向上划分位两层

相比之下MVC框架模式开发更利于维护，更利于责任分工，也能更大限度重用代码，因此学习MVC模式很有必要性

而嵌入式开发则在后期维护和扩展较为困难，页面稍微多点，工作量直接起飞

### 接口定义和实现的差别及分开写的好处

定义简单的一层代码清晰易懂，实现则复杂许多

只用给别人看定义别人就能使用你写的接口而不会泄漏你的程序代码，也更利于阅读，更加强调了分工分层合作的关系

同时也利于后期的维护，修改时只用修改实现的业务逻辑

百度：接口编程，Spring事物用的java动态代理

# 2020.10.10 第三周

## 复习

Model:domain、mapper(静态数据)、service

Controller:controller

用户名访问、用户登录

接口定义实现分离

## JUnit Test

[JUnit教程](https://www.w3cschool.cn/junit/fegu1hv3.html)

### 人工测试（非程式化）

可信度低、枯燥乏味、耗费时间及人力资源大

### 自动测试（程式化）

可信度高、快速自动、耗费时间及人力资源小

### 什么是JUnit

JUnit 是一个 Java 编程语言的单元测试框架，起源于 JUnit 的一个统称为 xUnit 的单元测试框架之一。

JUnit 促进了“先测试后编码”的理念，强调建立测试数据的一段代码，可以先测试，然后再应用。

### 特点：

- JUnit 是一个开放的资源框架，用于编写和运行测试。
- 提供注释来识别测试方法。
- 提供断言来测试预期结果。
- 提供测试运行来运行测试。
- JUnit 测试允许你编写代码更快，并能提高质量。
- JUnit 优雅简洁。没那么复杂，花费时间较少。
- JUnit 测试可以自动运行并且检查自身结果并提供即时反馈。所以也没有必要人工梳理测试结果的报告。
- JUnit 测试可以被组织为测试套件，包含测试用例，甚至其他的测试套件。
- JUnit 在一个条中显示进度。如果运行良好则是绿色；如果运行失败，则变成红色。

### 什么是一个单元测试用例?

单元测试用例是一部分代码，可以确保另一端代码（方法）按预期工作。

一个正式的编写好的单元测试用例的特点是：已知输入和预期输出，即在测试执行前就已知。已知输入需要测试的先决条件，预期输出需要测试后置条件。

每一项需求至少需要两个单元测试用例：一个正检验，一个负检验。如果一个需求有子需求，每一个子需求必须至少有正检验和负检验两个测试用例。

## 单元测试

pom依赖

注解@Test @Before @After

## 页面模板 Thyneleaf

### 练习产生的问题

1.pom文件导入spring-boot-starter-thymeleaf 依赖报错

导入依赖和配置后构建项目，spring-boot-starter-thymeleaf报红

解决：Invalidate and restart

# 2020.10.15 第四周

## 静态资源访问：application路径配置

index.html默认能访问（凑巧），实则未配置不能静态访问

spring.static-locations = classpath:  ...

## 自定义全局异常错误

@RestControllerAdvice默认返回json数据

@ExceptionHandler(value=Exception.class)捕捉所有异常

1.新键包，包中新建异常处理类

2.新建error.html (Thyneleaf已经配置好)

ModelAndView.setViewName指定模板

## SpringBoot2.X过滤器

### 自定义Filter

#### 步骤：

@ServletComponentScan启动类增加注解

新建Filter类，实现对应接口

@WebFilter标记为filter被扫描

urlPatterns拦截规则

chain.doFilter方法调用实现是否放行

不放行则干点别的（返回Json）

## 自定义原生Servlet

## 注解Listener常用监听器

ServletContextListener 应用启动监听

HttpSessionLisener 会话监听

ServletRequestListener 请求监听

## SpringBoot2.X拦截器

配置拦截器WebMvcConfigurer

### 自定义拦截器

preHandle 调用Controller之前 

postHandle  调用Controller之后，渲染之前

afterCompleton 用于资源清理

## 思考

### 过滤器和拦截器比较

比如：编写，生命周期，灵活度...

1、Filter需要在web.xml中配置，依赖于Servlet；Interceptor需要在SpringMVC中配置，依赖于框架

2、在action的*生命周期*中,*拦截器*可以多次被调用,而*过滤器*只能在容器初始化时被调用一次。

3、过滤器和拦截器触发时机不一样:过滤器是在请求进入容器后，但请求进入servlet之前进行预处理的。请求结束返回也是，是在servlet处理完后，返回给前端之前。

4、拦截器(是基于Java的反射机制,而过滤器是基于函数回调。从灵活性上说拦截器功能更强大些,Filter能做的事情,都能做,而且可以在请求前,请求后执行，比较灵活

### 多个拦截器的执行过程

多个拦截器工作时，perHandle()方法会按照配置文件中的拦截器的配置顺序执行，postHandle()方法和afterCompletion方法会按照配置顺序的反序执行。

# 2020.10.22 第五周

回顾静态访问、自定义全局异常、过滤器、拦截器

## 原生JDBC访问连接数据库

缺点：每次加载驱动，代码耦合（C + c C + v大法），参数设置不灵活，结果集处理麻烦，连接资源不能复用...

## ORM框架

对数据库表和POJO(Plain Ordinary Java Object)Java对象做映射

市面上的ORM框架：Hibernate(ssh)、JPA - Spring Data JPA、Mybatis（半自动化（半ORM框架）、便于写sql）

## Mybatis 

### 简介

官方文档：(mybatis.org/mybatis-3)

免除几乎所有JDBC代码以及设置参数和获取结果集的工作

通过简单的XML或注解来配置和映射原始类型、接口和Java POJO为数据库中的记录

### 入门实践

### 出现的问题

1、连接服务器失败

解决方案，经过仔细的查错阅读，发现密码123456输成了123465

![333](C:\Users\Administrator\Desktop\333.PNG)

![](C:\Users\Administrator\Desktop\111.png)



2、服务器错误：You must configure either the server or JDBC driver (via the serverTimezone conf)

解决方案：数据库和系统时区差异所造成的，在jdbc连接的url后面加上serverTimezone=GMT即可解决问题

![222](C:\Users\Administrator\Desktop\222.PNG)

https://blog.csdn.net/iiiiiilikangshuai/article/details/98459941

3.log4配置问题org.apache.ibatis.binding.BindingException: Parameter 'mobile' not found

![img](file:///C:\Users\Administrator\AppData\Roaming\Tencent\Users\1303869726\QQ\WinTemp\RichOle\65]2LJBLE3_S3$0AQIK$%]9.png)

4.etc...

## 思考

### ORM框架和原生JDBC访问的差异点

1.ORM框架通过简单的xml配置，将sql写在XML文件中，实现业务层和数据层的分离

2.JDBC代码量大繁琐易出错，ORM建立了java对象和数据库间的映射，大大降低代码量

3.ORM底层仍是JDBC，封装了JDBC

4.直接用JDBC更安全一些，JDBC也更加灵活

# 10.29 第六周

自学复习

# 11.5 第七周

回顾：

mybatis依赖，全局配置：数据源，映射，SQL语句配置

log4j

sqlSessionFactory



# 11.12 第八周

## Spring boot疑问

IOC控制反转

依赖注入IOP
