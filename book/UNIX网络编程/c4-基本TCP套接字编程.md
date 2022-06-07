# TCP 客户/服务端交互

# 句柄

- 监听套接字(listening socket)句柄
- 已连接套接字(connected socket)句柄
- 区别
  - 数量: 一个服务器通常只创建一个监听套接字; 内核为服务器接收的每个连接创建一个已连接套接字
  - 生命周期: 监听套接字在服务器的生命周期中一直存在; 已连接套接字在三次握手完成时创建, 在连接关闭时销毁
  - 句柄创建函数
    - 监听套接字: `int socket(int family, int type, int protocol)`
    - 已连接套接字: `int accept(int sockfd, struct sockaddr *cliaddr, socklen_t *addrlen)`

# socket

```c
<sys/socket.h>
int socket(int family, int type, int protocol)
```

- 功能
  - 服务端/客户端都需要使用此函数创建一个监听套接字句柄
- 签名
  - family: 协议簇. AF 或 PF 开头的值, 建议使用 AF 开头的值
  - type: 套接字类型
  - protocol: 协议类型
- 返回值: 成功时返回套接字句柄, 非负数
- type(套接字类型)的取值

|      type      |      说明      |
| :------------: | :------------: |
|  SOCK_STREAM   |     字节流     |
|   SOCK_DGRAM   |     数据报     |
|    SOCK_RAW    |   原始套接字   |
|    SOCK_RDM    |                |
| SOCK_SEQPACKET | 有序分组套接字 |

- protocol(协议类型)的取值

|   protocol   |     说明      |
| :----------: | :-----------: |
|   IPPROTO    | TCP 传输协议  |
| IPPROTO_UDP  | UDP 传输协议  |
| IPPROTO_SCTP | SCTP 传输协议 |

- [ ] SOCK_RDM 的作用
- [ ] 套接字类型在使用上的区别

# connect

```c
<sys/socket.h>
int connect(int sockfd, const struct sockaddr *servaddr, socklen_t addrlen)
```

- 功能: 客户端使用此方法与服务端建立连接
- 签名
  - sockfd传入的是`socket(..)`的返回值
- 返回值
  - 成功返回0

- [ ] connect的异常情况


# bind

```c
<sys/socket.h>
int bind(int sockfd, const struct *myaddr, socklen_t addrlen)
```
