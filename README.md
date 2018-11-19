# hexo-template-damien
hexo-template-damien是基于hexo-theme-snippet主题搭建的hexo博客模板。

如果本博客模板能帮助到你，请动动手指 [Star](https://github.com/damienzhong/damienzhong.github.io/stargazers) 支持一下

![image](https://camo.githubusercontent.com/56ff6555ec914189404da207cda4c6655e8ea55f/68747470733a2f2f7777772e7472617669732d63692e6f72672f7368656e6c6979616e672f6865786f2d7468656d652d736e69707065742e7376673f6272616e63683d6d6173746572)
![image](https://camo.githubusercontent.com/0e161c21509027b7970591b20c09693346c5e7bc/68747470733a2f2f696d672e736869656c64732e696f2f72656164746865646f63732f7069702f737461626c652e737667)
![image](https://camo.githubusercontent.com/bcfd764f5caed2fdde34e4b20c0c28b843ca1eb9/68747470733a2f2f636f6465626561742e636f2f6261646765732f36656632646364322d616639302d343065302d393632382d616336383934343166373734)
![image](https://camo.githubusercontent.com/03d6009dd8d062508d0167643ae7ff9c3230a0a5/68747470733a2f2f696d672e736869656c64732e696f2f6d61696e74656e616e63652f7965732f323031382e737667)
![image](https://camo.githubusercontent.com/1c13342ee63f0ef42bcb85c91f38c777ae7396b3/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f496d67426f742d6275696c642d627269676874677265656e2e737667)
![image](https://camo.githubusercontent.com/9a3ed64801222d45980fb085e7e059e31314d335/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6865786f2d253345253344253230332e302d626c75652e737667)
![image](https://camo.githubusercontent.com/890acbdcb87868b382af9a4b1fac507b9659d9bf/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d4d49542d626c75652e737667)

[主题效果演示](https://damienzhong.github.io/)

![image](http://image.damienzhong.com/687474703a2f2f3778707732622e636f6d312e7a302e676c622e636c6f7564646e2e636f6d2f6865786f2d73696e707065742f696d672f736e69707065742d73637265656e73686f7473313030302e6a7067.jpg)
# 基础篇
> 如果你在此之前使用的是 Hexo 2.x 版本，为了避免未知的错误，请备份好数据，或者建立新的博客目录
> "主题目录" => themes\hexo-theme-snippet, "Hexo根目录" => 项目主目录; "主题配置" => themes\hexo-theme-snippet\_config.yml, "Hexo配置" => 项目主目录下_config.yml

## 环境搭建
需要Node.js 环境、Git 环境以及 Hexo 
## 下载模板
有两种方式获取本主题--下载 *.zip 文件和通过 git方式：
### 下载zip包
下载该压缩文件之后直接解压即可。
### Git方式
```
git clone https://github.com/damienzhong/hexo-template-damien.git
```
## 安装插件
进入项目目录hexo-template-damien，打开Git Bash执行如下命令安装所需插件

```
npm install hexo --save
```
如果你尚未安装或者不了解 Hexo，请参考 [官方教程](https://hexo.io/zh-cn/docs/index.html) 进行了解以及安装。

```
npm i hexo-renderer-ejs hexo-renderer-less hexo-deployer-git -S
```
## 部署博客
以下操作都是在Git Bash中执行
#### 清空hexo静态文件和缓存，并重新生成
```
hexo clean && hexo g  //清空缓存并生成静态文件
```
#### 本地预览，确没有问题再进行发布
```
hexo s  //启动本地服务默认
```
#### 发布到github
```
hexo d 或者 gulp deploy  //部署发布
```
# 主题篇
## 主题配置

```
## menu -- 导航菜单显示{[@page:名字,@url:地址,@icon:图标]}
menu:
  - page: home
    url: /
    icon: fa-home

## favicon -- 网站图标位置{@favicon}
favicon: /favicon.ico

## rss --rss文件位置{@rss}
rss: /atom.xml


# 各个小工具的设置

## widgets -- 6个左边小工具{@widgets:[notification,category,archive,tagcloud,friends]}
widgets:
  - search
  - notification
  - social
  - category
  - archive
  - tagcloud
  - friends

# 各个小工具的设置

## 搜索
jsonContent:
  searchLocal: true // 是否启用本地搜索
  searchGoogle: true //是否启用谷歌搜索
  posts:
    title: true
    text: true
    content: true
    categories: false
    tags: false

## notification config --网站公告设置,支持 html 和 纯文本
notification: |-
            <p>
                支持本博客：<a href="https://github.com/damienzhong/damienzhong.github.io/stargazers" title="star me" target="_blank">Star一下</a> <br/>
                优酷播单：<a href="https://i.youku.com/i/UNDE3MDU5OTg3Mg==/playlists">优酷播单</a><br/>
                淘宝男装店：<a href="https://shop72495432.taobao.com/search.htm?spm=a1z10.1-c.0.0.25343b46cBwhQs&search=y">DM潮人社区</a><br/>
                QQ交流群：<a href="https://jq.qq.com/?_wv=1027&k=5xgZ7E0" title="" target="_blank">点击加入群聊【呆萌钟技术交流群】</a> 
            </p>

## 社交设置{@name:社交工具名字，@icon:社交工具图标，@href:设置工具链接} [参考图标](http://fontawesome.io/icons/)
social:
  - name: Github
    icon: git
    href: //github.com/damienzhong

## 文章分类设置{@cate_config:{@show_count:是否显示数字，@show_current: 是否高亮当前category}}
cate_config:
   show_count: true
   show_current: true

## 文章归档设置{@arch_config:/*参数参考：https://hexo.io/zh-cn/docs/helpers.html#list-archives*/}
## 推荐组合方式：[{type: 'monthly',format: 'YYYY年MM月'},{type: 'yearly',format: 'YYYY年'}]
arch_config:
   type: 'monthly'
   format: 'YYYY年MM月'
   show_count: true
   order: -1

## 标签云设置{/*参数参考：http://www.goat1000.com/tagcanvas-options.php */}
tagcloud:
  tag3d: false // 是否启用3D标签云
  textColour: '#444' // 字体颜色
  outlineMethod: 'block' // 选中模式(outline|classic|block|colour|size|none)
  outlineColour: '#FFDAB9' // 选中模式的颜色
  interval: 30 // 动画帧之间的时间间隔，值越大，转动幅度越大
  freezeActive: true // 选中的标签是否继续滚动
  frontSelect: true // 不选标签云后部的标签
  reverse: true // 是否反向触发
  wheelZoom: false // 是否启用鼠标滚轮

## 友链设置{@链接名称：链接地址{@links:[,,,]}}
links:
  - Hexo官网: https://hexo.io/zh-cn/


# 主题自定义个性化配置

## 网站宣传语{@branding：网站宣传语(不设置显示本地图片)}
branding: 从未如此简单有趣

## 设置banner背景图片{@img:imgUrl自定义图片地址,主题默认{"静态背景":"banner.jpg"},{"动态背景":"banner2.jpg"}}
banner:
  img: imgUrl

## 设置carousel{@img:图片地址,@url:点击跳转链接(默认值:"javascript:")}
carousel:
  img: 'img/head-img.jpg'
  url: 'javascript:'

## 首页列表底部面板{@homePanel: 是否开启}
homePanel: true

## 首页文章列表缩略图
### 加载规则: 自定义文章缩略图(在Front-matter中添加的'img'字段) > 文章内的图片 > defaultImgs(随机获取) > 无图模式列表

## 自定义随机图片
defaultImgs:
  - http://www.example.jpg //远程图片链接示例
  - /img/default-1.jpg //本地图片链接示例

### 文章摘要{@摘要显示优先级：自定义摘要 > 自动截取摘要 }
### 自定义摘要范围{@<!--more-->:截取more之前的内容为摘要}
### 自动截取摘要{@excerptLength:自动截取文章前多少个字为摘要，不配置默认：120字}
excerptLength: 120

## 是否开启文章目录
toc: true

## 代码高亮配置{@highlightTheme: 主题名称,(配置暂时不可用，后续开发中…)}

highlightTheme: default //TODO

## 文章过期提醒功能 {@warning:{days:临界天数(默认300天,设置0关闭功能),text:提醒文字/*%d为过期总天数占位符*/}}
warning:
  days: 300
  text: '本文于%d天之前发表，文中内容可能已经过时。'

## 文章内声明{@declaration: {enable:是否开启,title:声明标题,tip:提示内容}}
declaration:
  enable: true
  title: '转载声明'
  tip: |-
      商业转载请联系作者获得授权,非商业转载请注明出处 © <a href="" target="_blank">呆萌钟</a>

## 文章打赏{@reward: {alipay:支付宝打赏,wepay:微信打赏,tip:打赏提示语; 链接都为空,关闭打赏功能}}
reward:
  alipay: ''
  wepay: '../img/reward-wepay.jpg'
  tip: 赞赏是不耍流氓的鼓励


## 主题评论

### gitment
gitment:
  enable: false
  owner:
  repo:
  client_id:
  client_secret:
  labels:
  perPage:
  maxCommentHeight:

### 来必力(默认选项)
livere:
  enable: true
  livere_uid:

### 友言评论(服务不稳定，经常无法加载)
uyan:
  enable: false
  uyan_id:

### Disqus评论(需要翻墙，或者搭建代理)
disqus:
  enable: false
  shortname: snippet
  count: false

### 畅言评论(需要ICP备案)
changyan:
  enable: false
  appid:
  conf:

### Valine评论 参考网站: [valine评论](https://valine.js.org/)
valine:
  enable: true
  appId:
  appKey:
  placeholder: 说点什么吧
  notify: false // 邮件通知
  verify: false // 验证码
  avatar: mm // avatar头像
  meta: nick,mail // 输入框内容，可选值nick,mail,link
  pageSize: 10

## 网站访客统计 [不蒜子统计](http://busuanzi.ibruce.info/)
visit_counter:
   site: true // 总访问量和访问人数统计
   page: true // 文章阅读量统计

## 网站访问统计

### 网盟CNZZ统计 参考网站: [网盟CNZZ](http://www.umeng.com/)
cnzz_anaylytics:

### 百度统计 参考网站: [百度统计](https://tongji.baidu.com/)
baidu_anaylytics:

### 谷歌统计 参考网站：[谷歌统计](https://www.google-analytics.com/)
google_anaylytics:

### 腾讯分析 参考网站：[腾讯分析](http://ta.qq.com/)
tencent_analytics:

### 百度站点认证
baidu-site-verification:

### 百度自动推送(@baidu_push: 是否启用百度自动推送)  参考网站: [百度站长资源](https://ziyuan.baidu.com/college/courseinfo?id=267&page=2#h2_article_title18)
baidu_push:

## ICON配置 (不配则启用本地Font Icon)
fontAwesome: //cdn.bootcss.com/font-awesome/4.7.0/css/font-awesome.min.css

## 网站主题配置
since: 2017  //建站时间
robot: 'all'  //控制搜索引擎的抓取和索引编制行为，默认为all
version: 1.2.1  //当前主题版本号
```
## 使用技巧及功能扩展
1.修改新增文章Front-matter模板,修改scaffolds目录下的post.md模板
> 模板文件内部不要保留注释部分,关键词后面请使用英文冒号

```
 ---
  title: {{ title }} // 标题
  date: {{ date }}   // 时间
  categories: ['分类1','分类2'] // 分类
  tags: ['标签1','标签2']       // 标签
  comments: false    // 是否开启评论
  img:               // 自定义缩略图
  ---
```
2.启用站内本地搜索功能
如果要使用本地站点搜索，必须安装插件hexo-generator-json-content来创建本地搜索json文件

```
npm i hexo-generator-json-content@2.2.0 -S
```
然后修改主题配置_config.yml文件下jsonContent相关参数。