---
title: vue+springboot前后端分离实现单点登录跨域问题处理
date: 2018-11-26 15:46:01
tags: 
	- vue
	- Springboot
categories: 常用框架
---


最近在做一个后台管理系统，前端是用时下火热的vue.js，后台是基于springboot的。因为后台系统没有登录功能，但是公司要求统一登录，登录认证统一使用.net项目组的认证系统。那就意味着做单点登录咯，至于不知道什么是单点登录的同学，建议去找一下万能的度娘。

刚接到这个需求的时候，老夫心里便不屑的认为：区区登录何足挂齿，但是，开发的过程狠狠的打了我一巴掌（火辣辣的一巴掌）。。。，所以这次必须得好好记录一下这次教训，以免以后再踩这样的坑。

我面临的第一个问题是跨域，浏览器控制台直接报CORS,以我多年开发经验，我果断在后台配置了跨域配置，代码如下：


```
@Configuration
public class CorsConfiguration {

    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurerAdapter() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/**")
                        .allowedHeaders("*")
                        .allowedMethods("*")
                        .allowedOrigins("*");
            }
        };
    }
}
```


这个配置就是允许所有mapping，所有请求头，所有请求方法，所有源。改好配置之后我果断重启项目，看效果，结果发现根本没法重定向跳转到单点登录页面，看浏览器报错是跨域导致的，我先上我登录拦截器的代码


```
public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
    //用户已经登录
    if (request.getSession().getAttribute("user") != null) {
        return true;
    }
    //从单点登录返回之后的状态，本系统还不处于登录状态
    //根据code值去获取access_token，然后再根据access_token去获取用户信息，并将用户信息存到session中
    String state = request.getParameter("state");
    String uri = getUri(request);
    if (isLoginFromSSO(state)) {
        String code = request.getParameter("code");
        Object cacheUrl = request.getSession().getAttribute(state);
        if (cacheUrl == null) {
            response.sendRedirect(uri);
            return false;
        }
        HttpUtil client = new HttpUtil();
        StringBuffer sb = new StringBuffer();
        sb.append("code=").append(code)
                .append("&grant_type=").append("authorization_code")
                .append("&client_id=").append(SSOAuth.ClientID)
                .append("&client_secret=").append(SSOAuth.ClientSecret)
                .append("&redirect_uri=").append(URLEncoder.encode((String) cacheUrl));
        String resp = client.post(SSOAuth.AccessTokenUrl, sb.toString());
        Map<String, String> map = new Gson().fromJson(resp, Map.class);
        //根据access_token去获取用户信息
        String accessToken = map.get("access_token");
        HttpUtil http = new HttpUtil();
        http.addHeader("Authorization", "Bearer " + accessToken);
        String encrypt = http.get(SSOAuth.UserUrl);
        String userinfo = decryptUserInfo(encrypt);
        //封装成user对象
        User user = new Gson().fromJson(userinfo, User.class);
        request.getSession().setAttribute("user", user);
        return true;
    }
    //跳转到单点登录界面
    state = Const._SSO_LOGIN + Const.UNDERLINE + RandomUtil.getUUID();
    request.getSession().setAttribute(state, uri);
    String redirectUrl = buildAuthCodeUrl(uri, state);
    response.sendRedirect(redirectUrl);
    return false;
}
```

后面把前端vue请求后台的登录接口方式直接用


```
window.location.href=this.$api.config.baseUrl+"/system/user/login"
```

之后前端访问系统，可以直接跳转到单点登录页面。但是当我输完账号和密码点击登录后回跳到系统，发现所有的请求数据接口都无法正常访问，debug发现所有的请求都没带用户信息，被拦截器识别为未登录，所有请求无法通过。

为什么我明明登录了呀，拦截器也设置了用户信息到session啊，怎么cookies那就没了呢？再次发起请求，发现每次请求的JsessionId都不一样，查了很多资料，发现是需要在前端加一个允许带认证信息的配置


```
axios.defaults.withCredentials=true;
```

后台也需要做一个相应的配置allowCredentials(true);


```
@Bean
public WebMvcConfigurer corsConfigurer() {
    return new WebMvcConfigurerAdapter() {
        @Override
        public void addCorsMappings(CorsRegistry registry) {
            registry.addMapping("/**")
                    .allowedHeaders("*")
                    .allowedMethods("*")
                    .allowedOrigins("*").allowCredentials(true);
        }
    };
}
```

加完这个配置之后，重新执行一遍操作流程，发现登录之后能正常跳转到系统，页面数据也展示正常。

正当我以为大功告成的时候，突然点到一个页面又无法正常显示数据，好纳闷啊，赶紧F12，发现一个之前没见过的请求方式，OPTIONS请求，原来这个请求方式明明是POST呀，怎么就变成了OPTIONS了呢？于是我有点了其他几个POST的请求，发现都变成了OPTIONS请求，一脸懵逼的我赶紧查了一下OPTIONS请求的资料，网上说OPTIONS请求叫做“预检查请求”，就是在你的正式请求执行之前，浏览器会先发起预检查请求，预检查请求通过了，才能执行正式请求。看完恍然大悟，原来OPTIONS被拦截了，所以没法再执行我的POST的请求啊，那我直接让预检查请求通过就好了。只要在拦截器中加一个这个判断就好了

```
//option预检查，直接通过请求
if ("OPTIONS".equals(request.getMethod())){
    return true;
}
```

这样拦截器发现请求是预检查请求就直接通过，就可以执行接下来的POST的请求了。


