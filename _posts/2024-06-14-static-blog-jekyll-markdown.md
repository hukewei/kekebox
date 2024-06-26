---
layout:       post
title:        "初尝用静态网页创建博客"
author:       "Kewei"
header-img:   img/bg-cloud-computing.jpeg
catalog:      true
tags:
    - Web
    - Personal
    - Jekyll
---

> 重开kekebox，如何建站又是一个问题，相比于17年前，现在不论是技术架构以及hosting环境都发生了大变化。

### 网站位置
国内建站需要备案。以前备案倒是简单，线上申请一个ICP备案就好了，也不需要自己跑。想当初05年刚推出就做了备案，也算是第一批备案的人了。现在了解一下除了ICP，之后30天内还要有公安备案。流程一套走下来，少则一周，多则一个月。

境外建站就简单了。唯一需要注意的就是国内用户是否可以访问。

### hosting
#### PaaS
云服务兴起之后，国内国外虚拟主机购买的选择都还是很多的，国内阿里云，腾讯云，除了提供国内hosting服务，还有香港，新加坡等位于境外的机房可以选，对于不想在国内备案的人来说还是很方便的。

国外云服务提供商的话，AWS,Azure, GCP这三大家之外，还有oracle，ovh等其他小众一些的选择，对于新用户，个家都提供了一段时间的免费使用优惠，甚至是一些一直免费用的超小型vm。

#### SaaS
PaaS的灵活性高，虚拟机上想干啥干啥，但是如果只是想做博客的话，SaaS也是个好选择，运维完全交给提供商，自己专注写文章就好了。比如[wordpress.com](http://wordpress.com)，除了价格贵，没啥毛病。

### 博客选择
#### Wordpress走到黑
8之前的博客是基于wordpress，依赖环境是php+mysql，这么多年一直都在维护，现在还是有不少的用户群体的。要不是我网站之前的数据都遗失了，应该就无脑继续wordpress了。

#### 新的尝试
无意间看到通过github page的static website hosting的方案来搭建博客。通过使用jeykll加上github action来动态发布内容，使用markdown语言来排版。当时就想原来写博客还可以通过commit以“开源”的方式发布post。瞬间提起了兴趣。而且限制不多，一个小型blog够用：
- 1GB存储
- 每月100GB流量
- 每小时10次build

jekyll框架还是比较轻量的，在github上fork了一位大神的版本，稍作修改push之后直接就可以用了。这里面会用到github action来触发build，这样每次push新的内容，github会重新build静态页面并发布。每小时10次的限制基本上也够了。
1GB的容量少量图片还是够的，如果有视频或者大量的媒体文件就的放床图了。
   

### 结语
就这样，kekebox的博客在几个小时内就以全新的架构重现上线，所有的内容都通过github来存储，无需担心数据丢失的问题。唯一需要考虑的是github page在国内访问的稳定性的问题，目前通过移动宽带和联通手机流量都能访问，国外的访问速度还是要快不少。博客应该还是够了，如果之后要加其他功能就得再做研究了。



