---
title: ubuntu 下安装 eclipse
date: 2012-07-22 21:34:56
tags:
---

当然先要下载 [eclipse](http://eclipse.org) 解压到一个目录

然后在 ` ~/.local/share/applications/` 目录下创建个 eclipse.desktop 文件来启动 eclipse

<!-- more -->

```
[Desktop Entry]
Type=Application
Icon= ** eclipse 目录/icon.xpm **
Name=Eclipse
Categories=Development;
Exec= ** eclipse 目录/eclipse **
```
