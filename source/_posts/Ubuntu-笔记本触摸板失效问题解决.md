---
title: Ubuntu 笔记本触摸板失效问题解决
date: 2012-07-23 22:06:25
tags:
---

我的机器 Acer 4741 系统 Ubuntu 12.04

在软件中心安装 `dconf`, 这个相当于 win 的注册表?找到键

` org > gnome > settings-daemon > peripherals > touchpad `

不管怎么按触摸板的开关 `touchpad-enabled` 一直是 false
手动勾上 `touchpad-enabled`, 触摸板正常了, 开关也正常了

过了一天又不行了，google 下，应该是启动时没有加载触摸板模块？
在终端下执行

<!-- more -->

``` bash
sudo modprobe -r psmouse
modprobe psmouse proto=imps
```

再试下，可以开启了
创建文件 `/ec/modprobe.d/touchpad.conf`

``` bash
options psmouse proto=imps
```

一劳永逸，终于搞定
