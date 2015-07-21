---
layout: post
title: "与ucenter同步用户登录，注册"
date: 2011-10-13 11:35
comments: true
categories: PHP
---

1. 首先先在<http://www.discuz.net/thread-879237-1-1.html> 下载 UCenter开发手册，是developguide文件夹，里面有三个文件夹![](http://ww3.sinaimg.cn/large/4cc5f9b3gw1er6j7e5pp7j20hm01rq2u.jpg)
2. document：是官方为我们提供的ucenter开发接口手册。examples：是官方提供我们的例子。可以参照  [UCenter接口官方手册](http://www.ucapi.com/api/example.htm)
3. 首先将examples中的config.inc.php文件，api文件夹，include文件拷贝到您网站的根目录下边，同时将uc_client也拷贝到您网站的根目录下。ucexample_1.php，ucexample_2.php作为实验用的文件也拷贝进去。
4. 接下来登录到ucenter的后台在【应用管理->添加新应用】选择自定义安装应用名称：填写自己网站名应用的URL：填自己网站的域名通信密钥：随便填 但是自己要记住啊应用类型：不是下拉表中的就选其它是否开启同步登录：是 是否接受通知：是 点击提交 将会生成一段 应用的UCenter 配置信息，将此信息复制到config.inc.php中，将

```php
define('UC_CONNECT', 'mysql');    // 连接 UCenter 的方式: mysql/NULL, 默认为空时为 fscoketopen()
// mysql 是直接连接的数据库, 为了效率, 建议采用 mysql

//数据库相关 (mysql 连接时, 并且没有设置 UC_DBLINK 时, 需要配置以下变量)
define('UC_DBHOST', 'localhost');   // UCenter 数据库主机
define('UC_DBUSER', 'root');    // UCenter 数据库用户名
define('UC_DBPW', '');     // UCenter 数据库密码
define('UC_DBNAME', 'ucenter');    // UCenter 数据库名称
define('UC_DBCHARSET', 'gbk');    // UCenter 数据库字符集
define('UC_DBTABLEPRE', 'ucenter.uc_');   // UCenter 数据库表前缀

//通信相关
define('UC_KEY', '');    // 与 UCenter 的通信密钥, 要与 UCenter 保持一致
define('UC_API', 'http://yourwebsite/uc_server'); // UCenter 的 URL 地址, 在调用头像时依赖此常量
define('UC_CHARSET', 'gbk');    // UCenter 的字符集
define('UC_IP', '');     // UCenter 的 IP, 当 UC_CONNECT 为非 mysql 方式时, 并且当前应用服务器解析域名有问题时, 请设置此值
define('UC_APPID', 1);     // 当前应用的 ID
```

此段代码覆盖 接下来打来ucexample_1.php,进行测试，**注意里面include 文件的路径是否和你的匹配正确**。 然后就可以在你需要写代码的页面加上

```php
include_once 'config.inc.php';

include_once 'include/db_mysql.class.php';
$db = new dbstuff;
$db->connect($dbhost,$dbuser,$dbpw,$dbname,$pconnect);
unset($dbhost,$dbuser,$dbpw,$dbname,$pconnect);

include_once 'uc_client/client.php';
```

就可以随心所欲的用uc官方提供给我的接口了。

## Comments

**[Air Mattress](#9 "2011-11-08 12:57:58"):** 博主太有才了

