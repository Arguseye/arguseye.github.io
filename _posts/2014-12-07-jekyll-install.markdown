---
layout: default
title:  "jekyll's install"
date:   2014-12-07 20:51:22
categories: jekyll 
---

# Windows环境下，jekyllrb的搭建：

jekyll是一个简单的、以博客内容为中心的静态网站生成工具。它能够将markdown格式文件转换成静态网页，让我们专注于博客的编写。与此同时，jekyll又是github的文本解析引擎，我们通过建立jekyll工程就能完成一个Github Pages了，是不是很酷呢？让我们先建立一个jekyll吧！

[jekyllrb](http://jekyllrb.com/)需要利用gem install jekyll命令搭建环境，我们首先在windows下安装ruby：

## 1.1 ruby环境搭建

[Get Ruby for Windows](http://rubyinstaller.org/downloads/)。在windows下建议使用Ruby 2.0.0版本等老版本，因为新版本在windows可能存在不兼容问题

## 1.2 the Ruby Devkit

[the Ruby DevKit](http://rubyinstaller.org/downloads/)的安装。将压缩内容解压到C:\RubyDevKit\路径下，利用RubyDevKit为了更好的使用jekyllrb。

1.2和1.1的路径相同，但是1.2是在页面的左侧！！！

利用**cd C:\RubyDevKit\**进入路径，使用**ruby dk.rb init**和**ruby dk.rb install**进行安装。

目前为止，ruby的环境和工具都已安装完毕。

## 2.1 jekyll的安装

**gem install jekyll**  命令安装jekyll。刚开始可能会出现卡死，请不要使用中断命令；如果提示安装错误，请重新再安装一次（我就是第二次安装成功的）

## 2.2 wdm 兼容工具的安装

大家可能安装完jekyll后，都迫不及待地利用 **jekyll new my-awesome-site** && **cd my-awesome-site**，**jekyll serve**来起一个jekyll服务器，但是在起服务器的时候，会提示错误：

```sh
require 'rbconfig'
gem 'wdm', '~> 0.1.0' if RbConfig::CONFIG['target_os'] =~ /mswin|m     ingw/i
```
根据错误提示看到，如果系统是mswin需要安装wdm工具，利用**gem install wdm**，实现windows平台的兼容。

**请注意，需要在_config.yml配置highlighter: true参数才能够开启服务（原因不详，欢迎补充）**

## 3.1 code代码高亮显示

code代码高亮有很多方法，以Pygments的方法来实现，这种方法网上的教程很多，但请仔细尝试。
+ Pygments是基于Python的，所以机器上需要安装[Python](https://www.python.org/download/)，我用的版本是2.7.8
+ 安装Pygments，通过**easy_install Pygments**，但需要安装[easy_install](https://pypi.python.org/pypi/setuptools)
+ 在解压后的Pygments目录中，运行命令：sudo python setup.py install

Pygments提供了多种样式，比如’native’, ‘emacs’, ‘vs’等, pygmentize -S native -f html > pygments.css, “native”是样式名，“html”是formatter，在layout中引用刚刚加的pygments.css

并在_config.yml配置参数：

```js
markdown: redcarpet
    extensions: ["no_intra_emphasis", "fenced_code_blocks", "autolink", "tables", "with_toc_data"]
pygments: true
pygments_options: ['lineanchors', 'linenos=table']
highlighter: true
```

{% gist 01d30d114ae00ec03449 %}


## 3.2 公式的支持

blog如果出现数学公式可以考虑使用[Mathjax](<script src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>)，或者使用LaTeX来实现.我使用的是Mathjax。

PS:通过jekyll serve --watch起服务器后，通过localhost:4000访问，不要使用0.0.0.0:400访问，因为0.0.0.0在windows平台下属于非法地址。

## 参考：

 1. [jekyll中文](http://jekyllcn.com/docs/home/)、[jekyll英文](http://jekyllrb.com/docs/home/)
 2. [Jekyll on Windows](http://jekyllrb.com/docs/windows/)
 3. [ZhenYu's Blog](http://zyzhang.github.io/blog/2012/08/31/highlight-with-Jekyll-and-Pygments/)
 4. [Github Pages](http://yanping.me/cn/blog/2012/03/18/github-pages-step-by-step/)