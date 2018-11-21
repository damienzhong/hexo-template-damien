---
title: 【SpringBoot学习之路】15.错误处理机制
date: 2018-11-21 16:13:35
tags: 
	- springboot
categories: 常用框架
---
# SpringBoot默认的错误处理机制
### 默认效果
- 浏览器，返回一个默认的错误页面

![image](http://image.damienzhong.com/%E6%90%9C%E7%8B%97%E6%88%AA%E5%9B%BE20180226173408.png)
- 浏览器发送请求的请求头

![image](http://image.damienzhong.com/%E6%90%9C%E7%8B%97%E6%88%AA%E5%9B%BE20180226180347.png)

- 如果是其他客户端，默认响应一个json数据

![image](http://image.damienzhong.com/%E6%90%9C%E7%8B%97%E6%88%AA%E5%9B%BE20180226173527.png)

![image](http://image.damienzhong.com/%E6%90%9C%E7%8B%97%E6%88%AA%E5%9B%BE20180226180504.png)
## 原理
可以参照ErrorMvcAutoConfiguration,错误处理的自动配置；
给容器中添加了以下组件;
### DefaultErrorAttributes

```
//帮我们在页面共享信息；
    @Override
    public Map<String, Object> getErrorAttributes(RequestAttributes requestAttributes,
                                                  boolean includeStackTrace) {
        Map<String, Object> errorAttributes = new LinkedHashMap<String, Object>();
        errorAttributes.put("timestamp", new Date());
        addStatus(errorAttributes, requestAttributes);
        addErrorDetails(errorAttributes, requestAttributes, includeStackTrace);
        addPath(errorAttributes, requestAttributes);
        return errorAttributes;
    }
```
### BasicErrorController
处理默认/error请求

```
@Controller
@RequestMapping("${server.error.path:${error.path:/error}}")
public class BasicErrorController extends AbstractErrorController {
    @RequestMapping(produces = "text/html")//产生html类型的数据；浏览器发送的请求来到这个方法处理
    public ModelAndView errorHtml(HttpServletRequest request,
                                  HttpServletResponse response) {
        HttpStatus status = getStatus(request);
        Map<String, Object> model = Collections.unmodifiableMap(getErrorAttributes(
                request, isIncludeStackTrace(request, MediaType.TEXT_HTML)));
        response.setStatus(status.value());
//去哪个页面作为错误页面；包含页面地址和页面内容
        ModelAndView modelAndView = resolveErrorView(request, response, status, model);
        return (modelAndView == null ? new ModelAndView("error", model) : modelAndView);
    }
    @RequestMapping
    @ResponseBody //产生json数据，其他客户端来到这个方法处理；
    public ResponseEntity<Map<String, Object>> error(HttpServletRequest request) {
        Map<String, Object> body = getErrorAttributes(request,
                isIncludeStackTrace(request, MediaType.ALL));
        HttpStatus status = getStatus(request);
        return new ResponseEntity<Map<String, Object>>(body, status);
    }
```
### ErrorPageCustomizer

```
 @Value("${error.path:/error}")
 private String path = "/error"; //系统出现错误以后来到error请求进行处理；（web.xml注册的错误页面规则）
```
### DefaultErrorViewResolver

```

    @Override
    public ModelAndView resolveErrorView(HttpServletRequest request, HttpStatus status,
                                         Map<String, Object> model) {
        ModelAndView modelAndView = resolve(String.valueOf(status), model);
        if (modelAndView == null && SERIES_VIEWS.containsKey(status.series())) {
            modelAndView = resolve(SERIES_VIEWS.get(status.series()), model);
        }
        return modelAndView;
    }
    private ModelAndView resolve(String viewName, Map<String, Object> model) {
//默认SpringBoot可以去找到一个页面？ error/404
        String errorViewName = "error/" + viewName;
//模板引擎可以解析这个页面地址就用模板引擎解析
        TemplateAvailabilityProvider provider = this.templateAvailabilityProviders
                .getProvider(errorViewName, this.applicationContext);
        if (provider != null) {
//模板引擎可用的情况下返回到errorViewName指定的视图地址
            return new ModelAndView(errorViewName, model);
        }
//模板引擎不可用，就在静态资源文件夹下找errorViewName对应的页面 error/404.html
        return resolveResource(errorViewName, model);
    }
```
#### 步骤
一但系统出现4xx或者5xx之类的错误；ErrorPageCustomizer就会生效（定制错误的响应规则）；就会来到/error请求；就会被BasicErrorController处理；
- 响应页面；去哪个页面是由DefaultErrorViewResolver解析得到的；

```
    protected ModelAndView resolveErrorView(HttpServletRequest request,
                                            HttpServletResponse response, HttpStatus status, Map<String, Object> model) {
//所有的ErrorViewResolver得到ModelAndView
        for (ErrorViewResolver resolver : this.errorViewResolvers) {
            ModelAndView modelAndView = resolver.resolveErrorView(request, status, model);
            if (modelAndView != null) {
                return modelAndView;
            }
        }
        return null;
    }
```
# 定制错误响应
## 如何定制错误的页面
- 有模板引擎的情况下；error/状态码; 【将错误页面命名为 错误状态码.html 放在模板引擎文件夹里面的error文件夹下】，发生此状态码的错误就会来到 对应的页面；
- 我们可以使用4xx和5xx作为错误页面的文件名来匹配这种类型的所有错误，精确优先（优先寻找精确的状态码.html）；
- 页面能获取的信息
  - timestamp：时间戳
  - status：状态码
  - error：错误提示
  - exception：异常对象
  - message：异常消息
  - errors：JSR303数据校验的错误都在这里
- 没有模板引擎（模板引擎找不到这个错误页面），静态资源文件夹下找
- 以上都没有错误页面，就是默认来到SpringBoot默认的错误提示页面；
## 如何定制错误的json数据
### 自定义异常处理&返回定制json数据

```
@ControllerAdvice
public class MyExceptionHandler {

    @ResponseBody
    @ExceptionHandler(UserNotExistException.class)
    public Map<String,Object> handleException(Exception e){
        Map<String, Object> map = new HashMap<>();
        map.put("code","user.notexist");
        map.put("message",e.getMessage());
        return map;
    }
}

```
### 转发到/error进行自适应响应效果处理

```
  @ExceptionHandler(UserNotExistException.class)
    public String handleException(Exception e, HttpServletRequest request) {
        Map<String, Object> map = new HashMap<>();
//传入我们自己的错误状态码 4xx 5xx，否则就不会进入定制错误页面的解析流程
/**
 * Integer statusCode = (Integer) request
 .getAttribute("javax.servlet.error.status_code");
 */
        request.setAttribute("javax.servlet.error.status_code", 500);
        map.put("code", "user.notexist");
        map.put("message", e.getMessage());
//转发到/error
        return "forward:/error";
    }
}
```
### 将我们的定制数据携带出去
出现错误以后，会来到/error请求，会被BasicErrorController处理，响应出去可以获取的数据是由getErrorAttributes得到的（是AbstractErrorController（ErrorController）规定的方法）；
- 完全来编写一个ErrorController的实现类【或者是编写AbstractErrorController的子类】，放在容器中；
- 页面上能用的数据，或者是json返回能用的数据都是通过errorAttributes.getErrorAttributes得到；容器中DefaultErrorAttributes.getErrorAttributes()；默认进行数据处理的；

```
//给容器中加入我们自己定义的ErrorAttributes
@Component
public class MyErrorAttributes extends DefaultErrorAttributes {

    //返回值的map就是页面和json能获取的所有字段
    @Override
    public Map<String, Object> getErrorAttributes(WebRequest requestAttributes, boolean includeStackTrace) {
        Map<String, Object> map = super.getErrorAttributes(requestAttributes, includeStackTrace);
        map.put("company","damienzhong");

        //我们的异常处理器携带的数据
        Map<String,Object> ext = (Map<String, Object>) requestAttributes.getAttribute("ext", 0);
        map.put("ext",ext);
        return map;
    }
}
```
最终的效果：响应是自适应的，可以通过定制ErrorAttributes改变需要返回的内容，