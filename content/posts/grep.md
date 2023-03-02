---
title: "Grep"
date: 2021-10-09T10:21:22+08:00
draft: false
tags: [macOS]
---

grep -v 排除多个 patterns 用 | 分割且需转义

查看 vim 配置

```bash
cat .vimrc | grep -v '"\|^$'
```

