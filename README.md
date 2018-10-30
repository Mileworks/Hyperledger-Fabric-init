# Hyperledger相关整理文档 #

随着该技术发展成熟，早期阶段学习该技术的投资将会不断得到丰厚的回报。  

1.初期技术要求：  
  
  可以配合使用一些插件，方便整个代码查看和Docker 镜像的管理 。  

  golang\Java\Docker\NodeJS\移动端 , 以上前三种是能处理hyperledger前提 。  

  其中chaincode 只能用go 和java 进行开发。  
  
  Docker 用于部署镜像使用。  
  
  注：一定要看白皮书，是后续的总纲 ； 后续可使用k8s。  
  ```
  a. 代码查看-chrome插件 ：  
  https://about.sourcegraph.com/  

  b. Portainer - docker 插件 ：查看CLI 和管理镜像  
  https://portainer.readthedocs.io/en/stable/  

  c. k8s集群搭建 ：  
  https://github.com/wise2c-devops/breeze  

  ```  
    这里使用免登设置的时候注意大致要有5 - 6台设备，其中有一台专门用于部署breeze 控制台程序，大致设备情况如下（实际公司内部情况）：  
    1.Deploy - 121  
    2.k8s01 - 138 - master  
    3.k8s02 - 80 - master  
    4.k8s03 - 101 - minion node
    5.Harbor - 45
    
    【
    参考https://www.linuxidc.com/Linux/2017-04/142632.htm 中的免登配置，  
    注意首先现在121 服务器上进行ssh-copy-id @ip方式将所有服务器内容全部登录信息保存下来。
    进行从121到其他服务器的免登操作。注意web控制台的日志输出，来找到对应的错误信息。
    】

  ```

  ```
  
2.相关能用：  

```
百度网盘资源：（粗略过一遍即可 - 配合白皮书了解大概）  
链接:https://pan.baidu.com/s/1fiEtMnY_hgrQF9sRnKsXtw  密码:9z6i

中文文档：  
https://hyperledgercn.github.io/hyperledgerDocs/ (重点必看！！！)

大致了解其中词汇 ：  
https://hyperledgercn.github.io/hyperledgerDocs/glossary/  

> 有两个词汇要注意：
- Endorsement ：Endorsement 是指一个peer执行一个交易并返回YES-NO给生成交易proposal的client app 的过程。chaincode具有相应的endorsement policies，其中指定了endorsing peer。
- Ordering Service ：将交易排序放入block的节点的集合。ordering service独立于peer流程之外，并以先到先得的方式为网络上所有的channel作交易排序。ordering service先传递block给leading peer ，然后再由leading peer 传递给不同peer 中。

Demo例子：  
https://anders.com/blockchain/coinbase.html  
https://blockchaindemo.io/  
```

3.[Hyperledger网络和Fabric相关部署方法](https://github.com/Mileworks/Hyperledger-Fabric-init/tree/master/1.创建Fabric网络)

4.ChainCode 典例源码：（必须要看，参考书写格式、理解大致使用业务场景）  

https://www.ibm.com/developerworks/cn/cloud/library/cl-ibm-blockchain-chaincode-development-using-golang/index.html?mhq=Hyperledger%20Fabric%20%20%E6%96%87%E4%BB%B6&mhsrc=ibmsearch_a

请注意：这些操作通常由组织或者peer的管理员来完成。这个脚本使用CLI容器来执行这些命令，但SDK中也有支持。

5.本地如何调试ChainCode  

6.ChainCode 用Go 和 Java语言的比较（建议使用Golang）  
