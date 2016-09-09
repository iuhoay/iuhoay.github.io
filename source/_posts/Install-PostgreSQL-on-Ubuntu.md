---
title: Install PostgreSQL on Ubuntu
date: 2016-08-26 14:32:48
tags:
---

安装 PostgreSQL 9.5

```bash
$ sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
$ sudo apt-get install wget ca-certificates
$ wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install postgresql-9.5
```

<!-- more -->

安装完成，使用 `postgres` 用户登录控制台

```bash
$ sudo su - postgres
postgres@:~$ psql
psql (9.5.4)
Type "help" for help.

postgres=#
```

使用 `\password` 命令设置密码

```
postgres=# \password postgres
```

使用 `\q` 命令退出控制台

```
postgres=# \q
```

使用 shell 创建数据库用户

```bash
$ sudo -u postgres createuser --superuser dbuser
$ sudo -u postgres psql
postgres=# \password dbuser
postgres=# \q
```

为 `dbuser` 创建数据库

```shell
$ sudo -u postgres createdb -O dbuser exampledb
```

使用 `dbuser` 登录数据库并打开 `exampledb`

```shell
$ psql -U dbuser -d exampledb -h 127.0.0.1 -p 5432
```

`-U` 指定用户 `-d` 指定表 `-h` 指定服务器 `-p` 指定端口

打开远程访问

打开 `/etc/postgresql/9.5/main/postgresql.conf`，找到 `listen_addresses` 替换为

```
listen_addresses = '*'
```

修改 `/etc/postgresql/9.5/main/pg_hba.conf`，找到 `host   all   all   127.0.0.1/32    md5` 替换为

```
# TYPE  DATABASE  USER    ADDRESS     METHOD
host    all       all     0.0.0.0/0   md5
```

执行 `sudo service postgresql restart` 重启服务

最后使用外部 ip 访问

```
$ psql -U dbuser -d exampledb -h 192.168.1.233
```
