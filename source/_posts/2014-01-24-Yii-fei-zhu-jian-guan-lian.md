---
layout: post
title: "Yii 非主键关联"
date: 2014-01-24 13:53
comments: true
categories: yii
---

```php
function relations()
    {
        return array(
            'last_experience' => array(
                self::HAS_ONE,
                'Experience',
                '',
                'on' => 'user_id=last_experience.user_id'
            ),
        );
    }
```