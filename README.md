# hexo-template-damien
hexo-template-damien�ǻ���hexo-theme-snippet������hexo����ģ�塣

���������ģ���ܰ������㣬�붯����ָ [Star](https://github.com/damienzhong/damienzhong.github.io/stargazers) ֧��һ��

![image](https://camo.githubusercontent.com/56ff6555ec914189404da207cda4c6655e8ea55f/68747470733a2f2f7777772e7472617669732d63692e6f72672f7368656e6c6979616e672f6865786f2d7468656d652d736e69707065742e7376673f6272616e63683d6d6173746572)
![image](https://camo.githubusercontent.com/0e161c21509027b7970591b20c09693346c5e7bc/68747470733a2f2f696d672e736869656c64732e696f2f72656164746865646f63732f7069702f737461626c652e737667)
![image](https://camo.githubusercontent.com/bcfd764f5caed2fdde34e4b20c0c28b843ca1eb9/68747470733a2f2f636f6465626561742e636f2f6261646765732f36656632646364322d616639302d343065302d393632382d616336383934343166373734)
![image](https://camo.githubusercontent.com/03d6009dd8d062508d0167643ae7ff9c3230a0a5/68747470733a2f2f696d672e736869656c64732e696f2f6d61696e74656e616e63652f7965732f323031382e737667)
![image](https://camo.githubusercontent.com/1c13342ee63f0ef42bcb85c91f38c777ae7396b3/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f496d67426f742d6275696c642d627269676874677265656e2e737667)
![image](https://camo.githubusercontent.com/9a3ed64801222d45980fb085e7e059e31314d335/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6865786f2d253345253344253230332e302d626c75652e737667)
![image](https://camo.githubusercontent.com/890acbdcb87868b382af9a4b1fac507b9659d9bf/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d4d49542d626c75652e737667)

[����Ч����ʾ](https://damienzhong.github.io/)

![image](http://image.damienzhong.com/687474703a2f2f3778707732622e636f6d312e7a302e676c622e636c6f7564646e2e636f6d2f6865786f2d73696e707065742f696d672f736e69707065742d73637265656e73686f7473313030302e6a7067.jpg)
# ����ƪ
> ������ڴ�֮ǰʹ�õ��� Hexo 2.x �汾��Ϊ�˱���δ֪�Ĵ����뱸�ݺ����ݣ����߽����µĲ���Ŀ¼
> "����Ŀ¼" => themes\hexo-theme-snippet, "Hexo��Ŀ¼" => ��Ŀ��Ŀ¼; "��������" => themes\hexo-theme-snippet\_config.yml, "Hexo����" => ��Ŀ��Ŀ¼��_config.yml

## �����
��ҪNode.js ������Git �����Լ� Hexo 
## ����ģ��
�����ַ�ʽ��ȡ������--���� *.zip �ļ���ͨ�� git��ʽ��
### ����zip��
���ظ�ѹ���ļ�֮��ֱ�ӽ�ѹ���ɡ�
### Git��ʽ
```
git clone https://github.com/damienzhong/hexo-template-damien.git
```
## ��װ���
������ĿĿ¼hexo-template-damien����Git Bashִ���������װ������

```
npm install hexo --save
```
�������δ��װ���߲��˽� Hexo����ο� [�ٷ��̳�](https://hexo.io/zh-cn/docs/index.html) �����˽��Լ���װ��

```
npm i hexo-renderer-ejs hexo-renderer-less hexo-deployer-git -S
```
## ���𲩿�
���²���������Git Bash��ִ��
#### ���hexo��̬�ļ��ͻ��棬����������
```
hexo clean && hexo g  //��ջ��沢���ɾ�̬�ļ�
```
#### ����Ԥ����ȷû�������ٽ��з���
```
hexo s  //������ط���Ĭ��
```
#### ������github
```
hexo d ���� gulp deploy  //���𷢲�
```
# ����ƪ
## ��������

```
## menu -- �����˵���ʾ{[@page:����,@url:��ַ,@icon:ͼ��]}
menu:
  - page: home
    url: /
    icon: fa-home

## favicon -- ��վͼ��λ��{@favicon}
favicon: /favicon.ico

## rss --rss�ļ�λ��{@rss}
rss: /atom.xml


# ����С���ߵ�����

## widgets -- 6�����С����{@widgets:[notification,category,archive,tagcloud,friends]}
widgets:
  - search
  - notification
  - social
  - category
  - archive
  - tagcloud
  - friends

# ����С���ߵ�����

## ����
jsonContent:
  searchLocal: true // �Ƿ����ñ�������
  searchGoogle: true //�Ƿ����ùȸ�����
  posts:
    title: true
    text: true
    content: true
    categories: false
    tags: false

## notification config --��վ��������,֧�� html �� ���ı�
notification: |-
            <p>
                ֧�ֱ����ͣ�<a href="https://github.com/damienzhong/damienzhong.github.io/stargazers" title="star me" target="_blank">Starһ��</a> <br/>
                �ſᲥ����<a href="https://i.youku.com/i/UNDE3MDU5OTg3Mg==/playlists">�ſᲥ��</a><br/>
                �Ա���װ�꣺<a href="https://shop72495432.taobao.com/search.htm?spm=a1z10.1-c.0.0.25343b46cBwhQs&search=y">DM��������</a><br/>
                QQ����Ⱥ��<a href="https://jq.qq.com/?_wv=1027&k=5xgZ7E0" title="" target="_blank">�������Ⱥ�ġ������Ӽ�������Ⱥ��</a> 
            </p>

## �罻����{@name:�罻�������֣�@icon:�罻����ͼ�꣬@href:���ù�������} [�ο�ͼ��](http://fontawesome.io/icons/)
social:
  - name: Github
    icon: git
    href: //github.com/damienzhong

## ���·�������{@cate_config:{@show_count:�Ƿ���ʾ���֣�@show_current: �Ƿ������ǰcategory}}
cate_config:
   show_count: true
   show_current: true

## ���¹鵵����{@arch_config:/*�����ο���https://hexo.io/zh-cn/docs/helpers.html#list-archives*/}
## �Ƽ���Ϸ�ʽ��[{type: 'monthly',format: 'YYYY��MM��'},{type: 'yearly',format: 'YYYY��'}]
arch_config:
   type: 'monthly'
   format: 'YYYY��MM��'
   show_count: true
   order: -1

## ��ǩ������{/*�����ο���http://www.goat1000.com/tagcanvas-options.php */}
tagcloud:
  tag3d: false // �Ƿ�����3D��ǩ��
  textColour: '#444' // ������ɫ
  outlineMethod: 'block' // ѡ��ģʽ(outline|classic|block|colour|size|none)
  outlineColour: '#FFDAB9' // ѡ��ģʽ����ɫ
  interval: 30 // ����֮֡���ʱ�����ֵԽ��ת������Խ��
  freezeActive: true // ѡ�еı�ǩ�Ƿ��������
  frontSelect: true // ��ѡ��ǩ�ƺ󲿵ı�ǩ
  reverse: true // �Ƿ��򴥷�
  wheelZoom: false // �Ƿ�����������

## ��������{@�������ƣ����ӵ�ַ{@links:[,,,]}}
links:
  - Hexo����: https://hexo.io/zh-cn/


# �����Զ�����Ի�����

## ��վ������{@branding����վ������(��������ʾ����ͼƬ)}
branding: ��δ��˼���Ȥ

## ����banner����ͼƬ{@img:imgUrl�Զ���ͼƬ��ַ,����Ĭ��{"��̬����":"banner.jpg"},{"��̬����":"banner2.jpg"}}
banner:
  img: imgUrl

## ����carousel{@img:ͼƬ��ַ,@url:�����ת����(Ĭ��ֵ:"javascript:")}
carousel:
  img: 'img/head-img.jpg'
  url: 'javascript:'

## ��ҳ�б�ײ����{@homePanel: �Ƿ���}
homePanel: true

## ��ҳ�����б�����ͼ
### ���ع���: �Զ�����������ͼ(��Front-matter����ӵ�'img'�ֶ�) > �����ڵ�ͼƬ > defaultImgs(�����ȡ) > ��ͼģʽ�б�

## �Զ������ͼƬ
defaultImgs:
  - http://www.example.jpg //Զ��ͼƬ����ʾ��
  - /img/default-1.jpg //����ͼƬ����ʾ��

### ����ժҪ{@ժҪ��ʾ���ȼ����Զ���ժҪ > �Զ���ȡժҪ }
### �Զ���ժҪ��Χ{@<!--more-->:��ȡmore֮ǰ������ΪժҪ}
### �Զ���ȡժҪ{@excerptLength:�Զ���ȡ����ǰ���ٸ���ΪժҪ��������Ĭ�ϣ�120��}
excerptLength: 120

## �Ƿ�������Ŀ¼
toc: true

## �����������{@highlightTheme: ��������,(������ʱ�����ã����������С�)}

highlightTheme: default //TODO

## ���¹������ѹ��� {@warning:{days:�ٽ�����(Ĭ��300��,����0�رչ���),text:��������/*%dΪ����������ռλ��*/}}
warning:
  days: 300
  text: '������%d��֮ǰ������������ݿ����Ѿ���ʱ��'

## ����������{@declaration: {enable:�Ƿ���,title:��������,tip:��ʾ����}}
declaration:
  enable: true
  title: 'ת������'
  tip: |-
      ��ҵת������ϵ���߻����Ȩ,����ҵת����ע������ ? <a href="" target="_blank">������</a>

## ���´���{@reward: {alipay:֧��������,wepay:΢�Ŵ���,tip:������ʾ��; ���Ӷ�Ϊ��,�رմ��͹���}}
reward:
  alipay: ''
  wepay: '../img/reward-wepay.jpg'
  tip: �����ǲ�ˣ��å�Ĺ���


## ��������

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

### ������(Ĭ��ѡ��)
livere:
  enable: true
  livere_uid:

### ��������(�����ȶ��������޷�����)
uyan:
  enable: false
  uyan_id:

### Disqus����(��Ҫ��ǽ�����ߴ����)
disqus:
  enable: false
  shortname: snippet
  count: false

### ��������(��ҪICP����)
changyan:
  enable: false
  appid:
  conf:

### Valine���� �ο���վ: [valine����](https://valine.js.org/)
valine:
  enable: true
  appId:
  appKey:
  placeholder: ˵��ʲô��
  notify: false // �ʼ�֪ͨ
  verify: false // ��֤��
  avatar: mm // avatarͷ��
  meta: nick,mail // ��������ݣ���ѡֵnick,mail,link
  pageSize: 10

## ��վ�ÿ�ͳ�� [������ͳ��](http://busuanzi.ibruce.info/)
visit_counter:
   site: true // �ܷ������ͷ�������ͳ��
   page: true // �����Ķ���ͳ��

## ��վ����ͳ��

### ����CNZZͳ�� �ο���վ: [����CNZZ](http://www.umeng.com/)
cnzz_anaylytics:

### �ٶ�ͳ�� �ο���վ: [�ٶ�ͳ��](https://tongji.baidu.com/)
baidu_anaylytics:

### �ȸ�ͳ�� �ο���վ��[�ȸ�ͳ��](https://www.google-analytics.com/)
google_anaylytics:

### ��Ѷ���� �ο���վ��[��Ѷ����](http://ta.qq.com/)
tencent_analytics:

### �ٶ�վ����֤
baidu-site-verification:

### �ٶ��Զ�����(@baidu_push: �Ƿ����ðٶ��Զ�����)  �ο���վ: [�ٶ�վ����Դ](https://ziyuan.baidu.com/college/courseinfo?id=267&page=2#h2_article_title18)
baidu_push:

## ICON���� (���������ñ���Font Icon)
fontAwesome: //cdn.bootcss.com/font-awesome/4.7.0/css/font-awesome.min.css

## ��վ��������
since: 2017  //��վʱ��
robot: 'all'  //�������������ץȡ������������Ϊ��Ĭ��Ϊall
version: 1.2.1  //��ǰ����汾��
```
## ʹ�ü��ɼ�������չ
1.�޸���������Front-matterģ��,�޸�scaffoldsĿ¼�µ�post.mdģ��
> ģ���ļ��ڲ���Ҫ����ע�Ͳ���,�ؼ��ʺ�����ʹ��Ӣ��ð��

```
 ---
  title: {{ title }} // ����
  date: {{ date }}   // ʱ��
  categories: ['����1','����2'] // ����
  tags: ['��ǩ1','��ǩ2']       // ��ǩ
  comments: false    // �Ƿ�������
  img:               // �Զ�������ͼ
  ---
```
2.����վ�ڱ�����������
���Ҫʹ�ñ���վ�����������밲װ���hexo-generator-json-content��������������json�ļ�

```
npm i hexo-generator-json-content@2.2.0 -S
```
Ȼ���޸���������_config.yml�ļ���jsonContent��ز�����