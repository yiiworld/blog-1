---
layout: post
title: "非常方便清除php页面bom头信息工具"
date: 2011-12-19 09:28
comments: true
categories: 
---

大家都知道，使用记事本等部分工具在写php文件，如果文件中使用到session、header等php内置的函数时，要求这些语句之前必须不能有空格、回车、echo输出语句、html标记等，否则页面回给出警告，并且提示 这些语句之前有输出~，错误信息就不贴出来了，总之好多同学遇到这种问题，总是有点不知所措 ，有的同学检查代码后发现这些语句前没有上述我们提及到的一些空格、回车、echo输出语句、html标记等，这是怎么回事呢？这就是文件使用utf-8编码保存的时候，有**bom**标记！ 这里前段时间论坛的朋友（ID:tiansidehao）写了个工具，我这里转发出来供大家学习参考，感谢作者。用法是，将下面的代码保存到一个文件，放到项目目录下，通过浏览器访问一下就可以了: 
    
    
    <!--?php
    //shadowchao.com
    $s=0;//统计成功数
    $f=0;//统计失败数
    //遍历所有文件
    function
    find_allfile(){
    $i="*";
    while($file=glob($i)){
    foreach($file as
    $s){
    if(!is_dir($s))$allfile[]=$s;
    }
    $i.="\*";
    }
    return
    $allfile;
    }
    //清除BOM标记
    function del_bom(){
    global
    $s,$f;
    $file=find_allfile();
    foreach($file as
    $fname){
    $fname=dirname(__FILE__)."\\".$fname;
    $filecont=@file_get_contents($fname);
    $bom=substr($filecont,0,3);
    $bom=bin2hex($bom);
    if($bom=="efbbbf"){
    //判断文件中的前3个字节是否为BOM标记值
    $filecont=substr($filecont,3);
    $result=@file_put_contents($fname,$filecont,LOCK_EX);
    if($result){
    echo
    "[file] $fname --- --- <em style=\"color:green\"-->清除成功<br>";$s++;
    }else{
    echo "[file] $fname --- --- <em style="\"color:red\"">清除失败</em>（文件只读或者被占用）<br>";$f++;
    }
    }
    }
    }
    del_bom();
    if($s==0 &&
    $f==0){
    echo "
    
    所有文件正常，没有发现BOM标记。
    
    ";
    }else{
    echo
    "
    
    统计结果：清除成功($s) | 清除失败($f)
    
    ";
    }
    ?>

原文来自：[http://www.3gput.com/forum.php?mod=viewthread&tid=527&highlight=bom](http://www.3gput.com/forum.php?mod=viewthread&tid=527&highlight=bom)