---
layout: post
title: "Discuz X2.0本地调试成功上传服务器"
date: 2011-10-22 10:23
comments: true
categories: php
---

本地测试成功之后，那么接下来就要上传服务器了。

上传服务器之后，因为数据库用户名、密码改了，所以相应的配置文件也要改。

首先要改 config 文件下的config_global.php和config_ucenter.php文件。

![](http://ww1.sinaimg.cn/large/4cc5f9b3gw1er6jnhloptj20aj03k3z2.jpg)

修改相应的地方。

这样论坛就可以链接成功了。但是用户还不能登陆，还需要改uc_server下的data下的config.inc.php文件

也是修改相应的地方。

这时候你发现你的ucenter还不能打开，还需要修改。

进入后台，点击“站长”，修改“ucenter设置”下的“ucenter访问地址”。 （7.2版本的话在“全局”==>“Ucenter设置”下面改）

这时候应该就OK了。