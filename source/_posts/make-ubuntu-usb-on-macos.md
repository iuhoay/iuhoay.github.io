---
title: macos 制作 Ubuntu usb 启动盘
date: 2016-08-25 09:47:13
tags:
---

下载 Ubuntu 镜像，国内可以从 `http://mirrors.aliyun.com/ubuntu-releases/` 阿里云的镜像站下载

这里选择 `16.04.1` 已经有提供 `img` 的镜像文件了
`http://mirrors.aliyun.com/ubuntu-releases/16.04.1/ubuntu-16.04.1-server-i386.img`
下载到本地


<!-- more -->

使用 `diskutil list` 命令显示 U盘挂载在 `/dev/disk2`

```
$ diskutil list

/dev/disk2 (external, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *8.1 GB     disk2
   1:                       0x17                         683.6 MB   disk2s1
```

使用 `diskutil unmountDisk` 卸载 U盘
```
$ diskutil unmountDisk /dev/disk2
```

写入镜像到 U盘

```
$ sudo dd if=ubuntu-16.04.1-server-i386.img of=/dev/rdisk2
```

等待写入完成，最后弹出 U盘

```
$ diskutil eject /dev/disk2
```

enjoy.
