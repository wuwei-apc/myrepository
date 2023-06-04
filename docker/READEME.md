<!--
 * @Author: zpc 2827985512@qq.com
 * @Date: 2023-06-04 22:41:18
 * @LastEditors: zpc 2827985512@qq.com
 * @LastEditTime: 2023-06-04 23:01:43
 * @FilePath: \repository\docker\READEME.md
 * @Description: 这是学习docker的笔记
-->

## docker学习
> 概述：docker是一个开源的应用容器引擎，基于go语言并遵从Apache2.0协议开源。docker可以让开发者打包他们的应用以及依赖包到一个可移植的容器中，然后发布到任何流行的Linux机器上，也可以实现虚拟化。容器是完全使用沙箱机制，相互之间不会有任何接口。
> ## 预备
> >  一、安装
> >  > 1. [windows安装](https://www.runoob.com/docker/windows-docker-install.html)
> >  > 2. [linux安装](https://www.runoob.com/docker/centos-docker-install.html)

### 一、基础学习
#### 1.1 docker基础
> 1. docker是什么？
> > docker是一个开源的应用容器引擎，基于go语言并遵从Apache2.0协议开源。docker可以让开发者打包他们的应用以及依赖包到一个可移植的容器中，然后发布到任何流行的Linux机器上，也可以实现虚拟化。容器是完全使用沙箱机制，相互之间不会有任何接口。
> 2. docker的优势
> > 1. 更高效的利用系统资源
> > 2. 更快速的启动时间
> > 3. 一致的运行环境
> > 4. 持续交付和部署
> > 5. 更轻松的迁移
> > 6. 更轻松的维护和扩展
> 3. docker的组成
> > 1. docker客户端和服务器
> > 2. docker镜像
> > 3. Registry
> > 4. docker容器
> 4. docker的基本概念
> > 1. 镜像（Image）
> > 2. 容器（Container）
> > 3. 仓库（Repository）
> 5. docker的安装
> > 1. [windows安装](https://www.runoob.com/docker/windows-docker-install.html)
> > 2. [linux安装](https://www.runoob.com/docker/centos-docker-install.html)
> 6. docker的常用命令
> > 1. docker version 查看docker版本
> > 2. docker info 查看docker系统信息
> > 3. docker images 查看本地镜像
> > 4. docker search 镜像名 搜索镜像
> > 5. docker pull 镜像名 下载镜像
> > 6. docker rmi 镜像名 删除镜像
> > 7. docker run 镜像名 运行镜像
> > 8. docker ps 查看运行中的容器
> > 9. docker ps -a 查看所有容器
> > 10. docker start 容器id 启动容器
> > 11. docker stop 容器id 停止容器
> > 12. docker rm 容器id 删除容器
> > 13. docker exec -it 容器id /bin/bash 进入容器
> > 14. docker commit 容器id 镜像名:版本号 提交容器
> > 15. docker logs 容器id 查看容器日志
> > 16. docker cp 容器id:容器内路径 宿主机路径 从容器拷贝文件到宿主机
> > 17. docker cp 宿主机路径 容器id:容器内路径 从宿主机拷贝文件到容器
> > 18. docker save -o 文件名.tar 镜像名:版本号 保存镜像到本地
> > 19. docker load -i 文件名.tar 加载本地镜像
> > 20. docker build -t 镜像名:版本号 . 构建镜像
> > 21. docker tag 镜像名:版本号 新镜像名:版本号 给镜像打标签
> > 22. docker push 镜像名:版本号 推送镜像到远程仓库
> > 23. docker login 登录远程仓库
> > 24. docker logout 退出远程仓库
> > 25. docker network ls 查看网络
> > 26. docker network create --driver bridge 网络名 创建网络
> > 27. docker network inspect 网络名 查看网络详细信息
> > 28. docker network connect 网络名 容器id 将容器连接到网络
> > 29. docker network disconnect 网络名 容器id 将容器断开网络
> > 30. docker network rm 网络名 删除网络
> > 31. docker network prune 删除所有未使用的网络
> > 32. docker volume ls 查看数据卷
> > 33. docker volume create 数据卷名 创建数据卷
> > 34. docker volume inspect 数据卷名 查看数据卷详细信息
> > 35. docker volume rm 数据卷名 删除数据卷
> > 36. docker volume prune 删除所有未使用的数据卷
> > 37. docker run -d --name 容器名 -p 本机端口:容器端口 镜像名 后台运行容器
> > 38. docker run -d --name 容器名 -p 本机端口:容器端口 -v 宿主机路径:容器路径 镜像名 后台运行容器并挂载数据卷
> > 39. docker run -d --name 容器名 -p 本机端口:容器端口 --network 网络名 镜像名 后台运行容器并连接网络
> > 40. docker run -d --name 容器名 -p 本机端口:容器端口 --network 网络名 --ip ip地址 镜像名 后台运行容器并连接网络并指定ip
> > 41. docker run -d --name 容器名 -p 本机端口:容器端口 --network 网络名 -v 宿主机路径:容器路径 镜像名 后台运行容器并连接网络并挂载数据卷
> > 42. docker run -d --name 容器名 -p 本机端口:容器端口 --network 网络名 --ip ip地址 -v 宿主机路径:容器路径 镜像名 后台运行容器并连接网络并指定ip并挂载数据卷
> > 43. docker run -d --name 容器名 -p 本机端口:容器端口 --network 网络名 --ip ip地址 -v 宿主机路径:容器路径 -e 环境变量名=环境变量值 镜像名 后台运行容器并连接网络并指定ip并挂载数据卷并设置环境变量
> > 44. docker run -d --name 容器名 -p 本机端口:容器端口 --network 网络名 --ip ip地址 -v 宿主机路径:容器路径 -e 环境变量名=环境变量值 --restart=always 镜像名 后台运行容器并连接网络并指定ip并挂载数据卷并设置环境变量并设置容器重启策略
> > 45. docker run -d --name 容器名 -p 本机端口:容器端口 --network 网络名 --ip ip地址 -v 宿主机路径:容器路径 -e 环境变量名=环境变量值 --restart=always --privileged=true 镜像名 后台运行容器并连接网络并指定ip并挂载数据卷并设置环境变量并设置容器重启策略并设置容器拥有最高权限
> > 46. docker run -d --name 容器名 -p 本机端口:容器端口 --network 网络名 --ip ip地址 -v 宿主机路径:容器路径 -e 环境变量名=环境变量值 --restart=always --privileged=true --link 容器名:别名 镜像名 后台运行容器并连接网络并指定ip并挂载数据卷并设置环境变量并设置容器重启策略并设置容器拥有最高权限并连接其他容器
> > 47. docker run -d --name 容器名 -p 本机端口:容器端口 --network 网络名 --ip ip地址 -v 宿主机路径:容器路径 -e 环境变量名=环境变量值 --restart=always --privileged=true --link 容器名:别名 -v 宿主机路径:容器路径 镜像名 后台运行容器并连接网络并指定ip并挂载数据卷并设置环境变量并设置容器重启策略并设置容器拥有最高权限并连接其他容器并挂载其他容器数据卷
> > 48. docker run -d --name 容器名 -p 本机端口:容器端口 --network 网络名 --ip ip地址 -v 宿主机路径:容器路径 -e 环境变量名=环境变量值 --restart=always --privileged=true --link 容器名:别名 -v 宿主机路径:容器路径 -v 数据卷名:容器路径 镜像名 后台运行容器并连接网络并指定ip并挂载数据卷并设置环境变量并设置容器重启策略并设置容器拥有最高权限并连接其他容器并挂载其他容器数据卷并挂载数据卷
> > 49. docker run -d --name 容器名 -p 本机端口:容器端口 --network 网络名 --ip ip地址 -v 宿主机路径:容器路径 -e 环境变量名=环境变量值 --restart=always --privileged=true --link 容器名:别名 -v 宿主机路径:容器路径 -v 数据卷名:容器路径 -e 环境变量名=环境变量值 镜像名 后台运行容器并连接网络并指定ip并挂载数据卷并设置环境变量并设置容器重启策略并设置容器拥有最高权限并连接其他容器并挂载其他容器数据卷并挂载数据卷并设置环境变量

## 三、Dockerfile
### 1. Dockerfile是什么
> Dockerfile是一个文本文件，其内包含了一条条的指令(Instruction)，每一条指令构建一层，因此每一条指令的内容，就是描述该层应当如何构建。
### 2. Dockerfile指令
> Dockerfile指令分为两类，一类是构建指令，另一类是设置指令。
> 构建指令包括：FROM、RUN、COPY、ADD、CMD、ENTRYPOINT、ENV、EXPOSE、VOLUME、USER、WORKDIR、ONBUILD。
> 设置指令包括：MAINTAINER、LABEL、STOPSIGNAL、HEALTHCHECK、ARG、SHELL。
> 构建指令和设置指令的区别在于，构建指令用于构建镜像，设置指令用于设置镜像。

### 3. Dockerfile指令详解
> FROM：指定基础镜像，必须为第一条指令，且必须存在，后续指令都依赖于该指令指定的镜像。
> RUN：执行命令，有两种格式，一种是shell格式，另一种是exec格式。
> shell格式：RUN <命令>，例如：RUN echo "hello docker" > /home/hello.txt。
> exec格式：RUN ["可执行文件", "参数1", "参数2"]，例如：RUN ["echo", "hello docker"]。
> shell格式会启动一个shell，然后再shell中执行命令，而exec格式则是直接执行命令，推荐使用exec格式。
> COPY：复制文件，有两个参数，源路径和目标路径，源路径可以是Dockerfile所在目录的相对路径，也可以是一个URL，目标路径必须是容器内的绝对路径。
> ADD：复制文件，功能和COPY一样，但是ADD还可以自动解压缩文件，有两个参数，源路径和目标路径，源路径可以是Dockerfile所在目录的相对路径，也可以是一个URL，目标路径必须是容器内的绝对路径。
> CMD：指定容器启动时要执行的命令，有三种格式，分别是exec格式、shell格式和健康检查格式。
> exec格式：CMD ["可执行文件", "参数1", "参数2"]，推荐使用exec格式。
> shell格式：CMD 命令 参数1 参数2，例如：CMD echo "hello docker"。
> 健康检查格式：CMD ["CMD-SHELL", "命令"]，例如：CMD ["CMD-SHELL", "curl -f http://localhost/ || exit 1"]。
> ENTRYPOINT：指定容器启动时要执行的命令，有两种格式，分别是exec格式和shell格式。
> exec格式：ENTRYPOINT ["可执行文件", "参数1", "参数2"]，推荐使用exec格式。
> shell格式：ENTRYPOINT 命令 参数1 参数2，例如：ENTRYPOINT echo "hello docker"。
> ENV：设置环境变量，有两种格式，分别是键值对格式和只有键没有值格式。
> 键值对格式：ENV 键 值，例如：ENV MYSQL_ROOT_PASSWORD 123456。
> 只有键没有值格式：ENV 键，例如：ENV MYSQL_ROOT_PASSWORD。
> EXPOSE：声明端口，有两种格式，分别是声明一个端口和声明多个端口。
> 声明一个端口：EXPOSE 端口，例如：EXPOSE 3306。
> 声明多个端口：EXPOSE 端口1 端口2 端口3，例如：EXPOSE 3306 3307 3308。
> VOLUME：声明匿名卷，有两种格式，分别是声明一个匿名卷和声明多个匿名卷。
> 声明一个匿名卷：VOLUME 容器内路径，例如：VOLUME /data。
> 声明多个匿名卷：VOLUME 容器内路径1 容器内路径2 容器内路径3，例如：VOLUME /data1 /data2 /data3。
> USER：指定运行容器时的用户名或UID，后续的RUN、CMD和ENTRYPOINT都会使用该用户。
> WORKDIR：指定工作目录，后续的RUN、CMD和ENTRYPOINT都会使用该目录。
> ONBUILD：触发器指令，当所创建的镜像作为其他新创建镜像的基础镜像时，触发器指令会执行。
> MAINTAINER：指定镜像创建者的姓名和邮箱地址。
### 4. Dockerfile构建镜像
> 1. 编写Dockerfile文件
> 2. 执行docker build命令构建镜像
> 3. 执行docker run命令运行容器
> 4. 执行docker push命令推送镜像
> 5. 执行docker pull命令拉取镜像
> 6. 执行docker rmi命令删除镜像
> 7. 执行docker save命令保存镜像
> 8. 执行docker load命令加载镜像
> 9. 执行docker history命令查看镜像历史
> 10. 执行docker inspect命令查看镜像详细信息
> 11. 执行docker tag命令给镜像打标签
> 12. 执行docker commit命令提交容器副本
> 13. 执行docker export命令导出容器副本
> 14. 执行docker import命令导入容器副本
> 15. 执行docker login命令登录仓库
> 16. 执行docker logout命令退出仓库
> 17. 执行docker search命令搜索镜像
> 18. 执行docker info命令查看Docker系统信息
> 19. 执行docker version命令查看Docker版本信息
> 20. 执行docker events命令查看Docker事件
> 21. 执行docker system命令查看Docker系统信息
> 22. 执行docker top命令查看容器中的进程信息
> 23. 执行docker stats命令查看容器资源占用情况
> 24. 执行docker port命令查看容器端口映射情况
> 25. 执行docker diff命令查看容器文件结构变化情况
> 26. 执行docker exec命令在容器中执行命令
> 27. 执行docker attach命令连接到容器
> 28. 执行docker cp命令在容器和主机之间复制文件
> 29. 执行docker kill命令杀掉容器中的进程
> 30. 执行docker pause命令暂停容器中的所有进程
> 31. 执行docker unpause命令恢复容器中的所有进程
> 32. 执行docker stop命令停止容器
> 33. 执行docker start命令启动容器
> 34. 执行docker restart命令重启容器
> 35. 执行docker wait命令阻塞容器
> 36. 执行docker create命令创建容器
> 37. 执行docker rm命令删除容器
> 38. 执行docker rename命令重命名容器
> 39. 执行docker pause命令暂停容器中的所有进程
> 40. 执行docker unpause命令恢复容器中的所有进程
> 41. 执行docker export命令导出容器副本
> 42. 执行docker logs命令查看容器日志

## 四、Docker网络
### 1. Docker网络模式
> 1. none：无网络模式，不配置网络，只有lo回环网卡，只能使用容器内部的网络，不能和外部通信。
> 2. bridge：桥接模式，使用docker0网桥，容器内部和外部都可以通信，但是容器之间不能通信。
> 3. host：主机模式，使用宿主机网络，容器内部和外部都可以通信，容器之间也可以通信。
> 4. container：容器模式，使用其他容器的网络，容器内部和外部都可以通信，容器之间也可以通信。
> 5. overlay：覆盖网络模式，用于跨主机通信，容器内部和外部都可以通信，容器之间也可以通信。
> 6. macvlan：网卡模式，用于跨主机通信，容器内部和外部都可以通信，容器之间也可以通信。
> 7. ipvlan：IP模式，用于跨主机通信，容器内部和外部都可以通信，容器之间也可以通信。
> 8. none：无网络模式，不配置网络，只有lo回环网卡，只能使用容器内部的网络，不能和外部通信。

### 2. Docker网络命令
> 1. 执行docker network ls命令查看网络列表
> 2. 执行docker network inspect命令查看网络详细信息
> 3. 执行docker network create命令创建网络
 ``` python
  {
     "Name": "bridge",
     "Id": "f0b0e3
     "Scope": "local",
     "Driver": "bridge",
     "EnableIPv6": false,
     "IPAM": {
               "Driver": "default",
               "Options": null,
               "Config": [
                          {
                           "Subnet": "
                           "Gateway": "
                          }
              } 
  }

  ```