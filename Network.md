### 题目列表

1. OSI, TCP/IP, 五层协议的体系结构 以及各层协议.
2. IP地址的分类
3. ARP是地址解析协议, 简单语言解释一下工作原理
4. ICMP协议
5. TFTP协议
6. HTTP协议
7. NAT协议
8. DHCP协议
9. RARP协议
10. TCP三次握手和四次挥手全过程
11. 在浏览器输入www.baidu.com后执行的全部过程
12. TCP和UDP的区别
13. DNS域名系统, 简单描述其工作原理
14. TCP的三次握手过程？为什么会采用三次握手，若采用二次握手可以吗？
15. 交换机, 路由器, 网关的概念与用途:


#### 1.OSI, TCP/IP, 五层协议的体系结构 以及各层协议.

- OSI协议 (7层): 物理层, 数据链路层,网络层, 运输层, 会话层, 表示层, 应用层.
- TCP/IP协议(4层): 网际接口层, 网络层, 运输层,应用层.
- 五层协议(5层): 物理层, 数据链路层, 网络层,运输层,应用层.

|                            |                             功能                             |             常见              |                 协议                  |
| :------------------------: | :----------------------------------------------------------: | :---------------------------: | :-----------------------------------: |
|   物理层<br />(比特Bit)    |     设备间接收或发送比特流;<br />说明电压,线路和线缆等.      |   中继器,网线,集线器,HUB等    |        RJ45, CLOCK,IEEE802.3等        |
| 数据链路层<br />(帧Frame)  | 将比特组合成字节, 进而组合成帧;<br />用MAC地址访问介质; <br />错误可以被发现但不能被纠正. |    网卡,网桥,二层交换机等     |       PPP, FR, HDLC,VLAN,MAC等        |
| 网络层<br />(数据包Packet) |              负责数据包从源到宿的传递和网际互联              |  路由器,多层交换机,防火墙等.  | IP, ICMP,ARP,PARP,OSPF,IPX,RIP,IGRP等 |
|           运输层           |      可靠或者不可靠数据传输;<br />数据重传前的错误纠正.      |      进程, 端口(Socket)       |             TCP, UDP,SPX              |
|           会话层           |    保证不同应用程序的数据独立;<br />建立,管理和终止回话.     | 服务器验证用户登录, 断点续传. |          NFS,SQL,NetBIOS,RPC          |
|           表示层           | 数据表示;加密与解密,数据的压缩与解压缩, 图片编码与解码等特殊处理过程. | URL加密,口令加密,图片编解码等 |            JPEG,MPEG,ASCII            |
|           应用层           |                           用户接口                           |              --               | FTP,DNS,Telnet,SNMP,SMTP,HTTP,WWW,NFS |

#### 2. IP地址的分类

A类地址: 第一个字节范围: 1~127(1.0.0.0 - 127.255.255.255)

B类地址: 第一个字节范围: 128~191(128.0.0.0 - 191.255.255.255)

C类地址: 第一个字节范围: 192~223(192.0.0.0 - 223.255.255.255)

D类地址: 第一个字节范围: 224~239（224.0.0.0 - 239.255.255.255）

E类地址: 保留;

#### 3. ARP是地址解析协议, 简单语言解释一下工作原理

1. 首先, 每个主机都会在自己的ARP缓冲区建立一个ARP列表, 以表示IP地址和MAC地址之间的对应关系.
2. 当源主机要发送数据时, 首先检查ARP列表中有没有对应IP地址的目的主机的MAC地址, 如果有, 则直接发送数据, 如果没有, 就向本网段的所有主机发送ARP数据包, 该数据包包括的内容有: 源主机IP地址, 源主机MAC地址,目的主机的IP地址.
3. 当本网络的所有主机收到该ARP数据包时, 首先检查数据包中的IP地址是否是自己的IP地址, 如果不是则忽略该数据包, 如果是, 则首先从数据包中取出源主机的IP和MAC地址写入到ARP列表中, 如果已经存在, 则覆盖, 然后将自己的MAC地址写入到ARP响应包中, 告诉源主机自己是它想要找的MAC地址.
4. 源主机收到ARP响应包后. 将目的主机的IP和MAC地址写入ARP列表，并利用此信息发送数据。如果源主机一直没有收到ARP响应数据包，表示ARP查询失败。

