---
layout: post
title: "Yii 的代码规范问题"
date: 2014-03-30 11:04
comments: true
categories: 
---

Yii 遵循约定大于配置原理。遵循约定的好处是你不需要编写和管理复杂的配置，就可以创建复杂的 Yii 应用。 **网址** URL 默认地,Yii 识别以下格式 URL: `http: //hostname/index.php?r=ControllerID/ActionID` **代码 ** Yii 建议变量，函数和类类型使用骆驼方式命名，就是大写名字中的每个单词并不用空格连接起来。变量和函数名首字母小写，为了区分于类名称(如：$basePath ，runController()，LinkPager)。对于私有的类成员变量，建议将他们的名字前缀加下划线字符(例如：$ _actionList) 。 **配置** 配置是 键-值 对组成的数组。每个键代表要被配置的对象的一个属性,每个值是相应属性的初始值。例如, array('name'=>'My application', 'basePath'=>'./protected')初始 name 和 basePath 属性为其相应 的数组值。 **文件** 文件命名和使用的约定取决于其类型。 类文件应命名应使用包含的公共类名字。例如,CController 类是在 CController.php 文件中。公共类是一个可用于 任何其他类的类。每个类文件应包含最多一个公共类。私有类(只被单独一个公共类使用)可以和该公共类存放在同一 个文件里。 视图文件应使用视图名称命名。例如,index 视图在 index.php 文件里。视图文件是一个 PHP 脚本文件包含 HTML 和 PHP 代码,主要用来显示的。 配置文件可任意命名。配置文件是一个 PHP 脚本,其唯一目的就是要返回一个代表配置的关联数组。 **目录** Yii 默认设定了被用于各种目的的一个目录集合.需要时,它们每个均可被自定义。 

  * WebRoot/protected: 这是 application base directory 包括所有安全敏感的 PHP 脚本和数据文件。Yii 有一个 默认的别名为 application 代表此路径。这个目录和下面的一切文件目录,将得到保护不被网络用户访问。它 可通过 CWebApplication::basePath 自定义。
  *  WebRoot/protected/runtime: 此目录拥有应用程序在运行时生成的私有临时文件。这个目录必须可被 Web 服务器进程写。它可通过 CApplication::runtimePath 定制。
  *  WebRoot/protected/extensions: 此目录拥有所有第三方扩展。它可通过 CApplication::extensionPath 定 制。
  * WebRoot/protected/modules: 此目录拥有所有应用 模块,每个表示为一个子目录。
  *  WebRoot/protected/controllers: 此目录拥有所有控制器类文件。它可通过CWebApplication::controllerPath 定制。
  * WebRoot/protected/views:此目录包括所有的视图文件,包括控制视图,布局视图和系统视图。可通过CWebApplication::viewPath 定制。
  * WebRoot/protected/views/ControllerID: 此目录包括某个控制类的视图文件。这里 ControllerID 代表控制类的 ID。可通过 CController::viewPath 定制。
  * WebRoot/protected/views/layouts: 此目录包括所有的布局视图文件。可通过CWebApplication::layoutPath 来定制。
  *  WebRoot/protected/views/system: 此目录包括所有的系统视图文件。系统视图文件是显示错误和异常的模板。可通过 CWebApplication::systemViewPath 定制。
  * WebRoot/assets: 此目录包括发布的 asset 文件。一个 asset 文件是一个私有文件,可被发布来被 Web 用户访问。此目录必须 Web 服务进程可写。可通过 CAssetManager::basePath 定制。
  * WebRoot/themes: 此目录包括各种适用于应用程序的各种主题。每个子目录代表一个主题,名字为子目录名字。可通过 CThemeManager::basePath 定制。
**数据库** 大多数 Web 应用由数据库支撑的. 最佳实践是,我们建议数据库的表和列遵循如下命名约定. 注意它们不是 Yii 必需 的. 

  *  数据库的表和列均以小写格式命名.
  * 名字中的单词应以下划线分隔(例如 product_order)。
  * 对于表的名字, 可以使用 singular（单数）或 plural（复数）名字, 但不要两者均采用. 简化起见, 我们推荐使用 singular（单数） 名字.
  * 表名字可以使用前缀,如 tbl_。 当一个应用的表和其他应用的表共存在同一个数据库时非常有用. 使用不同的表前缀可以容易地将它们分开.
**开发流程**

  1. 已经描述了 Yii 的基本概念,现在我们看看用 Yii 开发一个 web 程序的基本流程。前提是我这个程序我们已经做了需求分 析和必要的设计分析。
  2. 创建目录结构。在前面的章节 Creating First Yii Application 写的 yiic 工具可以帮助我们快速完成这步。
  3. 配置 application。就是修改 application 配置文件。这步有可能会写一些 application 组件(例如:用户组件)
  4. 每种类型的数据都创建一个 model 类来管理。同样,yiic 可以为我们需要的数据库表自动生成 active record 类。
  5. 每种类型的用户请求都创建一个 controller 类。依据实际的需求对用户请求进行分类。一般来说,如果一个 model类需要用户访问,就应该对应一个 controller 类。yiic 工具也能自动完成这步。
  6. 实现 actions 和相应的 views。这是真正需要我们编写的工作。
  7. 在 controller 类里配置需要的 action filters 。
  8. 如果需要主题功能,编写 themes。
  9. 如果需要 internationalization 国际化功能,编写翻译语句。
  10. 使用 caching 技术缓存数据和页面。
  11. 最后 tune up 调整程序和发布。
以上每个步骤,有可能需要编写测试案例来测试。