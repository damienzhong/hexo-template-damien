---
title: 【SpringBoot学习之路】02.Hello World
date: 2018-11-20 18:26:20
tags: 
	- springboot
categories: 常用框架
---
# 功能
浏览器发送hello请求，服务器接受请求并处理，响应Hello World字符串
### 创建一个maven工程
### 导入spring boot相关的依赖

```
   <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.0.5.RELEASE</version>
    </parent>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>
```
### 编写一个主程序

```
/**
 * @SpringBootApplication 来标注一个主程序类，说明这是一个Spring Boot应用
 */
@SpringBootApplication
public class HelloWorldMainApplication {
    // Spring应用启动起来
    public static void main(String[] args) {
        SpringApplication.run(HelloWorldMainApplication.class,args);
    }
}
```
- 启动该主程序，能运行起来则成功。
### 编写相关的Controller

```
@Controller
public class HelloController {

    @ResponseBody
    @RequestMapping("/hello")
    public String hello() {
        return "Hello World!";
    }
}
```
### 运行主程序测试
![image](http://image.damienzhong.com/springboothello.png)
## 简化部署
```
<!--这个插件，可以将应用打包成一个可执行的jar包-->
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
```
- 将这个应用打成jar包
![image](http://image.damienzhong.com/package%E6%89%93%E5%8C%85.png)
- 先将IDEA的项目停止运行
- 找到刚才package打包生成的jar包
- 直接使用java -jar的命令进行执行

![image](http://image.damienzhong.com/springbo.png)