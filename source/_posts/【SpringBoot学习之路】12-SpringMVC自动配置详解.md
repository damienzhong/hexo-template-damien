---
title: 【SpringBoot学习之路】12.SpringMVC自动配置详解
date: 2018-11-21 15:59:15
tags: 
	- springboot
categories: 常用框架
---
# SpringMVC自动配置
## Spring MVC auto-configuration
Spring Boot 自动配置好了SpringMVC
以下是SpringBoot对SpringMVC的默认配置:（WebMvcAutoConfiguration）
- Inclusion of ContentNegotiatingViewResolver and BeanNameViewResolver beans.
  - 自动配置了ViewResolver（视图解析器：根据方法的返回值得到视图对象（View），视图对象决定如何渲染（转发？重定向？））
  - ContentNegotiatingViewResolver：组合所有的视图解析器的；
  - 如何定制：我们可以自己给容器中添加一个视图解析器；自动的将其组合进来；
- Support for serving static resources, including support for WebJars (see below).静态资源文件夹路径,webjars
- Static index.html support. 静态首页访问
- Custom Favicon support (see below). favicon.ico
- 自动注册了 of Converter , GenericConverter , Formatter beans.
  - Converter：转换器； public String hello(User user)：类型转换使用Converter
  - Formatter 格式化器； 2017.12.17===Date；

```
@Bean
@ConditionalOnProperty(prefix = "spring.mvc", name = "date‐format")//在文件中配置日期格式化的规则
public Formatter<Date> dateFormatter() {
    return new DateFormatter(this.mvcProperties.getDateFormat());//日期格式化组件
}
```
==**自己添加的格式化器转换器，我们只需要放在容器中即可**==
- Support for HttpMessageConverters (see below).
  - HttpMessageConverter：SpringMVC用来转换Http请求和响应的；User---Json；
  - HttpMessageConverters 是从容器中确定；获取所有的HttpMessageConverter；
  - **自己给容器中添加HttpMessageConverter，只需要将自己的组件注册容器中
（@Bean,@Component）**

```
初始化WebDataBinder；
请求数据=====JavaBean；
```
**org.springframework.boot.autoconfigure.web：web的所有自动场景；**

If you want to keep Spring Boot MVC features, and you just want to add additional MVC configuration
(interceptors, formatters, view controllers etc.) you can add your own @Configuration class of type
WebMvcConfigurerAdapter , but without @EnableWebMvc . If you wish to provide custom instances of
RequestMappingHandlerMapping , RequestMappingHandlerAdapter or ExceptionHandlerExceptionResolver
you can declare a WebMvcRegistrationsAdapter instance providing such components.
If you want to take complete control of Spring MVC, you can add your own @Configuration annotated with
@EnableWebMvc .
# 扩展SpringMVC
```
<mvc:view-controller path="/hello" view-name="success"/>
    <mvc:interceptors>
        <mvc:interceptor>
            <mvc:mapping path="/hello"/>
            <bean></bean>
        </mvc:interceptor>
    </mvc:interceptors>
    <mvc:default-servlet-handler/>
```
==**编写一个配置类（@Configuration），是WebMvcConfigurerAdapter类型；不能标注@EnableWebMvc;**==

既保留了所有的自动配置，也能用我们扩展的配置；
```
//使用WebMvcConfigurerAdapter可以来扩展SpringMVC的功能
@Configuration
public class MyMvcConfig extends WebMvcConfigurerAdapter {
    @Override
    public void addViewControllers(ViewControllerRegistry registry) {
//        super.addViewControllers(registry);
        //浏览器发送 /damienzhong 请求来到 success
        registry.addViewController("damienzhong").setViewName("success");
    }
}

```
## 原理
- WebMvcAutoConfiguration是SpringMVC的自动配置类
- 在做其他自动配置时会导入；@Import(EnableWebMvcConfiguration.class)
- 容器中所有的WebMvcConfigurer都会一起起作用
- 我们的配置类也会被调用

效果：SpringMVC的自动配置和我们的扩展配置都会起作用
## 全面接管SpringMVC
SpringBoot对SpringMVC的自动配置不需要了，所有都是我们自己配置；所有的SpringMVC的自动配置都失效了
我们需要在配置类中添加@**EnableWebMvc即可**；
```
//使用WebMvcConfigurerAdapter可以来扩展SpringMVC的功能
@EnableWebMvc
@Configuration
public class MyMvcConfig extends WebMvcConfigurerAdapter {
    @Override
    public void addViewControllers(ViewControllerRegistry registry) {
//        super.addViewControllers(registry);
        //浏览器发送 /damienzhong 请求来到 success
        registry.addViewController("damienzhong").setViewName("success");
    }
}
```
### 原理
为什么@EnableWebMvc自动配置就失效了？
- @EnableWebMvc的核心
```
@Import({DelegatingWebMvcConfiguration.class})
public @interface EnableWebMvc {
}
```
```
@Configuration
public class DelegatingWebMvcConfiguration extends WebMvcConfigurationSupport {
```

```
@Configuration
@ConditionalOnWebApplication(
    type = Type.SERVLET
)
@ConditionalOnClass({Servlet.class, DispatcherServlet.class, WebMvcConfigurer.class})
//容器中没有这个组件的时候，这个自动配置类才生效
@ConditionalOnMissingBean({WebMvcConfigurationSupport.class})
@AutoConfigureOrder(-2147483638)
@AutoConfigureAfter({DispatcherServletAutoConfiguration.class, TaskExecutionAutoConfiguration.class, ValidationAutoConfiguration.class})
public class WebMvcAutoConfiguration {
```
- @EnableWebMvc将**WebMvcConfigurationSupport**组件导入进来；
- 导入的WebMvcConfigurationSupport只是SpringMVC最基本的功能
## 如何修改SpringBoot的默认配置
### 模式
- SpringBoot在自动配置很多组件的时候，先看容器中有没有用户自己配置的（@Bean、@Component）如果有就用用户配置的，如果没有，才自动配置；如果有些组件可以有多个（ViewResolver）将用户配置的和自己默认的组合起来；
- 在SpringBoot中会有非常多的xxxConfigurer帮助我们进行扩展配置
- 在SpringBoot中会有很多的xxxCustomizer帮助我们进行定制配置