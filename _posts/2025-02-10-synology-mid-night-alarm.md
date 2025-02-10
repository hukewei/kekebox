---
layout:       post
title:        "群晖半夜报警风波"
author:       "Kawai"
header-img:   img/synology-nas.png
catalog:      true
tags:
    - Synology
    - Personal
    - NAS
---

> 半夜三点被哔哔声吵醒，结果发现是群晖在报警

### 半夜三更
这天睡眠本来质量就一般，前一晚吃了辣螃蟹，几次被热醒，好不容易入睡，结果半夜被哔哔声吵醒，仔细一听，原来是群晖在报警。马上摸出手机打开控制台。

结果发现系统显示不支持的磁盘，存储空间无法重组。

### 解除警报
无法重组的是两块ssd组成的raid 0阵列，里面没有重要数据，现在又是大半夜的，马上消除警报，继续睡觉。

### 查找问题
第二天下班回来，重新尝试重组磁盘，依旧失败。
群晖给的错误代码是：
One or more drives (Cache device 1) are incompatible with the current device. Please insert them in the original device to continue using the drives.
重新插拔ssd之后，问题依旧。谷狗搜出来没有发现最近相同的案例，但是在群晖的官方支持论坛上发现去年11月的一个[帖子](https://community.synology.com/enu/forum/1/post/190402)，上面虽然没有说警报声的事情，但是也提示了自己的安装的第三方ssd在升级系统之后被NAS提示不支持。

其实NAS显示不支持该SSD的警告我几个月前升级到DSM 7.2的时候已经遇到过， 当时并没有任何警报。所以也就没太在意。

### 解决问题
在那个帖子最后帖主更新了他采取的办法，放了一个github的[项目链接](https://github.com/007revad/Synology_HDD_db)。
抱着死马当活马医的态度，直接跟随github上的procedure把上面的script 运行了一遍，按提示重启NAS，没想到重启之后报警声不再响起，打开控制台发现之前丢失的存储空间已经正常，ssd也不再提示不支持。问题就这么解决了。

这时候才真正联想到是不是昨晚的问题和系统更新有关，查找log之后果然发现系统在3点左右自动更新并重启了。

### 事件复盘
- 3：00 AM 群晖自动查找更新 （设定是每周一3am）
- 3：12 AM 自动更新开始 （升级了7.2之后，默认是自动安装更新，以前都是手动安装）
- 3：20 AM 更新结束，系统重启
- 3：22 AM 新系统“不支持”我的WD的SSD，并且报警，同时我被吵醒
- 3：24 AM 警报被我关闭

### 应对措施
1. 关闭自动安装更新
2. 修改搜索更新的时间，从周一3am改到了周六11am
3. 每次开机时自动运行hdd check脚本   

### 结语
群晖这次更新直接发送警报真是让人措手不及，被吵醒的应该不少人。希望下次不要在被吵醒了，也希望群晖能够对第三方ssd更加的宽容。



