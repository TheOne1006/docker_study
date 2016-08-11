# dockerfile

- 包含注释,指令
- 指令 大写

```bash
# Comment
INSTRUCTION avg
```

## 指令类型

1. `FROM <IMAGE>[:<TAG>]`
  - 已经曾在的镜像
  - 后续的指令也基于此镜像,也成为基础镜像
  - 必须是 __第一条__ 非注释指令
2. `MAINTAINER <name>`
  - 指定镜像的作者信息,包含作者的联系方式.
3. RUN
  - 指定镜像中运行命令
  - 每一个 `run` 指令都会在当前镜像的上层创 __建新的镜像__
  - SHELL 模式: `RUN <COMMAND>`
    - `/bin/sh -c COMMAND` ?
  - EXEC 模式: `RUN ["exectable", "param1", "param2"]`
4. `EXPOSE <port> [<port>]`
  - 指定运行该镜像的容器和使用端口
  - 但是在 容器启动时,依然需要 `-p port` 指定端口号(出于安全考虑)
5. CMD
  - 容器运行的默认命令
  - SHELL 模式: `CMD <COMMAND>`
  - EXEC 模式: `CMD ["exectable","param1", "param2"]`
  - ENTRYPOINT 指令默认参数
  - 跟 RUN 指令的差异
    1. RUN 在镜像构建时运行
    2. CMD 在容器运行运行
    3. `docker run ` 如果指定运行命令, cmd 会被覆盖
6. ENTRYPOINT (入口)
  - 与 CMD 命令类似, 容器运行时的指令
  - 区别 不会被` docker run` 的指令覆盖
  - SHELL 模式: `ENTRYPOINT <COMMAND>`
  - EXEC 模式: `ENTRYPOINT ["exectable","param1", "param2"]`
7. ADD
8. `COPY <SRC> <DEST>`
  - src 构建目录中的相对地址
  - dest 指定镜像中的绝对路径
  - ADD 提供 tar 等功能
  - 单纯复制文件建议copy
9. `VOLUME ["/data"]`
  - 添加数据卷
10. `WORKDIR`
  - 指定命令的目路径,绝对路径
11. `ENV`
  - `ENV <key> <val>`
  - `ENV <key>=<val> ...`
  - 指定环境变量
12. `USER daemon`
  - 指定命令以什么用户身份运行
  - 默认为 root
13. `ONBUILD [INSTRUCTION]`
  - 当镜像作为其他镜像的基础镜像时会被执行




## 创建
```bash
# 在当前目录通过 docker 创建 imageName 的镜像
docker build -t <imageName>:<tag> .
```




- - - -
