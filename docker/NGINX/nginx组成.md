### Nginx组成部分

```
1. Nignx二进制可执行文件  由各个模块源码编译出的一个文件
2. Nignx.conf配置文件    控制nginx的行为
3. access.log 访问日志   记录每一条http请求信息
4. error.log 错误日志    定位问题
```



```nginx
正向代理：
反向代理：

```

```
/etc/logrotate.d   日志切割
/etc/nginx     目录，配置文件    Nginx主要配置文件
/etc/nginx/nginx.conf
/etc/nginx/conf.d
/etc/nginx/conf.d/default.conf
/etc/nginx/mime.types
```



### Nginx配置

```nginx
Nginx连接配置限制
Syntax: limit_conn_zone key(如限制ip, 域名) zone=name:size   name(限制的名字) size(开辟空间)
Content: http

Syntax: limit_conn name number; 调用上一个name
Content: http server location
number

Nginx请求配置限制
Syntax: limit_req_zone key zone=name:size rate=rate; rate number/s
Content:http

Syntax: limit_req zone=name [brust=number][nodylay]
Content: http, server, location


apt-get install apache2-utils 安装ab  并发：ab -c 20 -n 20 http://www.baidu.com

```

