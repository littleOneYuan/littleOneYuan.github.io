---
layout: post
title: 使用github pages+Jekyll模板搭建博客（网页小白）
date: 2020-02-10 15:32:24.000000000 +09:00
---

>写在前面：本人大三计算机相关专业，此前没有接触过网页相关知识，最近通过互联网资源使用**github pages+Jekyll模板**搭建了一个博客，这篇文章，我将一步一步演示过程，方便和我一样的小白进行学习交流。
***这是本人的第一篇博客，有什么问题还希望大家可以告诉我。***

>此文章是由CSDN编写，图片无法显示，我已经删除，且有些格式CSDN特有，这里观看不方便
网址：https://blog.csdn.net/weixin_43871601/article/details/104248805

### 一、前提准备
	拥有自己的github以及初识git版本管理软件。
==推荐学习(强烈推荐）：[廖雪峰老师的Git教程](https://www.liaoxuefeng.com/wiki/896043488029600)==
==强烈建议有一定Git基础的同学继续向下学习，也可以先向下看==

1. 下载git并安装：[官网地址](https://git-scm.com/downloads)
2. 注册github账号：[github](https://github.com/)
注册过程略，由于是外网，访问会较慢，邮箱验证码也比较慢，耐心等待即可。
### 二、创建github pages仓库
1. 右上角选择New repository
2. 按照 ==用户名.github.io==的格式创建仓库名
TIPS：也可是创建为 ==用户名.github.com（推荐此种命名方式）==
我开始使用的io结尾，访问的时候可能会出现无响应。

### 三、创建本地仓库
1. 本地准备 
在本地磁盘中创建一个空文件夹，用于保存个人博客网站的内容。
2. 由于Github Pages基于Jekyll构建，Jekyll 可以帮助我们把纯文本转换为静态博客网站，帮助我们不了解网页以及相关知识的小白可以轻松入手。
你可以在[JekyllThemes](http://jekyllthemes.org/page5/)找到喜欢的主题，也可以在Github中找其他人的。
[这是](https://github.com/onevcat/vno-jekyll)我使用的主题。以ZIP格式下载即可。
下载完成后解压缩到刚刚创建的文件夹。
3. ==搭建Jekyll环境（重要）==

==安装Ruby==
 - Linux/UNIX平台，可以使用第三方工具（如[rbenv](https://github.com/rbenv/rbenv)或[RVM](http://rvm.io/)）或使用系统中的包管理系统。
- macOS平台，可以使用第三方工具（如[rbenv](https://github.com/rbenv/rbenv)或[RVM](http://rvm.io/)）。
- Windows平台，可以使用[RubyInstaller](https://rubyinstaller.org/)。
由于是外网，下载速度十分缓慢，RubyInstaller的百度云下载地址为：
链接：[https://pan.baidu.com/s/13GUdkwVXprgCkh6GUUlT6w](https://pan.baidu.com/s/13GUdkwVXprgCkh6GUUlT6w) 
提取码：op31
（os:百度云盘emmm没有会员也慢。。耐心等吧）

==安装Jekyll==
打开cmd运行：
<kbd>gem install jekyll</kbd>

 ==安装Jekyll bundle==
<kbd>gem install jekyll bundle</kbd>
（以上下载速度均 比较缓慢，请耐心等待，若出现失败，则再次重新输入命令继续下载，换个时段或者换个网络）

4. 在创建的本地文件夹中，右击选择<kbd>git bash here</kbd>

- 若没有出现该选择，则是git安装出现了问题。
- 引入Bundle来管理项目中的所有Gem依赖
执行命令：<kbd>bundle install</kbd>
- 此时可能会出现版本兼容错误：

```ruby
find_spec_for_exe': can't find gem bundler (>= 0.a) 
(Gem::GemNotFoundException)
```
通过上网查阅资料得到解决办法：
在copy的博客模板中Gemfile.lock的文件（就是你刚刚解压的，用搜索文件名可以找到）中，最后<kbd>BUNDLED WITH </kbd>下面的版本改成与自己安装的bundle 版本一致即可。
* 如何查看自己下载的bundle版本呢?
在cmd中输入<kbd>bundle -v</kbd>即可查看。

5. 启动Jekyll服务
<kbd>bundle exec jekyll serve</kbd>
- 可能会出现编码错误：
```ruby
Error:  Invalid GBK character "\xE2" on line 10
```
* 解决办法：
在安装的<kbd>...Ruby2.3.3\lib\ruby\gems\2.3.0\gems\sass-3.7.2\lib\sass.rb</kbd>文件用记事本打开，在最后另加一空白行，输入：
<kbd>Encoding.default_external = Encoding.find('utf-8')</kbd>

- 再次使用命令启动Jekyll服务
出现：

```ruby
  Server address : http://127.0.0.1:4000
Server running... press ctrl -c to stop
```

- 表示服务启动成功，使用浏览器访问[http://127.0.0.1:4000](http://127.0.0.1:4000)
即可看到自己的博客。
### 四、推送到远程仓库
- 所有文件推送到远程仓库

1. 若有git基础且已经连接到远程仓库的同学可以直接使用以下代码：
```powershell
git add .
git commit -m "apply theme"
git push origin master
```
2. 若不会连接到远程仓库的同学
可查看[廖老师的教程](https://www.liaoxuefeng.com/wiki/896043488029600/898732864121440)
（OS：老师讲的比我清楚，我直接断章取义可能会出现一些问题）
### 五、管理博客
- 别忘了每次修改、添加本地仓库文件之后，要推送到远程github仓库才可以被别人看得到。
1.修改主题
用记事本打开本地文件夹的<kbd>_config.yml</kbd>文件

如图所示修改相应个人信息即可，即使没有网页知识的小伙伴也没有关系，依葫芦画瓢很简单的，可以看得懂。
2.博客文章
在仓库文件夹下，进入<kbd>_posts</kbd>目录，所有的文章都必须放在<kbd>_posts</kbd>文件夹下，大家可以访问 [Jekyll-目录结构](http://jekyllcn.com/docs/structure/) 详细了解每个文件夹的功能。
文件格式为：<kbd>yyyy-MM-dd-filename.md</kbd>即markdown文档。
（你现在眼前的这篇博客也是markdown文档，具体可百度搜一下。目前网上也有很多markdown的编辑软件，你也可以使用在线的编辑器。）
- 再次提醒：修改、添加完文件记得PUSH到远程仓库哦。
### 六、效果展示
我的网址：[https://yanwd628.github.io/](https://yanwd628.github.io/)
（还没怎么写博客。。。）

>写在最后：即使按照步骤走，每个人都会遇到各式各样的问题，大家可以多搜索，主动去寻找问题的答案。
==有问题可以联系我：yanwd628@163.com==
