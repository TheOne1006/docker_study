## 安装

### Linux

1. ubuntu 维护的安装
2. docker 提供的安装脚本

添加 docker 用户组:  
```bash
sudo groupadd docker
sudo gpasswd -a ${user} docker
sudo service docker restart
```


### OS X

需要 `boot2docker`
<http://dashboard.daocloud.io/> 下载安装 Docker Toolbox. 更快
