---
title: 【SpringBoot学习之路】10.Web开发之静态资源的映射规则
date: 2018-11-20 23:11:21
tags: 
	- springboot
categories: 常用框架
---
# 简介
使用SpringBoot
1. 创建SpringBoot应用，选中我们需要的模块；
1. SpringBoot已经默认将这些场景配置好了，只需要在配置文件中指定少量配置就可以运行起来
1. 自己编写业务代码；
### 自动配置原理？
这个场景SpringBoot帮我们配置了什么？能不能修改？能修改哪些配置？能不能扩展？

```
xxxxAutoConfiguration：帮我们给容器中自动配置组件；
xxxxProperties:配置类来封装配置文件的内容；
```
# SpringBoot对静态资源的映射规则

```
@ConfigurationProperties(
    prefix = "spring.resources",
    ignoreUnknownFields = false
)
public class ResourceProperties {
//可以设置和静态资源有关的参数，缓存时间等
```

```
public class WebFluxAutoConfiguration {
    public void addResourceHandlers(ResourceHandlerRegistry registry) {
                if (!this.resourceProperties.isAddMappings()) {
                    logger.debug("Default resource handling disabled");
                } else {
                    if (!registry.hasMappingForPattern("/webjars/**")) {
                        ResourceHandlerRegistration registration = registry.addResourceHandler(new String[]{"/webjars/**"}).addResourceLocations(new String[]{"classpath:/META-INF/resources/webjars/"});
                        this.configureResourceCaching(registration);
                        this.customizeResourceHandlerRegistration(registration);
                    }
    
                    String staticPathPattern = this.webFluxProperties.getStaticPathPattern();
                    //静态资源文件夹映射
                    if (!registry.hasMappingForPattern(staticPathPattern)) {
                        ResourceHandlerRegistration registration = registry.addResourceHandler(new String[]{staticPathPattern}).addResourceLocations(this.resourceProperties.getStaticLocations());
                        this.configureResourceCaching(registration);
                        this.customizeResourceHandlerRegistration(registration);
                    }
    
                }
            }
//配置喜欢的图标            
public class WebMvcAutoConfiguration {            
            public static class FaviconConfiguration implements ResourceLoaderAware {
            private final ResourceProperties resourceProperties;
            private ResourceLoader resourceLoader;

            public FaviconConfiguration(ResourceProperties resourceProperties) {
                this.resourceProperties = resourceProperties;
            }

            public void setResourceLoader(ResourceLoader resourceLoader) {
                this.resourceLoader = resourceLoader;
            }

            @Bean
            public SimpleUrlHandlerMapping faviconHandlerMapping() {
                SimpleUrlHandlerMapping mapping = new SimpleUrlHandlerMapping();
                mapping.setOrder(-2147483647);
                //所有 **/favicon.ico
                mapping.setUrlMap(Collections.singletonMap("**/favicon.ico", this.faviconRequestHandler()));
                return mapping;
            }

            @Bean
            public ResourceHttpRequestHandler faviconRequestHandler() {
                ResourceHttpRequestHandler requestHandler = new ResourceHttpRequestHandler();
                requestHandler.setLocations(this.resolveFaviconLocations());
                return requestHandler;
            }
```
==**所有 /webjars/** ，**都去 classpath:/META-INF/resources/webjars/ 找资源；**==

webjars：以jar包的方式引入静态资源；

http://www.webjars.org/

![image](http://image.damienzhong.com/jquerywebjar.png)

http://localhost:8080/webjars/jquery/3.3.1-1/jquery.js可以直接访问到js文件内容

```
<!‐‐引入jquery‐webjar。在访问的时候只需要写webjars下面资源的名称即可‐‐>
        <dependency>
            <groupId>org.webjars</groupId>
            <artifactId>jquery</artifactId>
            <version>3.3.1-1</version>
        </dependency>
```
**=="/" 访问当前项目的任何资源，都去（静态资源的文件夹）找映射==**

```
"classpath:/META‐INF/resources/",
"classpath:/resources/",
"classpath:/static/",
"classpath:/public/"
"/"：当前项目的根路径
```
localhost:8080/abc === 去静态资源文件夹里面找abc

**==欢迎页； 静态资源文件夹下的所有index.html页面；被"/"映射；==**

localhost:8080/ 找index页面

**==所有的 **/favicon.ico 都是在静态资源文件下找；==**