#### 4. ICMP协议

ICMP协议: 网际控制报文协议; 它是TCP/IP协议族的一个子协议, 用于在IP主机, 路由器之间传递控制消息.

#### 5. TFTP协议

TFTP协议: Trivial File Transfer Protocol,简单文件传输协议; 用于在客户机和服务器之间进行简单的文件传输的协议, 提供并不复杂, 开销不大的文件传输服务.

#### 6. HTTP协议

超文本传输协议:  是一个属于应用层的面向对象的协议,简洁快速, 适用于分布式超媒体信息系统;

#### 7. NAT协议

网络地址转换协议: 专用网内部的主机使用本地 IP 地址又想和互联网上的主机通信时, 可以使用 NAT 来将本地 IP 转换为全球 IP. (一种将私有地址转化为合法IP地址的转换技术)

#### 8. DHCP协议

动态主机配置协议, 是一种让系统得以连接到网络上, 并获取所有的配置参数手段, 使用UDP协议工作. 具体用途: 给内部网络或网络服务供应商自动分配IP地址, 给用户或者内部网络管理员作为对所有计算机作中央管理的手段.

#### 9. RARP协议

RARP协议是逆地址解析协议. 作用是完成硬件地址到IP地址的映射，主要用于无盘工作站，因为给无盘工作站配置的IP地址不能保存。工作流程：在网络中配置一台RARP服务器，里面保存着IP地址和MAC地址的映射关系，当无盘工作站启动后，就封装一个RARP数据包，里面有其MAC地址，然后广播到网络上去，当服务器收到请求包后，就查找对应的MAC地址的IP地址装入响应报文中发回给请求者。因为需要广播请求报文，因此RARP只能用于具有广播能力的网络。

#### 10. TCP三次握手和四次挥手全过程

![](img/TCP_1.png)

第一次握手: 客户端发送syn包(syn=x)到服务器，并进入SYN_SENT状态，等待服务器确认；

第二次握手: 服务器收到syn包，必须确认客户的SYN（ack=x+1），同时自己也发送一个SYN包（syn=y），即SYN+ACK包，此时服务器进入SYN_RECV状态；

第三次握手: 客户端收到服务器的SYN＋ACK包，向服务器发送确认包ACK(ack=y+1)，此包发送完毕，客户端和服务器进入ESTABLISHED状态，完成三次握手。

**三次握手的原因**: 第三次握手是为了防止失效的连接请求到达服务器，让服务器错误打开连接。

失效的连接请求是指，客户端发送的连接请求在网络中滞留，客户端因为没及时收到服务器端发送的连接确认，因此就重新发送了连接请求。滞留的连接请求并不是丢失，之后还是会到达服务器。如果不进行第三次握手，那么服务器会误认为客户端重新请求连接，然后打开了连接。但是并不是客户端真正打开这个连接，因此客户端不会给服务器发送数据，这个连接就白白浪费了。

![](img/TCP_2.jpg)



第一次挥手：主动关闭方发送一个FIN，用来关闭主动方到被动关闭方的数据传送，也就是主动关闭方告诉被动关闭方：我已经不 会再给你发数据了(当然，在fin包之前发送出去的数据，如果没有收到对应的ack确认报文，主动关闭方依然会重发这些数据)，但是，此时主动关闭方还可 以接受数据。
第二次挥手：被动关闭方收到FIN包后，发送一个ACK给对方，确认序号为收到序号+1（与SYN相同，一个FIN占用一个序号）。
第三次挥手：被动关闭方发送一个FIN，用来关闭被动关闭方到主动关闭方的数据传送，也就是告诉主动关闭方，我的数据也发送完了，不会再给你发数据了。
第四次挥手：主动关闭方收到FIN后，发送一个ACK给被动关闭方，确认序号为收到序号+1，至此，完成四次挥手。

#### 11. 在浏览器输入www.baidu.com后执行的全部过程

简单的说:

