## Images
1. 查看镜像
2. 删除镜像
3. 搜索镜像
4. 获取与推送镜像

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
