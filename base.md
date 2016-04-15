
## 基础简介

docker 的容器技术,是虚拟化方案的一种.  
与`虚拟器`的差异 ...  

#### Linux 容器技术 与 虚拟机
容器技术:
1. 直接运行在操作系统内核之上的用户控件
2. 所以只能运行相同或形似的内核操作系统
3. 依赖于Linux内核特性:Namespace和Cgroups(Control Group)
4. 优点: 磁盘操作空间更少

虚拟机技术:  
1. 通过中间层将一台或多台独立的机器虚拟运行与硬件之上
2. 虚拟机不仅需要应用,还需要包含操作系统
3. 虚拟机需要模拟硬件的行为,对内存和cpu 的损耗非常大

#### docker 目标
轻量化的建模方式
职责的逻辑分离
快速高效的开发声明周期
鼓励面向服务的架构

#### 场景
1. 使用docker开发,测试,部署服务
2. 创建隔离的运行环境
3. 搭建测试环境
4. 构建多用户的平台服务(PaaS)基础设施
5. 提供软件即服务(SaaS) 应用程序
6. 高性能,超大规模的宿主机部署


## 基本组成
1. Client 客户端
2. Daemon 守护进程
3. Image 镜像
4. Container 容器
5. Registry 仓库

### 客户端和守护进程
C/S架构, 守护进程即服务端  
对服务端可以在本地也可以在远程  





- - -