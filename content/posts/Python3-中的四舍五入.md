---
title: "Python3 中的四舍五入"
date: 2021-10-09T10:41:06+08:00
draft: false
tags: [programming,Python]
---

最近在项目中遇到前后端计算数值不一样的情况，发现是由于 Python3 数学运算处理方式和 [PHP BC Math](https://asktao.me/how-to-avoid-floating-point-math-error-in-php-and-python/) 不一样

PHP 的 round 函数

```php
round ( float $val , int $precision = 0 , int $mode = PHP_ROUND_HALF_UP ) : float
```

Constants | Description
----------- | --------
PHP_ROUND_HALF_UP | Rounds `num` away from zero when it is half way there, making 1.5 into 2 and -1.5 into -2.
PHP_ROUND_HALF_DOWN | Rounds `num` towards zero when it is half way there,making 1.5 into 1 and -1.5 into -1.
PHP_ROUND_HALF_EVEN | Rounds `num` towards the nearest even value when it is half way there, making both 1.5 and 2.5 into 2.
PHP_ROUND_HALF_ODD | Rounds `num` towards the nearest odd value when it is half way there, making 1.5 into 1 and 2.5 into 3.

其中 PHP_ROUND_HALF_UP 是默认的  

Python3 的 round 函数没有处理[浮点数运算](https://asktao.me/how-to-avoid-floating-point-math-error-in-php-and-python/)的问题

```python
round(number[, ndigits])
```
The behavior of [`round()`] for floats can be surprising

https://docs.python.org/3/library/functions.html?highlight=round#round

```python
round(2.675, 2) gives 2.67
```

而 decimal 可以四舍五入等运算方式，不过需要指定参数 rounding

可选值为
```python
decimal.ROUND_CEILING
Round towards Infinity.
 
decimal.ROUND_DOWN
Round towards zero.
 
decimal.ROUND_FLOOR
Round towards -Infinity.
 
decimal.ROUND_HALF_DOWN
Round to nearest with ties going towards zero.
 
decimal.ROUND_HALF_EVEN
Round to nearest with ties going to nearest even integer.
 
decimal.ROUND_HALF_UP
Round to nearest with ties going away from zero.
 
decimal.ROUND_UP
Round away from zero.
 
decimal.ROUND_05UP
Round away from zero if last digit after rounding towards zero would have been 0 or 5; otherwise round towards zero.
```
用法如下

```
>>> from decimal import Decimal
>>> Decimal('2.145').quantize(Decimal("0.00"), rounding = "ROUND_HALF_UP")
Decimal('2.15')
```

也可以用 context
```
>>> import decimal
>>> decimal.getcontext().rounding = "ROUND_HALF_UP"
>>> decimal.Decimal('2.145').quantize(decimal.Decimal("0.00"))
Decimal('2.15')
```
即可实现一般财务计算中四舍五入的方式
```
>>> decimal.Decimal('2.675').quantize(decimal.Decimal("0.00"))
Decimal('2.68')
```