- 查找域名对应的IP地址。这一步会依次查找浏览器缓存，系统缓存，路由器缓存，ISPNDS缓存，根域名服务器
- 浏览器向IP对应的web服务器发送一个HTTP请求
- 服务器响应请求，发回网页内容
- 浏览器解析网页内容

也可以这么说:

1、客户端浏览器通过DNS解析到[www.baidu.com](http://www.baidu.com/) 的IP地址220.181.27.48，通过这个IP地址找到客户端到服务器的路径。客户端浏览器发起一个HTTP会话到220.181.27.48，然后通过TCP进行封装数据包，输入到网络层。
2、在客户端的传输层，把HTTP会话请求分成报文段，添加源和目的端口，如服务器使用80端口监听客户端的请求，客户端由系统随机选择一个端口如5000，与服务器进行交换，服务器把相应的请求返回给客户端的5000端口。然后使用IP层的IP地址查找目的端。
3、客户端的网络层不用关心应用层或者传输层的东西，主要做的是通过查找路由表确定如何到达服务器，期间可能经过多个路由器，这些都是由路由器来完成的工作，我不作过多的描述，无非就是通过查找路由表决定通过那个路径到达服务器。
4、客户端的链路层，包通过链路层发送到路由器，通过邻居协议查找给定IP地址的MAC地址，然后发送ARP请求查找目的地址，如果得到回应后就可以使用ARP的请求应答交换的IP数据包现在就可以传输了，然后发送IP数据包到达服务器的地址。

#### 12. TCP和UDP的区别

TCP提供面向连接的,可靠的数据流传输. 而UDP提供的是无连接的, 尽最大努力的数据传输服务. 

TCP传输单位是TCP报文段. UDP传输单位成为用户数据报

TCP注重数据安全性, UDP数据传输快, 因为不需要链接等待, 少了许多操作, 但是其安全性却一般.

TCP与UDP对应的协议:

TCP:

（1） FTP：定义了文件传输协议，使用21端口。
（2） Telnet：一种用于远程登陆的端口，使用23端口，用户可以以自己的身份远程连接到计算机上，可提供基于DOS模式下的通信服务。
（3） SMTP：邮件传送协议，用于发送邮件。服务器开放的是25号端口。
（4） POP3：它是和SMTP对应，POP3用于接收邮件。POP3协议所用的是110端口。
（5）HTTP：是从Web服务器传输超文本到本地浏览器的传送协议。

UDP:

（1） DNS：用于域名解析服务，将域名地址转换为IP地址。DNS用的是53号端口。
（2） SNMP：简单网络管理协议，使用161号端口，是用来管理网络设备的。由于网络设备很多，无连接的服务就体现出其优势。
（3） TFTP(Trival File Transfer Protocal)，简单文件传输协议，该协议在熟知端口69上使用UDP服务。

#### 13. DNS域名系统, 简单描述其工作原理

把主机名解析为 IP 地址。

被设计成分布式系统。

##### 层级结构:

一个域名由多个层次构成，从上层到下层分别为顶级域名、二级域名、三级域名以及四级域名。所有域名可以画成一颗域名树。

域名服务器可以分为以下四类：

1. 根域名服务器：解析顶级域名；
2. 顶级域名服务器：解析二级域名；
3. 权限域名服务器：解析区内的域名；
4. 本地域名服务器：也称为默认域名服务器。可以在其中配置高速缓存。

##### 解析过程

主机向本地域名服务器解析的过程采用递归，而本地域名服务器向其它域名服务器解析可以使用递归和迭代两种方式。

迭代的方式下，本地域名服务器向一个域名服务器解析请求解析之后，结果返回到本地域名服务器，然后本地域名服务器继续向其它域名服务器请求解析；而递归的方式下，结果不是直接返回的，而是继续向前请求解析，最后的结果才会返回。

#### 

建立连接的过程是利用客户服务器模式，假设主机A为客户端，主机B为服务器端。

（1）TCP的三次握手过程：主机A向B发送连接请求；主机B对收到的主机A的报文段进行确认；主机A再次对主机B的确认进行确认。
（2）采用三次握手是为了防止失效的连接请求报文段突然又传送到主机B，因而产生错误。失效的连接请求报文段是指：主机A发出的连接请求没有收到主机B的确认，于是经过一段时间后，主机A又重新向主机B发送连接请求，且建立成功，顺序完成数据传输。考虑这样一种特殊情况，主机A第一次发送的连接请求并没有丢失，而是因为网络节点导致延迟达到主机B，主机B以为是主机A又发起的新连接，于是主机B同意连接，并向主机A发回确认，但是此时主机A根本不会理会，主机B就一直在等待主机A发送数据，导致主机B的资源浪费。
（3）采用两次握手不行，原因就是上面说的实效的连接请求的特殊情况。

#### 15. 交换机, 路由器, 网关的概念与用途:

1）交换机
在计算机网络系统中，交换机是针对共享工作模式的弱点而推出的。交换机拥有一条高带宽的背部总线和内部交换矩阵。交换机的所有的端口都挂接在这条背 部总线上，当控制电路收到数据包以后，处理端口会查找内存中的地址对照表以确定目的MAC（网卡的硬件地址）的NIC（网卡）挂接在哪个端口上，通过内部 交换矩阵迅速将数据包传送到目的端口。目的MAC若不存在，交换机才广播到所有的端口，接收端口回应后交换机会“学习”新的地址，并把它添加入内部地址表 中。
交换机工作于OSI参考模型的第二层，即数据链路层。交换机内部的CPU会在每个端口成功连接时，通过ARP协议学习它的MAC地址，保存成一张 ARP表。在今后的通讯中，发往该MAC地址的数据包将仅送往其对应的端口，而不是所有的端口。因此，交换机可用于划分数据链路层广播，即冲突域；但它不 能划分网络层广播，即广播域。
交换机被广泛应用于二层网络交换，俗称“二层交换机”。
交换机的种类有：二层交换机、三层交换机、四层交换机、七层交换机分别工作在OSI七层模型中的第二层、第三层、第四层盒第七层，并因此而得名。
2）路由器
路由器（Router）是一种计算机网络设备，提供了路由与转送两种重要机制，可以决定数据包从来源端到目的端所经过 的路由路径（host到host之间的传输路径），这个过程称为路由；将路由器输入端的数据包移送至适当的路由器输出端(在路由器内部进行)，这称为转 送。路由工作在OSI模型的第三层——即网络层，例如网际协议。
路由器的一个作用是连通不同的网络，另一个作用是选择信息传送的线路。 路由器与交换器的差别，路由器是属于OSI第三层的产品，交换器是OSI第二层的产品(这里特指二层交换机)。
3）网关
网关（Gateway），网关顾名思义就是连接两个网络的设备，区别于路由器（由于历史的原因，许多有关TCP/IP 的文献曾经把网络层使用的路由器（Router）称为网关，在今天很多局域网采用都是路由来接入网络，因此现在通常指的网关就是路由器的IP），经常在家 庭中或者小型企业网络中使用，用于连接局域网和Internet。 网关也经常指把一种协议转成另一种协议的设备，比如语音网关。
在传统TCP/IP术语中，网络设备只分成两种，一种为网关（gateway），另一种为主机（host）。网关能在网络间转递数据包，但主机不能 转送数据包。在主机（又称终端系统，end system）中，数据包需经过TCP/IP四层协议处理，但是在网关（又称中介系 统，intermediate system）只需要到达网际层（Internet layer），决定路径之后就可以转送。在当时，网关 （gateway）与路由器（router）还没有区别。
在现代网络术语中，网关（gateway）与路由器（router）的定义不同。网关（gateway）能在不同协议间移动数据，而路由器（router）是在不同网络间移动数据，相当于传统所说的IP网关（IP gateway）。
网关是连接两个网络的设备，对于语音网关来说，他可以连接PSTN网络和以太网，这就相当于VOIP，把不同电话中的模拟信号通过网关而转换成数字信号，而且加入协议再去传输。在到了接收端的时候再通过网关还原成模拟的电话信号，最后才能在电话机上听到。
对于以太网中的网关只能转发三层以上数据包，这一点和路由是一样的。而不同的是网关中并没有路由表，他只能按照预先设定的不同网段来进行转发。网关最重要的一点就是端口映射，子网内用户在外网看来只是外网的IP地址对应着不同的端口，这样看来就会保护子网内的用户。

