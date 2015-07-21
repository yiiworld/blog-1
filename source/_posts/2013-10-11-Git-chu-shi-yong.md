---
layout: post
title: "Git初使用"
date: 2013-10-11 22:30
comments: true
categories: 
---

1、Mac 安装Git，软件下载地址：<http://code.google.com/p/git-osx-installer/> 2、第一个要配置的是你个人的用户名称和电子邮件地址。这两条配置很重要，每次 Git 提交时都会引用这两条信息，说明是谁提交了更新，所以会随更新内容一起被永久纳入历史记录： $ git config --global user.name "forecho" $ git config --global user.email caizhenghai@gmail.com 3、建立SSH key 可以让你在你的电脑和 Git @ OSC 之间建立安全的加密连接。 ssh-keygen -t rsa -C "xxxxx@xxxxx.com" 4、查看你的public key，并把他添加到 Git @ OSC http://git.oschina.net/keys cat ~/.ssh/id_rsa.pub 5、Clone 项目 $ git clone <http://git.oschina.net/xxxxxx/xxxxxx.git> 6、复制文件到这个目录下，然后跟踪新的文件： $ git add .    #跟踪所有改动过的文件 $ git add -u    # 只加修改過的檔案, 新增的檔案不加入. $ git add -i     # 進入互動模式 7、提交变更： $ git commit -m "xxxx" $ git commit -a -m 'xxxx' **commit和commit -a的区别:** commit -a相当于： 第一步：自动地add所有改动的代码，使得所有的开发代码都列于index file中 第二步：自动地删除那些在index file中但不在工作树中的文件 第三步：执行commit命令来提交 ​ 8、推送到服务器上： $ git push 9、恢复单个文件 $ git checkout -- hello.rb 远程服务器覆盖当前的改动： $ git checkout -f 10、添加被忽略的文件以及文件夹 $ git add -f 文件路径 11、服务器更新本地 $ git pull 12、git如何查看某一个文件的详细提交记录 $ git log -p filename