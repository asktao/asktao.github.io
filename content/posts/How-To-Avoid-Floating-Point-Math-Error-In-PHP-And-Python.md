---
title: "How to Avoid Floating Point Math Error in PHP and Python"
date: "2021-10-07T15:28:09+08:00"
tags: [programming,PHP,Python]
---
```bash
php -r "var_dump(intval(0.58 * 100));”

int(57)
```


```bash
python3

>>>print(0.58*100)57.99999999999999
```


other languages [http://0.30000000000000004.com](http://0.30000000000000004.com/)

how did this happen  [http://www.laruence.com/2013/03/26/2884.html](http://www.laruence.com/2013/03/26/2884.html)

Mathematical extensions in php and decimal module in python to avoid this

```bash
php -r "var_dump(intval(bcmul('0.58', '100')));"

int(58)
```


```bash
>>> from decimal import Decimal

>>> from decimal import getcontext

>>> print(Decimal('0.58') * Decimal('100'))

58.00
```
