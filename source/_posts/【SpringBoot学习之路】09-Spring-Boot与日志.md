---
title: 【SpringBoot学习之路】09.Spring Boot与日志
date: 2018-11-20 23:08:33
tags: 
	- springboot
categories: 常用框架
---
# 日志框架
市场上存在非常多的日志框架。JUL（java.util.logging），JCL（Apache Commons Logging），Log4j，Log4j2，Logback、SLF4j、jboss-logging等。Spring Boot在框架内容部使用JCL，spring-boot-starter-logging采用了slf4j+logback的形式，Spring Boot也能自动适配（jul、log4j2、logback）并简化配置
![image](http://image.damienzhong.com/springboot%E6%97%A5%E5%BF%97.png)
# SLF4j使用
## 如何在系统中使用SLF4j(https://www.slf4j.org)
以后开发的时候，日志记录方法的调用，不应该来直接调用日志的实现类，而是调用日志抽象层里面的方法；
给系统里面导入slf4j的jar和 logback的实现jar
```
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
public class HelloWorld {
    public static void main(String[] args) {
        Logger logger = LoggerFactory.getLogger(HelloWorld.class);
        logger.info("Hello World");
    }
}
```
![image](https://www.slf4j.org/images/concrete-bindings.png)

每一个日志的实现框架都有自己的配置文件。使用slf4j以后，**配置文件还是做成日志实现框架自己本身的配置文件**；
## 遗留问题
a（slf4j+logback）: Spring（commons-logging）、Hibernate（jboss-logging）、MyBatis、xxxx
统一日志记录，即使是别的框架和我一起统一使用slf4j进行输出？
![image](https://www.slf4j.org/images/legacy.png)
**如何让系统中所有的日志都统一到slf4j**?
1. 将系统中其他日志框架先排除出去；
1. 用中间包来替换原有的日志框架；
1. 我们导入slf4j其他的实现
# SpringBoot日志关系
```
<dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter</artifactId>
</dependency>
```
SpringBoot使用它来做日志功能；
```
<dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-logging</artifactId>
</dependency>
```
底层依赖关系

![image](http://image.damienzhong.com/%E6%90%9C%E7%8B%97%E6%88%AA%E5%9B%BE20180131220946.png)

**总结**：
1. SpringBoot底层也是使用slf4j+logback的方式进行日志记录
1. SpringBoot也把其他的日志都替换成了slf4j；
1. 中间替换包

```
@SuppressWarnings("rawtypes")
public abstract class LogFactory {

    static String UNSUPPORTED_OPERATION_IN_JCL_OVER_SLF4J = "http://www.slf4j.org/codes.html#unsupported_operation_in_jcl_over_slf4j";

    static LogFactory logFactory = new SLF4JLogFactory();
```
![image](http://image.damienzhong.com/%E6%90%9C%E7%8B%97%E6%88%AA%E5%9B%BE20180131221411.png)
- 如果我们要引入其他框架,一定要把这个框架的默认日志依赖移除掉
- Spring框架用的是commons-logging；

```
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring‐core</artifactId>
            <exclusions>
                <exclusion>
                    <groupId>commons‐logging</groupId>
                    <artifactId>commons‐logging</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
```
==SpringBoot能自动适配所有的日志，而且底层使用slf4j+logback的方式记录日志，引入其他框架的时候，只需要把这个框架依赖的日志框架排除掉即可；==
# 日志使用
## 默认配置
SpringBoot默认帮我们配置好了日志
```
//记录器
    Logger logger = LoggerFactory.getLogger(getClass());
    @Test
    public void contextLoads() {
        //日志的级别；
        //由低到高 trace<debug<info<warn<error
        //可以调整输出的日志级别；日志就只会在这个级别以以后的高级别生效
        logger.trace("这是trace日志。。。");
        logger.debug("这是debug日志。。。");
        //SpringBoot默认给我们使用的是info级别的，没有指定级别的就用SpringBoot默认规定的级别；root级别
        logger.info("这是info日志。。。");
        logger.warn("这是warn日志。。。");
        logger.error("这是error日志。。。");
    }
```

```
日志输出格式：
%d表示日期时间，
%thread表示线程名，
%‐5level：级别从左显示5个字符宽度
%logger{50} 表示logger名字最长50个字符，否则按照句点分割。
%msg：日志消息，
%n是换行符
‐‐>
%d{yyyy‐MM‐dd HH:mm:ss.SSS} [%thread] %‐5level %logger{50} ‐ %msg%n
```
**SpringBoot修改日志的默认配置**
```
logging.level.com=trace

# 不指定路径在当前项目下生成springboot.log日志
# 可以指定完整的路径；
#logging.file=D:/springboot.log

# 在当前磁盘的根路径下创建spring文件夹和里面的log文件夹；使用 spring.log 作为默认文件
logging.path=/spring/log

# 在控制台输出的日志的格式
logging.pattern.console=%d{yyyy-MM-dd} [%thread] %-5level %logger{50} - %msg%n
# 指定文件中日志输出的格式
logging.pattern.file=file=%d{yyyy-MM-dd} === [%thread] === %-5level === %logger{50} ==== %msg%n
```
![image](http://image.damienzhong.com/springbootlog.png)
## 指定配置
给类路径下放上每个日志框架自己的配置文件即可；SpringBoot就不使用他默认配置的了
![image](http://image.damienzhong.com/springbootlog%E6%8C%87%E5%AE%9A%E9%85%8D%E7%BD%AE.png)
- logback.xml：直接就被日志框架识别了；
- logback-spring.xml：日志框架就不直接加载日志的配置项，由SpringBoot解析日志配置，可以使用SpringBoot的高级Profile功能

```
<springProfile name="staging">
    <!‐‐ configuration to be enabled when the "staging" profile is active ‐‐>
    可以指定某段配置只在某个环境下生效
</springProfile>
```

```
<appender name="stdout" class="ch.qos.logback.core.ConsoleAppender">
        <!--
        日志输出格式：
			%d表示日期时间，
			%thread表示线程名，
			%-5level：级别从左显示5个字符宽度
			%logger{50} 表示logger名字最长50个字符，否则按照句点分割。 
			%msg：日志消息，
			%n是换行符
        -->
        <layout class="ch.qos.logback.classic.PatternLayout">
            <springProfile name="dev">
                <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} ----> [%thread] ---> %-5level %logger{50} - %msg%n</pattern>
            </springProfile>
            <springProfile name="!dev">
                <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} ==== [%thread] ==== %-5level %logger{50} - %msg%n</pattern>
            </springProfile>
        </layout>
</appender>
```
==如果使用logback.xml作为日志配置文件，还要使用profile功能，会有以下错误:
no applicable action for [springProfile]==