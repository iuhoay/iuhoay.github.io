---
title: JDK 安装
date: 2013-09-27 22:27:04
tags:
---

下载
`http://www.oracle.com/technetwork/java/javase/downloads/index.html`

解压到指定目录

``` bash
sudo tar zxvf ./jdk-x-linux-xxx.tar.gz -C /usr/lib/jvm
cd /usr/lib/jvm
sudo mv jdk1.x.x java-7-oracle
```

修改环境变量

``` bash
export JAVA_HOME=/usr/lib/jvm/java-7-oracle
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH
```

<!-- more -->
