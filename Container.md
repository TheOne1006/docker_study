# 容器
1. 基本操作
2. 守护式容器
  - 一次性命令容器
  - 交互式容器
  - 守护式容器的区别
3. 实践:部署静态网站

## 基本操作

### 启动容器

```bash
# 一次执行一个命令
# COMMAND 启动后执行的命令
# arg 启动后执行 命令的参数
docker run IMAGE [COMMAND][ARG...]

# 启动交互式容器
docker run -i -t IMAGE /bin/bash
-i, --interactive=true|false 默认 fasle ,为容器始终打开标准输入
-t, --tty=true|false ,默认 false, 为容器提供个伪终端
-d, 以守护进程方式运行
```

demo
```bash
# 启动一个 ubuntu
# 并执行 echo 'xx' 命令
# 该容器输出 hello world后实际已经停止了, 执行单次命令
$ docker run ubuntu echo 'Hello World'
Hello World

```

##### 启动参数

> `--env` 环境变量  

```bash
docker run --env <key>=<value>
```

> `--rm` 容器完成后自动删除

```bash
docker run --rm
```



### 查看容器

- docker ps
- docker inspect : 查看详情

```bash
docker ps // 正在运行的容器列表
-a, 所有容器
-l, 最新创建的容器

CONTAINER ID    IMAGE        COMMAND     CREATED     STATUS     PORTS   NAMES
容器 id          镜像         命令         创建时间      状态       端口     名字
```

### 自定义容器名字
`docker run ` 使用`--name`

```bash
docker run --name 自定义名字 ....
```

### 重新启动 已经停止的容器

```bash
docker start [-i] 容器名
#-i 以交互的方式重启
```

### 删除容器
- 删除 __已经停止__ 的容器` docker rm 容器名`



## 守护式容器

- 什么是守护式容器
- 如何开启
- 如何进入守护式容器
- 查看容器日志
- 查看容器进程
- 在守护进程中开辟新进程
- 如何停止

交互式容器,在退出之后就停止了,守护式容器的差异:  

1. 长期运行
2. 没有交互式的会话
3. 非常适合运行应用和服务

运行方式:  
```bash
# 第一种
docker run -i -t IMAGE /bin/#!/usr/bin/env bash
Ctrl + Q, Ctrl + P // 退出交互的 bash

# 第二种使用 run 命令
docker run -d IMAGE [COMMAND][AVG]

```

__进入守护式容器__:
```bash
docker attach CONTAINER
```

### 查看容器日志

```bash
docker logs [-f][-t][--tail] 容器名
-f, --follows=true|false ,默认 false ,一直跟踪日志的变化
-t, --timestamps=true|false , 默认 false, 返回结果上加上时间戳
--tail ="all" , 结果条数
```

### 查看容器内进程

```bash
docker top 容器名
```

### 在运行的容器中启动新的进程
虽然 docker 的理念是在一个容器中运行一种服务,单仍旧需要多个进程  

```bash
docker exec [-d][-i][-t] 容器名 [COMMAND][ARG] ...
-d,  
-i,
-t,
```


### 停止守护式容器

1. docker stop 容器, 发送信号给容器等待停止
2. docker kill 容器, 强制


## 实践

容器的端口映射,需要在 run 命令 设置端口映射
```bash
# -P , --publish-all=true|false ,默认 false, 为容器暴露所有端口进行映射
# -p , 指定哪些端口需要映射

```

`-p`四中映射防范

1. containerPort(容器端口) : `docker run -p 80 -i -t ubuntu /bin/bash`
2. hostPort:containerPort(宿主机端口:容器端口)
3. ip:containerPort(主机 ip: 容器 ip)
4. ip:hostPort:containerPort( ip:主机端口:容器端口)

demo nginx
```bash
# 创建80端口映射的交互式容器
docker run --name web -i -t ubuntu /bin/bash
# 安装 nginx vim
apt-get install -y nginx vim
# 创建静态页面
# 修改 nginx 配置

# 运行 nginx
nginx

# 验证

# 宿主机查看 port 映射
docker port [CONTAINER]

# 宿主机查看容器进程  
docker top [CONTAINER]

# 宿主机关闭容器
docker stop [CONTAINER]

# 重启容器
docker start [CONTAINER]

# 新进程执行 ngxin
docker exec [CONTAINER] nginx

```



- - -
