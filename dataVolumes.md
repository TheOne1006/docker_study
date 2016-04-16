# 数据卷 Data volume

> 什么是数据卷?
  1. 数据卷是经过特殊设计的目录,它可以联合文件系统(UFS),为一个或多个容器提供访问.
  2. 数据卷的目的: 数据的持久化,它完全独立于容器的生存周期,因此 docker 不会再删除容器时删除数据卷.

## 数据卷的特点

1. 数据卷在容器启动时初始化,如果容器使用的镜像在挂载点包含了数据,这些数据会拷贝到新初始化的数据卷中.
2. 数据卷可以在容器之间共享和重用.
3. 可以对数据卷的内容直接的修改
4. 数据卷的变化不会影响镜像的更新
5. 数据卷会一直存在,即使容器已经被删除


## 为容器添加数据卷

```bash
docker run -v ~/container_data/ :  /本机地址/data -it IMAGE [COMMAND] [AVG]
# 可以通过 inspect 查看挂在数据卷信息
```

为数据卷设置访问权限:  
```bash
修改为
/容器地址/:/本机地址/:权限
```

## 数据卷容器
目的: 通过数据卷容器实现,容器之间的数据共享
使用数据卷容器挂在到别的容器,实际上只是传递了数据卷的配置信息  


```bash
# 第一步 创建一个挂在数据卷的容器
docker run -v /container_data/:/local/data/ -it IMAGE --name dataVolContainer

# 第二部创建 容器
docker run --volumes-form dataVolContainer -it IMAGE


```
