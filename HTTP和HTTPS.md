# HTTP和HTTPS

## 1.什么是HTTP？

即超文本传输协议，是一个基于请求与响应，无状态的，**应用层**的协议，常基于TCP/IP协议传输数据，互联网上应用最为广泛的一种网络协议,所有的WWW文件都必须遵守这个标准。设计HTTP的初衷是为了提供一种**发布和接收HTML页面**的方法。

- 基于(传输层)**TCP/IP**(网络层)协议

- 定义了web客户端如何与web服务端对话，以及服务端如何把数据传回客户端

- HTTP是**无连接**的，无连接的含义是限制每次连接只处理一个请求。每次请求需要通过TCP三次握手四次挥手，和服务器重新建立连接。
- HTTP是**无状态**的，无状态是指协议对于事务处理没有记忆能力。



## 2.什么是HTTPS？

HTTPS是一种通过计算机网络进行安全通信的传输协议，经由HTTP进行通信，利用SSL/TLS建立全信道，加密数据包。HTTPS使用的主要目的是提供对网站服务器的身份认证，同时保护**交换数据的隐私与完整性**。



## 3.两者比较

HTTP协议传输数据以明文形式显示。

HTTPS协议传输的不是明文数据。

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210812105948015.png" alt="image-20210812105948015" style="zoom: 67%;" />

## 4.HTTP的通信

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210812110801409.png" alt="image-20210812110801409" style="zoom:50%;" />

HTTP属于TCP/IP模型中的运用层协议

#### TCP的连接建立

##### 三次握手

采用三报文握手主要是为了防止已失效的连接请求报文段突然又传送到了，因而产生错误。

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210812113423400.png" alt="image-20210812113423400" style="zoom:50%;" />

为什么需要三次握手呢？为了防止已失效的连接请求报文段突然又传送到了服务端，因而产生错误。

比如：client发出的第一个连接请求报文段并没有丢失，而是在某个网络结点长时间的滞留了，以致延误到连接释放以后的某个时间才到达server。本来这是一个早已失效的报文段，但是server收到此失效的连接请求报文段后，就误认为是client再次发出的一个新的连接请求，于是就向client发出确认报文段，同意建立连接。假设不采用“三次握手”，那么只要server发出确认，新的连接就建立了，由于client并没有发出建立连接的请求，因此不会理睬server的确认，也不会向server发送数据，但server却以为新的运输连接已经建立，并一直等待client发来数据。所以没有采用“三次握手”，这种情况下server的很多资源就白白浪费掉了。

来源：[某一篇博客](https://blog.csdn.net/xiaoming100001/article/details/81109617)

##### 四次挥手

- 数据传输结束后，通信的双方都可释放连接。

- TCP连接释放过程是四报文握手。

  

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210812113610444.png" alt="image-20210812113610444" style="zoom:50%;" />

为什么需要四次挥手呢？TCP是全双工模式；

- 当client发出FIN报文段时，只是表示client已经没有数据要发送了，client告诉server，它的数据已经全部发送完毕了；

- 但是，这个时候client还是可以接受来server的数据；

- 当server返回ACK报文段时，表示它已经知道client没有数据发送了，但是server还是可以发送数据到client的；

- 当server也发送了FIN报文段时，这个时候就表示server也没有数据要发送了，就会告诉client，我也没有数据要发送了，如果收到client确认报文段，之后彼此就会愉快的中断这次TCP连接。
  

## 5.HTTPS的实现

<img src="C:\Users\kEEpkind-\AppData\Roaming\Typora\typora-user-images\image-20210812152316308.png" alt="image-20210812152316308" style="zoom:67%;" />

