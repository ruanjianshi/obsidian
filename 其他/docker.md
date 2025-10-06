# Docker导图

![image-20250109114722377](http://qxmapdepot.xiaoq11.cn/picture/image-20250109114722377.png)

DockerHub:[Docker Home](https://app.docker.com/)

Play with Docker:[Play with Docker](https://labs.play-with-docker.com/#)

Docker安装：[docker - 搜索](https://www.bing.com/search?q=docker&filters=dtbk:"MCFjZ192NV9kb3dubG9hZCFvdmVydmlldyFlMWJmYTQ5ZS1kZDIyLTdiZTUtMWRlYy0wYjhjMzBiZmVhODU%3d"+sid:"e1bfa49e-dd22-7be5-1dec-0b8c30bfea85"+tphint:"f"&FORM=DEPNAV)

DockerDesktop:[Docker: Accelerated Container Application Development](https://www.docker.com/)

# Docker常用指令

![image-20250109114904931](http://qxmapdepot.xiaoq11.cn/picture/image-20250109114904931.png)



# docker基本组成

![img](http://qxmapdepot.xiaoq11.cn/picture/e841778324ac69e7b63543c3c0028959.jpeg)

## 镜像（Image）：

> docker镜像就好比一个模板，我们可以通过这个模板来创建容器服务，tomcat镜像===>run==>tomcat01容器（提供服务器），通过这个镜像可以创建多个容器（最终服务运行或者项目运行就是在容器中的）。
>

## 容器（container）：

> docker利用容器技术，独立运行一个或者一组应用 通过镜像来创建
>

> 启动，停止，删除，基本命令！
> 目前就可以把这个容器理解为就是一个简易的linux系统

## 仓库（repository）：

> 仓库就是存放 镜像（image）的地方！
>
> 仓库又可以分为 公有仓库和私有仓库
>

# 底层原理

## docker是怎么工作的？

> Docker 是一个Client-Server结构的系统，Docker的守护进程运行在主机上。
>
> 通过Socket从客户端访问！
>
> DockerServer 接收到Docker-Client的指令，就会执行这个命令！
>

![img](http://qxmapdepot.xiaoq11.cn/picture/559c1a1c8ee9a42db804b3ad0cf9c8d8.png)

## docker为什么比VM（虚拟机）快？

- Docker有着比虚拟机更少的抽象层。
- docker利用的是宿主机的内核，vm需要是Guest OS。

![img](http://qxmapdepot.xiaoq11.cn/picture/ed334b904a3ed287a96711130b9d9735.png)

1. 新建一个容器的时候，docker不需要像虚拟机一样重新加载一个操作系统内核，避免引导。
2. 虚拟机是加载GuestOS，分钟级别的，而docker是利用宿主机的操作系统，省略了这个复杂的过程，秒级！

## Docker和虚拟机技术的区别：

- 传统的虚拟机，可以虚拟出一条硬件，运行一个完整的操作系统，在这个操作系统上安装和运行所需的软件
- 容器内的应用可以直接运行在宿主 主机的内核中，容器没有自己的内核，也不用虚拟硬件 （轻便）
- 每个容器是相互隔离的，每个容器内都有属于自己的文件系统，之间互不影响。

> 容器化技术：（容器化技术不是模拟的一个完整的操作系统）



# Docker可视化界面工具

##  什么是portainer ?

Docker图形化界面管理工具！提供一个后台面板供我们操作！

类似于 宝塔面板

## 安装

8088 外网访问端口 9000 是内部映射端口

```dockerfile
docker run -d -p 8088:9000 --restart=always -v /var/run/docker.sock:/var/run/docker.sock --privileged=true portainer/portainer
```


访问测试：http://ip:8088

![img](http://qxmapdepot.xiaoq11.cn/picture/fb377d03db72fc9529b6d5b2d2273ffa.png)

选择本地的：Local

![img](http://qxmapdepot.xiaoq11.cn/picture/b85df53e368680c439603d4f05c875e4.png)

进入之后的面板

![img](http://qxmapdepot.xiaoq11.cn/picture/73e489b8505443a1902cebae98aad9ba.png)