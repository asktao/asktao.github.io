---
title: "Laravel 使用联合主键"
date: 2021-10-09T10:19:02+08:00
draft: false
tags: [programming]
---

在 Model 中表示方式

```php
protected $primaryKey = ['key_one', 'key_two'];
public $incrementing = false;
```

