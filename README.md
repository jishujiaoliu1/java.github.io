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
[491](https://heiliaozhan6.pages.dev/491/)
[492](https://heiliaozhan6.pages.dev/492/)
[493](https://heiliaozhan6.pages.dev/493/)
[494](https://heiliaozhan6.pages.dev/494/)
[495](https://heiliaozhan6.pages.dev/495/)
[496](https://heiliaozhan6.pages.dev/496/)
[497](https://heiliaozhan6.pages.dev/497/)
[1](https://heiliaozhan4.pages.dev/1/)
[2](https://heiliaozhan4.pages.dev/2/)
[3](https://heiliaozhan4.pages.dev/3/)
[4](https://heiliaozhan4.pages.dev/4/)
[5](https://heiliaozhan4.pages.dev/5/)
[6](https://heiliaozhan4.pages.dev/6/)
[7](https://heiliaozhan4.pages.dev/7/)
[8](https://heiliaozhan4.pages.dev/8/)
[9](https://heiliaozhan4.pages.dev/9/)
[10](https://heiliaozhan4.pages.dev/10/)
[11](https://heiliaozhan4.pages.dev/11/)
[12](https://heiliaozhan4.pages.dev/12/)
[13](https://heiliaozhan4.pages.dev/13/)
[14](https://heiliaozhan4.pages.dev/14/)
[15](https://heiliaozhan4.pages.dev/15/)
[16](https://heiliaozhan4.pages.dev/16/)
[17](https://heiliaozhan4.pages.dev/17/)
[18](https://heiliaozhan4.pages.dev/18/)
[19](https://heiliaozhan4.pages.dev/19/)
[20](https://heiliaozhan4.pages.dev/20/)
[21](https://heiliaozhan4.pages.dev/21/)
[22](https://heiliaozhan4.pages.dev/22/)
[23](https://heiliaozhan4.pages.dev/23/)
[24](https://heiliaozhan4.pages.dev/24/)
[25](https://heiliaozhan4.pages.dev/25/)
[26](https://heiliaozhan4.pages.dev/26/)
[27](https://heiliaozhan4.pages.dev/27/)
[28](https://heiliaozhan4.pages.dev/28/)
[29](https://heiliaozhan4.pages.dev/29/)
[30](https://heiliaozhan4.pages.dev/30/)
[31](https://heiliaozhan4.pages.dev/31/)
[32](https://heiliaozhan4.pages.dev/32/)
[33](https://heiliaozhan4.pages.dev/33/)
[34](https://heiliaozhan4.pages.dev/34/)
[35](https://heiliaozhan4.pages.dev/35/)
[36](https://heiliaozhan4.pages.dev/36/)
[37](https://heiliaozhan4.pages.dev/37/)
[38](https://heiliaozhan4.pages.dev/38/)
[39](https://heiliaozhan4.pages.dev/39/)
[40](https://heiliaozhan4.pages.dev/40/)
[41](https://heiliaozhan4.pages.dev/41/)
[42](https://heiliaozhan4.pages.dev/42/)
[43](https://heiliaozhan4.pages.dev/43/)
[44](https://heiliaozhan4.pages.dev/44/)
[45](https://heiliaozhan4.pages.dev/45/)
[46](https://heiliaozhan4.pages.dev/46/)
[47](https://heiliaozhan4.pages.dev/47/)
[48](https://heiliaozhan4.pages.dev/48/)
[49](https://heiliaozhan4.pages.dev/49/)
[50](https://heiliaozhan4.pages.dev/50/)
[51](https://heiliaozhan4.pages.dev/51/)
[52](https://heiliaozhan4.pages.dev/52/)
[53](https://heiliaozhan4.pages.dev/53/)
[54](https://heiliaozhan4.pages.dev/54/)
[55](https://heiliaozhan4.pages.dev/55/)
[56](https://heiliaozhan4.pages.dev/56/)
[57](https://heiliaozhan4.pages.dev/57/)
[58](https://heiliaozhan4.pages.dev/58/)
[59](https://heiliaozhan4.pages.dev/59/)
[60](https://heiliaozhan4.pages.dev/60/)
[61](https://heiliaozhan4.pages.dev/61/)
[62](https://heiliaozhan4.pages.dev/62/)
[63](https://heiliaozhan4.pages.dev/63/)
[64](https://heiliaozhan4.pages.dev/64/)
[65](https://heiliaozhan4.pages.dev/65/)
[66](https://heiliaozhan4.pages.dev/66/)
[67](https://heiliaozhan4.pages.dev/67/)
[68](https://heiliaozhan4.pages.dev/68/)
[69](https://heiliaozhan4.pages.dev/69/)
[70](https://heiliaozhan4.pages.dev/70/)
[71](https://heiliaozhan4.pages.dev/71/)
[72](https://heiliaozhan4.pages.dev/72/)
[73](https://heiliaozhan4.pages.dev/73/)
[74](https://heiliaozhan4.pages.dev/74/)
[75](https://heiliaozhan4.pages.dev/75/)
[76](https://heiliaozhan4.pages.dev/76/)
[77](https://heiliaozhan4.pages.dev/77/)
[78](https://heiliaozhan4.pages.dev/78/)
[79](https://heiliaozhan4.pages.dev/79/)
[80](https://heiliaozhan4.pages.dev/80/)
[81](https://heiliaozhan4.pages.dev/81/)
[82](https://heiliaozhan4.pages.dev/82/)
[83](https://heiliaozhan4.pages.dev/83/)
[84](https://heiliaozhan4.pages.dev/84/)
[85](https://heiliaozhan4.pages.dev/85/)
[86](https://heiliaozhan4.pages.dev/86/)
[87](https://heiliaozhan4.pages.dev/87/)
[88](https://heiliaozhan4.pages.dev/88/)
[89](https://heiliaozhan4.pages.dev/89/)
[90](https://heiliaozhan4.pages.dev/90/)
[91](https://heiliaozhan4.pages.dev/91/)
[92](https://heiliaozhan4.pages.dev/92/)
[93](https://heiliaozhan4.pages.dev/93/)
[94](https://heiliaozhan4.pages.dev/94/)
[95](https://heiliaozhan4.pages.dev/95/)
[96](https://heiliaozhan4.pages.dev/96/)
[97](https://heiliaozhan4.pages.dev/97/)
[98](https://heiliaozhan4.pages.dev/98/)
[99](https://heiliaozhan4.pages.dev/99/)
[100](https://heiliaozhan4.pages.dev/100/)
[101](https://heiliaozhan4.pages.dev/101/)
[102](https://heiliaozhan4.pages.dev/102/)
[103](https://heiliaozhan4.pages.dev/103/)
[104](https://heiliaozhan4.pages.dev/104/)
[105](https://heiliaozhan4.pages.dev/105/)
[106](https://heiliaozhan4.pages.dev/106/)
[107](https://heiliaozhan4.pages.dev/107/)
[108](https://heiliaozhan4.pages.dev/108/)
[109](https://heiliaozhan4.pages.dev/109/)
[110](https://heiliaozhan4.pages.dev/110/)
[111](https://heiliaozhan4.pages.dev/111/)
[112](https://heiliaozhan4.pages.dev/112/)
[113](https://heiliaozhan4.pages.dev/113/)
[114](https://heiliaozhan4.pages.dev/114/)
