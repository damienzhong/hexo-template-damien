---
title: 【SpringBoot学习之路】13.设置默认访问首页
date: 2018-11-21 16:04:01
tags: 
	- springboot
categories: 常用框架
---

```
//使用WebMvcConfigurerAdapter可以来扩展SpringMVC的功能
//@EnableWebMvc
@Configuration
public class MyMvcConfig extends WebMvcConfigurerAdapter {
    //方式一
    @Override
    public void addViewControllers(ViewControllerRegistry registry) {
//        super.addViewControllers(registry);
        //浏览器发送 /damienzhong 请求来到 success
        registry.addViewController("damienzhong").setViewName("success");
    }

    //方式二
    @Bean
    public WebMvcConfigurerAdapter webMvcConfigurerAdapter(){
        WebMvcConfigurerAdapter webMvcConfigurerAdapter = new WebMvcConfigurerAdapter() {
            @Override
            public void addViewControllers(ViewControllerRegistry registry) {
                registry.addViewController("/").setViewName("login");
                registry.addViewController("/index").setViewName("login");
                registry.addViewController("/login").setViewName("login");
            }
        };
        return  webMvcConfigurerAdapter;
    }
}

```
