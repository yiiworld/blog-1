---
layout: post
title: "JQuery类似于知乎修改问题的效果"
date: 2011-11-26 14:48
comments: true
categories: 
---

html示例，[猛击这里演示](/demo/edit.html)
    
    
    <input type="text" name="filename" value="示例" /><span id="editfile">修改文件名</span> <span id="cancel">取消</span> <input id="baoc" type="submit" value="保存" />

jquery 代码如下： 
    
    
    <script type="text/javascript">// <![CDATA[
    		$("#filename").css("display","block");
    		$("input[name='filename']").css("display","none");
    		$("#cancel").css("display","none");
    		$("#baoc").css("display","none");
    		$("#editfile").css("cursor","pointer").click(function(){
    			$("#filename").css("display","none");
    			$("input[name='filename']").css("display","block");
    			$("#editfile").css("display","none");
    			$("#cancel").css("display","inline");
    			$("#baoc").css("display","inline");
    			});
    
    		$("#cancel").css("cursor","pointer").click(function(){
    			$("#filename").css("display","block");
    			$("input[name='filename']").css("display","none");
    			$("#editfile").css("display","inline");
    			$("#cancel").css("display","none");
    			$("#baoc").css("display","none");
    			});
    // ]]></script>

先调用一个JQ文件