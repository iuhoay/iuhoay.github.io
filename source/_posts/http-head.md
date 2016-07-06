---
title: Http 之 HEAD
date: 2013-09-28
---

Http 中 HEAD 方法同 GET 相同，但是 HEAD 只返回 Http header 信息。通常用于测试链接的有效性，可达性，和最新的修改信息。

<!-- more -->

``` bash
$ curl --head iuhoay.me 
HTTP/1.1 200 OK
Server: GitHub.com
Date: Sat, 28 Sep 2013 12:54:08 GMT
Content-Type: text/html
Content-Length: 1363
Last-Modified: Sat, 28 Sep 2013 12:35:39 GMT
Connection: keep-alive
Expires: Sat, 28 Sep 2013 13:04:08 GMT
Cache-Control: max-age=600
Vary: Accept-Encoding
Accept-Ranges: bytes
```

参考链接  
[http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.4](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.4)


