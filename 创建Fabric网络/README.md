# Fabric网络构建方法 - 已经全部验证，后续只需要按下面步骤傻瓜式敲入命令

```
  官方例子：
  https://github.com/hyperledger/fabric  
  https://github.com/hyperledger/fabric-samples  
```  

初始目的 ：

利用这些Docker镜像可以快速引导一个由4个代表2个不同组织的peer节点以及一个排序服务节点的Hyperledger fabric网络。  
它还将启动一个容器来运行一个将peer节点加入channel、部署实例化链码服务以及驱动已经部署的链码执行交易的脚本。按照我验证的方式，傻瓜式操作即可。  
这里暂时跳过docker 、docker-compose 、 golang 这些环境的配置。大致步骤如下：

A. 构建第一个fabric 网络

- 在golang运行环境的src目录下，创建src/github.com/hyperledger/，最终目录为

```
~/go/src/github.com/hyperledger/
```

- clone 代码库: 切换到~/go/src/github.com/hyperledger/目录下，使用如下命令克隆fabric-sample仓库。

```
git clone https://github.com/hyperledger/fabric-samples.git
```

- 安装fabric命令、下载docker镜像

```
curl -sSL https://raw.githubusercontent.com/hyperledger/fabric/master/scripts/bootstrap.sh | bash -s 1.3.0
```

该命令执行完成后，当前目录下会出现 bin 目录，里面都是 fabric 的一些命令。另外使用 docker images 可以看到下载了很多镜像，这些镜像都是启动 fabric 要使用的。

> 生成配置文件:   
切换到 first-network 目录，然后执行 ./byfn.sh -m generate, 相关的配置文件会在 crypto-config 目录中生成。如图：  

![Alt text](./pic/1.png)  

> 启动网络:  
运行 ./byfn.sh -m up。看到类似如下内容，说明成功。

![Alt text](./pic/2.png)  

![Alt text](./pic/3.png)  

这样就把一个 fabric 的网络搭建起来了。

> 停止网络:  
运行 ./byfn.sh -m down  