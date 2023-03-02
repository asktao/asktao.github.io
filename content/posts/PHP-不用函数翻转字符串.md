---
title: "PHP 不用函数翻转字符串"
date: 2021-10-09T10:17:27+08:00
draft: false
tags: [programming,PHP]
---
```php
$str = 'hello';

$newstr = '';

$i = 0;

while (!empty($str[$i])) {
	$newstr = $str[$i].$newstr;

	$i++;
}

echo $newstr;
```

