---
layout: post
title: "PHP命名规则"
date: 2012-10-16 14:02
comments: true
categories: 
---

以下文字全部摘自《PHP从入门到精通》这本书，谨以此作为标准。 就一般约定而言，类、函数和变量的名字应该是能够让代码阅读者能够容易地知道这些代码的作用，应该避免使用凌磨两可的命名。 

  1. **类命名**
    * 使用大写字母作为词的分割，其他的字母均使用小写。
    * 名字的首字母使用大写。
    * 不要使用下划线('_')。
    * 如：Name、SuperMan、BigClassObject。
  2. **类属性命名**
    1. 属性命名应该以字符‘m’为前缀。
    2. 前缀‘m’后采用与类命名一致的规则。
    3. ‘m’总是在名字的开头起修饰作用，就像以‘r’开头表示引用一样。
    4. 如：mValue、mLongString等
  3. **方法命名**
    1. 方法的作用都是执行一个动作，达到一个目的。所以名称应该说明方法是做什么的。一般名称的前缀都是有第一规律的，如Is（判断）、Get（得到），Set（设置）。
    2. 方法的命名规范和类命名是一致的。如： 
        
                class    StartStudy{                    //设置类
                $mLessonOne = "";               //设置类属性
                $mLessonTwo = "";               //设置类属性
                fonction GetLessonOne(){        //定义方法，得到属性mLessonOne的值
                    ...
            }
        }

  4. **方法中参数命名**
    1. 第一个字符使用小写字母。
    2. 在首字符后的所有字符都按照类命名规则首字符大写。如 
        
                class EchoAnyWord{
            function EchoWord($firstWord,$secondWord){
                ...
            }
        }

  5. **变量命名**
    1. 所有字母都使用小写。
    2. 使用‘_’作为每个词的分界。
    3. 如：$msg_error、$chk_pwd等。
  6. **引用变量**
    1. 引用变量要带有‘r’前缀。如： 
        
                class Example{
            $mExam = "";
            funciton SetExam(&$rExam){
                ...
            }
            function $rGetExam(){
                ...
            }
        }

  7. **全局变量**
    1. 全局变量应该带有前缀‘g’。如：global = $gTest、global = $g。
  8. **常量、全局常量**
    1. 常量、全局常量，应该全部使用大写字母，单词之间用‘_’来分割。如 
        
                define('DEFAULT_NUM_AVE',90);
        define('DEFAULT_NUM_SUM',500);

  9. **静态变量**
    1. 静态变量应该带有前缀‘s’。如： 
        
                station $sStatus = 1;

  10. **函数命名**
    1. 所有的名称都使用小写字母，多个单词使用‘_’来分割。如： 
        
                function this_good_idear(){
            ...
        }

  以上的各种命名规则，可以组合一起来使用，如： 
    
    
    class OtherExample{
        $msValue = "";        //该参数既是类属性，又是静态变量
    }