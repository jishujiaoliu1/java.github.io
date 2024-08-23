Network Programming - [Do It Yourself] Write a server and client (TCP) based on C language!
==
If we want to write a server and client ourselves, we need to master certain network programming techniques. Personally, I think the most critical thing in network programming is this thing-socket.

Socket: Simply put, socket is used to describe the IP address and port. It is the handle of a communication chain and can be used to implement communication between different virtual machines or different computers.

✁TCP protocol
TCP protocol: It is a connection-oriented, reliable, byte stream-based transport layer communication protocol, defined by IETF's RFC 793. In the simplified OSI model of computer networks, it completes the functions specified by the fourth layer transport layer

Keywords: three-way handshake, reliable, byte stream-based.
--
Some friends may ask, is TCP just a simple sentence? Of course not. TCP is a very important transmission protocol , and there are many details to know. This article may not be enough to explain it in detail. However, in this article, we only need to understand a few of its key words to understand the following content well.

✁ TCP server and client operation process
As shown in the figure, this is a complete TCP server-client operation flow chart . In fact, I personally think that programs are the same regardless of the language. The core lies in the design of the algorithm and the call of the function. So what do the functions in the figure mean?

1. Create a socket

Socket is a structure created in the kernel

sockfd=socket(AF_INET,SOCK_STREAM,0);   //AF_INT:ipv4, SOCK_STREAM:tcp协议
2. Call the bind function

Bind the socket to the address (including IP and port).

A structure address needs to be defined to convert the host byte order of the port into the network byte order

struct socka ddr_inmyaddr;  //地址结构体 
bind function

bind(sockfd,(structsockaddr*)&myaddr,sizeof(serveraddr))
3. Listen to listen and put the received client connections into the queue

listen(sockfd,8)  //第二个参数是队列长度 
4. Call the accept function, get the request from the queue, and return the socket descriptor

If there is no request, it will block until a connection is obtained.

int fd=accept(sockfd,NULL，NULL);  //这边采用默认参数 
5. Call read/write for two-way communication

6. Close the socket returned by accept

close(scokfd);
Here is the complete code:
If you also want to learn programming, you can come to my C language/C++ programming learning base [click to enter]!

There are also free ones (source code, zero-based tutorials, project-based teaching videos )!

Involving: game development, course design , common software development, basic programming knowledge, hacking, etc...
[31](https://chigua57.pages.dev/31/)
[32](https://chigua57.pages.dev/32/)
[33](https://chigua57.pages.dev/33/)
[34](https://chigua57.pages.dev/34/)
[35](https://chigua57.pages.dev/35/)
[36](https://chigua57.pages.dev/36/)
[37](https://chigua57.pages.dev/37/)
[38](https://chigua57.pages.dev/38/)
[39](https://chigua57.pages.dev/39/)
[40](https://chigua57.pages.dev/40/)
[41](https://chigua57.pages.dev/41/)
[42](https://chigua57.pages.dev/42/)
[43](https://chigua57.pages.dev/43/)
[44](https://chigua57.pages.dev/44/)
[45](https://chigua57.pages.dev/45/)
[46](https://chigua57.pages.dev/46/)
[47](https://chigua57.pages.dev/47/)
[48](https://chigua57.pages.dev/48/)
[49](https://chigua57.pages.dev/49/)
[50](https://chigua57.pages.dev/50/)
[51](https://chigua57.pages.dev/51/)
[52](https://chigua57.pages.dev/52/)
[53](https://chigua57.pages.dev/53/)
[54](https://chigua57.pages.dev/54/)
[55](https://chigua57.pages.dev/55/)
[56](https://chigua57.pages.dev/56/)
[57](https://chigua57.pages.dev/57/)
[58](https://chigua57.pages.dev/58/)
[59](https://chigua57.pages.dev/59/)
[60](https://chigua57.pages.dev/60/)

