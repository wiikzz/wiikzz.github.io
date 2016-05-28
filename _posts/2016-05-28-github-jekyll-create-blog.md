---
layout: post_layout
title: Github+jekylly创建自己的Blog
time: 2016年05月28日 星期六
location: 上海
pulished: true
excerpt_separator: "```"
---

#### **环境配置**
工欲善其事，必先利其器。

1. 我们得将最基本的git版本控制环境给配置好，这个同学们自己去谷歌云云。偷懒的同学请看[这里][2]^_^。
2. 我们需要一个[github][3]帐号，这个不多说。并创建一个名为`用户名.github.io`仓库。 在仓库的设置界面可以通过Launch automatic page generator来创建一个pages页面；通过`用户名.github.io`就可以直接访问些页面啦。当然我们的目不仅于此，我们需要更多的自定义；所以我们采用[Jekyll][4]来创建静态博客页面。创建成功后，当你上传你的文章时，github会自动帮你生成网页，我们只负责上传我们的文章就行。
3. 本地配置Jekyll环境（我们写文章需要实时预览其在网站上的表现效果）。

**MAC：** 

 - Ruby是自带的，如果没有请[自行安装][5]。
 
```bash
#更新gem
gem update --system
```

 - 这一步估计需要翻墙，请移步[查看办法][6]。
 
```bash
$ gem sources --add https://ruby.taobao.org/ --remove https://rubygems.org/
$ gem sources -l
*** CURRENT SOURCES ***

https://ruby.taobao.org
# 请确保只有 ruby.taobao.org
gem update --system
```

 - 安装Jekyll
 
```bash
gem install jekyll
```

[**Windows：**][7]Windwos安装Jekyll主要分为几步：

 - 安装Ruby
 下载Ruby，进入[Rubby下载界面][8]选择对应的版本下载，下载完成后，使用默认路径安装，安装时记得勾上`Add Ruby executables to your PATH`，这样就不用自己去配置环境变量了。完成后，使用命令 `ruby -v` 查看安装情况。
 - 安装DevKit
 下载DevKit，进入[DevKit下载界面][9]（与Ruby下载同一个地方），选择与Ruby对应的版 本下载。安装（就是解压到某一个路径，这里一般选`C:\DevKit`)。
 创建config.xml文件
 
```bash
cd C:\DevKit
ruby dk.rb init
```

 审查并安装
 
```bash
ruby dk.rb review
ruby dk.rb install
```

 - 安装Jekyll
 
```bash
gem install jekyll
```

 - 安装Pyments【[安装Python][10]，[安装Easy Install][11]，安装Pygments】
 Pyments是Jekyll里默认的语法高亮插件。需要安装Phthon支持。Python安装于此不多说，自行Google解决。
 安装Easy Install，下载[ez_setup.py][12]，并保存到C盘，使用命令`python C:\ez_setup.py`运行该脚本。使用命令`easy_install --version`查看是否正确安装。
 使用命令`easy_install Pygments` 安装Pygments。

---

#### **开始博客之旅**

我们需要下载一个[博客模版代码][13]，或者[自己手机配置一个][14]。
基本目录结构如下所示

> |-->\_configy.yml
> |-->\_layouts
> |-->　　default.html
> |-->\_posts
> |-->　　2015-05-28-hello-world.md
> |-->index.html

当然自己创建的还需要知道一些基本的Html知识，以及每个文件代表的含义，这些可以参考下[这里][15]，我就不做过多说明了。

```
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2016-5-28      9:54                assets
d-----        2016-5-28      9:54                _data
d-----        2016-5-28      9:54                _includes
d-----        2016-5-28      9:54                _layouts
d-----        2016-5-28      9:54                _posts
d-----        2016-5-28      9:54                _site
-a----        2016-5-28      9:54            475 .gitignore
-a----        2016-5-28      9:54            147 .travis.yml
-a----        2016-5-28      9:54           7582 about.html
-a----        2016-5-28      9:54             12 CNAME
-a----        2016-5-28      9:54             59 Gemfile
-a----        2016-5-28      9:54            828 Gemfile.lock
-a----        2016-5-28      9:54            628 index.html
-a----        2016-5-28      9:54           1098 LICENSE.md
-a----        2016-5-28      9:54            359 menu.html
-a----        2016-5-28      9:54            100 README.md
-a----        2016-5-28      9:54            590 _config.yml
```

上面是我的一个博客目录结构。
在本地build并运行jekyll serve

```
PS C:\Users\wiikii\Documents\wiikzz.github.io> jekyll build
Configuration file: C:/Users/wiikii/Documents/wiikzz.github.io/_config.yml
            Source: C:/Users/wiikii/Documents/wiikzz.github.io
       Destination: C:/Users/wiikii/Documents/wiikzz.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
                    done in 0.463 seconds.
 Auto-regeneration: disabled. Use --watch to enable.
PS C:\Users\wiikii\Documents\wiikzz.github.io> jekyll serve
Configuration file: C:/Users/wiikii/Documents/wiikzz.github.io/_config.yml
            Source: C:/Users/wiikii/Documents/wiikzz.github.io
       Destination: C:/Users/wiikii/Documents/wiikzz.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
                    done in 0.439 seconds.
  Please add the following to your Gemfile to avoid polling for changes:
    gem 'wdm', '>= 0.1.0' if Gem.win_platform?
 Auto-regeneration: enabled for 'C:/Users/wiikii/Documents/wiikzz.github.io'
Configuration file: C:/Users/wiikii/Documents/wiikzz.github.io/_config.yml
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```

浏览器打开`http://127.0.0.1:4000/`即可看到博客的首页，给你们上张图瞧瞧。

<img src="/assets/img/github_jekyll_create_blog_sample.png" width="500px" />

使用git将其上传到仓库`用户名.github.io`。

```bash
#这里只列出一些关键命令。
git add origin git@github.com:用户名/用户名.github.io.git
git push origin master
```

等待github给你发successfully邮件。使用`用户名.github.io`即可访问到我们的博客啦。


#### **添加自己的域名**

我们希户使用自己的域名访问到我们的博客，如我自己有一个名为'wiikzz.com'的域名，我想让该域名直接解析到我们的博客。怎么办呢？

 -  在博客的source文件中新建一个名为`CNAME`的文件，并写入你的域名，注意不需要添加http://或者www。
 
```
PS C:\Users\wiikii\Documents\wiikzz.github.io> cat CNAME
wiikzz.com
PS C:\Users\wiikii\Documents\wiikzz.github.io>
```

 -  在域名解析提 供商，添加CNAME解析，如下所示，记录值都写`用户名.github.io`。
 -  等待一段时间，基本上就可以使用你的域名访问了。


* * * 

_**[感谢各路大神]**_
 




  [1]: http://www.wiikzz.com
  [2]: http://rogerdudler.github.io/git-guide/index.zh.html
  [3]: http://www.github.com
  [4]: http://jekyll.bootcss.com/
  [5]: http://www.cnblogs.com/daguo/p/4097263.html
  [6]: https://ruby.taobao.org
  [7]: http://yizeng.me/2013/05/10/setup-jekyll-on-windows/
  [8]: http://rubyinstaller.org/downloads/
  [9]: http://rubyinstaller.org/downloads/
  [10]: http://www.python.org/download/
  [11]: https://pypi.python.org/pypi/setuptools#installation-instructions
  [12]: https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py
  [13]: https://github.com/wiikzz/wiikzz.github.io
  [14]: http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html
  [15]: http://blog.csdn.net/on_1y/article/details/19259435