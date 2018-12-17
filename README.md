# VpnTree
VPN技术研究


<pre>
      VPN提供了一种通过公用网络安全的对用户进行访问的连接方式。

      VPN连接使用隧道作为传输通道，这个隧道是建立在公共网络基础之上的。VPN依靠3项技术保证
   通信的安全性：隧道协议，身份认证，数据加密
</pre>

使用VPN访问图

![](https://i.imgur.com/4WCHO7k.png)

<pre>
VPN工作原理：

      1、通常情况下，VPN网关采取双网卡结构，外网卡使用公网IP接入Internet。
　　  2、网络一（假定为公网internet）的终端A访问网络二（假定为公司内网）的终端B，其发出的
        访问数据包的目标地址为终端B的内部IP地址。

　　  3、网络一的VPN网关在接收到终端A发出的访问数据包时对其目标地址进行检查，如果目标地址
       属于网络二的地址，则将该数据包进行封装，封装的方式根据所采用的VPN技术不同而不同，
       同时VPN网关会构造一个新VPN数据包，并将封装后的原数据包作为VPN数据包的负载，VPN数
       据包的目标地址为网络二的VPN网关的外部地址。

　　  4、网络一的VPN网关将VPN数据包发送到Internet，由于VPN数据包的目标地址是网络二的VPN
        网关的外部地址，所以该数据包将被Internet中的路由正确地发送到网络二的VPN网关。

　　  5、网络二的VPN网关对接收到的数据包进行检查，如果发现该数据包是从网络一的VPN网关发
       出的，即可判定该数据包为VPN数据包，并对该数据包进行解包处理。解包的过程主要是先将
       VPN数据包的包头剥离，再将数据包反向处理还原成原始的数据包。

　　  6、网络二的VPN网关将还原后的原始数据包发送至目标终端B，由于原始数据包的目标地址是终
        端B的IP，所以该数据包能够被正确地发送到终端B。在终端B看来，它收到的数据包就和从终
        端A直接发过来的一样。

　　  7、从终端B返回终端A的数据包处理过程和上述过程一样，这样两个网络内的终端就可以相互通
        讯了
</pre>