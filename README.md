# 介绍
三个简单的工具：  
- ssh\_client.py: 作为ssh客户端，仅让目标执行一条命令  
- keepalive\_client.py: 作为搭建在渗透目标上的ssh客户端，长时间连接目标的服务器，并反弹自身的shell给服务器  
- ssh\_reverse\_server: 作为ssh服务器，反向获取ssh客户端的shell  
  
# 使用实例
  
![](img/python12md1.png)  

# 技术回顾
本次主要使用了paramiko库来实现ssh的核心功能。  
- 创建客户端的channel的过程为： SSHClient -> Transport -> channel  
- 创建服务端的channel的过程为： socket -> Transport -> channel  
channel可以使用类似socket的各种方法来收发数据，ssh的加密、解密过程会自动完成。  
## 遇到的问题
主要是使用密钥而无密码连接ssh时遇到了各种报错，错误主要集中在known\_hosts文件中没有记录目标主机，尝试了各种解决办法尚未解决，所以先使用了密码登录来代替密钥登录，得以成功执行。  
