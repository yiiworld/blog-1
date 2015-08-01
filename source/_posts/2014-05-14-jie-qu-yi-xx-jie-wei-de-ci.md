---
layout: post
title: "截取以xx结尾的词"
date: 2014-05-14 11:06
comments: true
categories: php
---

```php
function endsWith($haystack, $needle)
{
   $length = strlen($needle);
   if ($length == 0) {
       return true;
   }

   return (substr($haystack, -$length) === $needle);
}
```