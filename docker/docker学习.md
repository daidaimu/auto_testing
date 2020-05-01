

###dockehub账号密码

```
wenjiantan
twj000898?!
```



### docker与传统虚拟机的区别

```

```



### docker操作

```
1. docker pull lmage  拉取镜像
2. docker image ls    列出镜像
3. docker system df   查看镜像，容器， 数据卷占用空间
4. docker image ls --format "table {{.ID}}\t{{.Repository}}\t{{.Tag}}" 自定义展示
5. docker image rm imageid     删除镜像
6. docker image rm $(docker image ls -q)  删除所有镜像
7. docker container rm containerID
8. docker image rm imageID
9. docker container prune 清理掉所有处于终止状态的容器
```



### docker 定制镜像

```dockerfile
Dockefile: 是一个文本，其内容包含了一条条的指令(Instruction), 每一条指令构建一层，因此，没一条指令的内容，就是描述改成应当如何创建

指令创建：
mkdir Nginx && cd Nginx 
touch Dockerfile

FROM nginx   // FROM：指定基础镜像， 这里以nginx为基础镜像，在nginx基础镜像上进行构建

RUN echo '<h1> Hello World!</h1> //   run用来执行命令行的  注：一个命令行构建一层

COPY 原路径  目标路径   //复制
ADD  原路径  目标路径   // 高级复制，可以自动解压原路径文件到目标路径下

CMD 容器启动命令
ENTRYPOINT 

ARG 参数名 值

ENV   //设置环境变量
	1. ENV <key> <value>      // ENV NODE_VERSION 7.2.0
	2. <key1>=<value1> <key2>=<value2>...  //  ENV=NODE_VERSION 7.2.0

EXPOSE 声明端口  //EXPOSE 指令是声明运行时容器提供服务端口, 只是声明，并不会开启端口
EXPOSE 端口1 端口2

构建镜像：在Dockerfile的路径下执行
docker build -t nginx:v4 .           nginx:v4 镜像名:tag



```



### docker导出容器

```
1. docker export   容器导出命令
	 docker export containerID > /Desktop/
	 
2. 导入容器快照
	 docker export - test/image:tag
```







### docker-compose up

