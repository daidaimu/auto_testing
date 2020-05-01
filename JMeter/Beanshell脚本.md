### 元件分类

- 简单元件： 现成元件（控制器，线程组等）不太支持定制化修改
- 定制化元件：---beanshell元件

### beanshell作用

- 设置全局变量

- 加密/签名

- 处理数据

- 编写/调用java代码

  ```
  1. 定时器
  2. 前置处理器：加密（时间戳+签名）
  3. 采样器：自定义请求
  4. 后置处理器： 解密，全局变量（跨线程组）
  5. 断言：自定义断言
  6. 监听器
  ```



### BeanShell内置变量

```java
log: log.info()   //日志
ctx: 上下文
vars: 引用线程组中的局部变量容器（在线程组内部传递）
  1. vars.get(String key)  :从Jmeter中获得变量值
  2. vars.put(String key, String value): 数据存到jmeter变量中

props: 操作Jmeter属性，该变量引用了Jmeter的配置信息，可以获取Jmeter的属性, 在jmeter.properties中定义
  1. props.get("START.HMS");
  2. props.put("PROPS1", "1234");

prev: 获取前面的sample返回信息
  1. getResponeseDataAsString(); 获取响应信息，后置处理器
  2. getResponseCode(); 获取响应状态码
  
```



### Beanshell设置全局变量

```java
//在BeanShell后置处理器，设置全局变量${__setProperty(全局变量名,值,)} 
1. ${__setProperty(globalname,${result},)} 

//获取全局变量名
2. ${__P(变量名)}

//外部引用java文件
导入java文件

source("java文件路径");

//创建实例 实例化类
class md5 = new class();

//调用加密方法
String res = test.getMD5string();

log.info("+++++"+res)
  

  
导入jar包 路劲(lib->ext->jar包)
import MD5U *;

//创建实例 实例化类
class md5 = new class();

//调用加密方法
String res = test.getMD5string();


导入class文件
addClass("javapath")
//创建实例 实例化类
class md5 = new class();

//调用加密方法
String res = test.getMD5string();

```



```
grafana-server --config=/usr/local/etc/grafana/grafana.ini --homepath /usr/local/share/grafana --packaging=brew cfg:default.paths.logs=/usr/local/var/log/grafana cfg:default.paths.data=/usr/local/var/lib/grafana cfg:default.paths.plugins=/usr/local/var/lib/grafana/plugins

brew services start grafana
brew services stop  grafana
```



```
To have launchd start influxdb now and restart at login:
  brew services start influxdb
Or, if you don't want/need a background service you can just run:
  influxd -config /usr/local/etc/influxdb.conf
==> Summary
/usr/local/Cellar/influxdb/1.7.9: 9 files, 149.9MB

开启服务
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.influxdb.plist

停止服务
launchctl unload ~/Library/LaunchAgents/homebrew.mxcl.influxdb.plist

前台启动
influxd -config /etc/influxdb/influxdb.conf

查看influxdb运行配置
influxd config

启动客户端
influx -precision rfc3339


# The bind address used by the HTTP service.
    bind-address = ":8086"
    
[[graphite]]
  # Determines whether the graphite endpoint is enabled.
    enabled = true
    database = "graphite"
   # retention-policy = ""
    bind-address = ":2003"
    protocol = "tcp"
   consistency-level = "one"

```

