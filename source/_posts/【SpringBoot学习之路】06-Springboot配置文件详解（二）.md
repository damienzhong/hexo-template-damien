---
title: 【SpringBoot学习之路】06.Springboot配置文件详解（二）
date: 2018-11-20 23:04:50
tags: 
	- springboot
categories: 常用框架
---
# 配置文件值注入
## @Value获取值和@ConfigurationProperties获取值比较
![image](http://image.damienzhong.com/%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6%E5%8F%96%E5%80%BC%E6%AF%94%E8%BE%83.png)
> 配置文件yml还是properties他们都能获取到值
- 如果说，我们只是在某个业务逻辑中需要获取一下配置文件中的某项值，使用@Value；
- 如果说，我们专门编写了一个javaBean来和配置文件进行映射，我们就直接使用@ConfigurationProperties；
## 配置文件注入值数据校验

```
@Component
@Validated
@ConfigurationProperties(prefix = "person")
public class Person {

    /**
     * <bean class="Person">
     * <property name="lastName" value="字面量/${key}从环境变量、配置文件中获取值/#
     {SpEL}"></property>
     * <bean/>
     */

    //@Value("${person.last-name}")
    @Email
    private String lastName;
    //@Value("#{11*2}")
    private Integer age;
   // @Value("true")
    private Boolean boss;
    private Date birth;
    private Map<String,Object> maps;
    private List<Object> lists;
    private Dog dog;
```
## @PropertySource&@ImportResource&@Bean
@**PropertySource**：加载指定的配置文件；
```
@PropertySource("classpath:person.properties")
@Component
//@Validated
@ConfigurationProperties(prefix = "person")
public class Person {
```
@**ImportResource**：导入Spring的配置文件，让配置文件里面的内容生效；

Spring Boot里面没有Spring的配置文件，我们自己编写的配置文件，也不能自动识别；
想让Spring的配置文件生效，加载进来，用@ImportResource标注在一个配置类上

```
@ImportResource(locations = {"classpath:beans.xml"})
//导入Spring的配置文件让其生效
```
xml配置文件
```
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="helloService" class="com.damienzhong.springboot02config.service.HelloService"></bean>
</beans>
```
SpringBoot推荐给容器中添加组件的方式；推荐使用全注解的方式
- 配置类@Configuration------>Spring配置文件
- 使用@Bean给容器中添加组件
```
/**
 * @Configuration:指明当前类是配置类；就是替代之前的Spring配置文件
 * 在配置文件中用<bean></bean>标签要添加
 */
@Configuration
public class MyAppConfig {

    //将方法的返回值添加到容器中；容器中这个组件默认的id就是方法名
    @Bean
    public HelloService helloService(){
        System.out.println("配置类@Bean给容器中添加组件了");
        return  new HelloService();
    }
}
```
# 配置文件占位符
## 随机数

```
${random.value}、${random.int}、${random.long}
${random.int(10)}、${random.int[1024,65536]}
```
## 占位符获取之前配置的值，如果没有可以是用:指定默认值
```
person.last-name=呆萌钟${random.uuid}
person.age=${random.int}
person.boss=true
person.birth=2018/10/30
person.maps.k1=v1
person.maps.k2=v2
person.lists=zhangsan,lisi
person.dog.name=${person.hello:哈士奇}_dog
person.dog.age=2
```
