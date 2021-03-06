---
layout: post
title: "解决iPhone/iPad 按钮样式问题"
date: 2014-03-06 10:07
comments: true
categories: css
---

你要的左边的按钮的样式，在Android上面显示是 OK 的，但是不知道为什么，iPad 和 iPhone 上面显示却是右边的按钮样式，很难看。 ![](http://i.stack.imgur.com/PsQOV.jpg) 解决办法就是添加下面的代码：

```css
-webkit-appearance: none;
```

或者是：

```css
input[type="button"], input[type="submit"], input[type="reset"] {
    -webkit-appearance: none;
}
```

参考链接：

[CSS submit button weird rendering on iPad/iPhone](http://stackoverflow.com/questions/5438567/css-submit-button-weird-rendering-on-ipad-iphone)

[CSS input button on iPhone](http://stackoverflow.com/questions/11378380/css-input-button-on-iphone)