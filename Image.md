## Images
1. 查看镜像
2. 删除镜像
3. 搜索镜像
4. 获取与推送镜像
5. 构建镜像

镜像存储位置 : `/var/lib/docker`

### 查看镜像
查看镜像列表
```bash
docker images [OPTIONS] [REPOSITORY]
-a, --all=false  // 所有镜像 , 默认不显示中间层的镜像
-f, --filter=[]  // 过滤条件
--no-trunc=false // 不使用截断的形式(id)
-q, --quiet=false // 只显示镜像的唯一 id
```
结果
```bash
REPOSITORY        TAG           IMAGE ID            CREATED             SIZE  
镜像所属的仓库名     不同镜像的标签  镜像的唯一id         镜像建立时间          大小 MB  
```

查看 镜像/容器 详细信息
```bash
docker inspect [OPTIONS] CONTAINER|IMAGE [CONTAINER|IMAGE]
-f ,--format
例如: docker inspect ubuntu:14:04 / docker inspect imageId
```

### 删除镜像
```bash
docker rmi [OPTIONS] IMAGE [IMAGES]
-f, --force=false 强制删除
--no-prune=false 保留被打标签的父镜像
```


### 搜索镜像
1. Docker Hub
  - <https://registry.hub.docker.com>
2. commond `docker search [OPTIONS] TERM`
  - --automated=false 自动化选项
  - --no-trunc
  - -s, --start=0 限定最低星级

### 获取与推送镜像

##### 拉取镜像
```bash
docker pull [OPTIONS] NAME[:TAG]
-a, --all-tags=false 下载所有
-no-trunc
-s, --starts=0
命令最多显示25条命令
```

##### 推送镜像
```bash
docker push NAME[:tag]
```

### 构建镜像
1. 保存对容器的修改,并再次使用
2. 自定义镜像的能力
3. 以软件的形式打包并分发服务以及其环境

__构建方法__:  
1. `docker commit`: 通过容器构建
2. `docker build` : 通过 Dockerfile 文件构建

#### docker commit 通过容器构建镜像

```
docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]  
# -a,--author= // 指定作者
# -m,--message= // Commit message
# -p,--pause=true // 是否暂容器
```

#### Dockerfile
 



- - -
