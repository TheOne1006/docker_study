# 容器的连接

## base


## 容器间的连接

1. 允许所有容器的互联
2. 拒绝容器的互联
3. 允许特定容器的互联

### 容器之间的互联

```bash
# docker 以link 方式连接
docker run --link=[CONTAINER]:[ALIAS] [IMAGE] [COMMAND]
# 允许/拒绝容器的互联
--icc=true|false, 默认true , true 允许互联, false 不允许互联
# 允许特定容器访问
需要 `--icc= false --iptables=true --link` 设置这几个选项
```

- 同一宿主机下的容器可以默认可以自由连接的
- 每次重启都可能会改变ip 地址
