# OSI网络七层(Open Systems Interconnection)
还记得我上大学的时候，在《网络原理》这书本里，我花了很多时间去背的一个概念，就是OSI网络七层。这个概念对理解网络Network非常重要，以至于一直到我前几年的一次线下面试DevOps工作的时候还被要求当场把这七层都写下来。那今天我们就来介绍一下这个网络的最基础概念。</br>

**总的来说，OSI网络七层就是网络中的通用语言，它使得不同设备的操作系统能通过互联网相互通讯**我们知道网络是个很大的话题，它涉及非常多方面的考虑，比如你要考虑如何找到接收方，如果数据包丢失了你要怎么办，你使用什么质地的材料传输信息，如何加密会话，如何控制会话的窗口，等等。为了使网络开发更加高效，人们把所有网络相关的因素分类成了7大类，也就是我们今天介绍的OSI网络七层。这每一类都专注于一个领域的开发，然后每一类都向上下层做成一个服务，这样其他层就可以直接拿去使用，这就有点像我们现在开发常说的模块式开发。这七层从上到下分别是：应用层(Application Layer)，表示层(Presentation Layer)，会话层(Session Layer)，传输层(Transport Layer)，网络层(Network Layer)，数据链路层(Data Link Layer)，物理层(Physical Layer)。我在背诵的时候喜欢用这个顺口溜记：“应表会传网数物”，这个记法用了十几年，好用。</br>

接下来我们一一介绍每一层的作用。</br>

第7层：应用层(Application Layer): 这一层是和计算机用户最接近的一层，这一层的协议主要是直接和用户的软件直接数据交互的，比如我们常用的浏览器或者电子邮件。这一层最常见的协议有HTTP和SMTP(Simple Mail Transfer Protocol一种邮件通讯协议). </br>

第6层：表示层(Presentation Layer):这一层的功能专注于对数据本身的处理，从而应用层可以直接使用这些数据。这个处理主要包括三个方面：转译(Translation), 加密(Encryption)，压缩(Compression)。不同的两台设备可能使用不同的编码方式，这一层就负责解码这些数据，然后使得应用层能够直接读取这些数据，这是转译功能。为了保障数据在传输途中的安全，在发送到网络之前有些数据会被加密，接收方就需要解密，这是加密功能。最后，为了数据能在网络总更高效的传输，我们需要压缩然后解压数据，这就是压缩功能。</br>

第5层：会话层(Session Layer)：这一层专注于开启和关闭两个设备之间的会话(Session)。会话(Session)本身指的是两个设备之间通讯的时长。这一层的功能就是确保这个通讯窗口足够的长，使得所有数据都能被传送完，然后等数据传完了，就关闭这个通讯通道，释放计算机和网络的资源，这样就不会浪费资源了。这一层还有一个很重要的功能，就是同步检查点。举个例子，我们在传送1G大小的文件的时候，这一层就会在传送每5M数据的时候打做一个记录。如果文件中途因为某种原因，中断传输，那下次再传的时候，就不需要重头开始传了，只要从最近的那个检查点开始继续传就好。断电续传就是通过这一层实现的。</br>

第4层：传输层(Transport Layer)：这一层主要负责两点之间端到端的通讯，它在发送端会把我们数据切分成一小段一小段的数据块(segment)然后在接收端会把这些数据块按顺序拼接起来，给下一层使用。这一层还有两个很重要的功能:流量控制(flow control)和错误控制(error control)。流量控制主要是一种传输速度的优化手段，它能确保速度过快的发送方不会让速度太慢的接收方因为传的东西太快而崩溃，就好像你说话太快，有些反应慢的同学都反应不过来，这个功能就是让你说话慢一些。而错误控制则是保证数据段(segment)完整性的机制，它会检测是否所有数据包都传送完整，如果不是，就让发送方重传。我们上篇讲到的TCP/UDP就是属于这一层的协议。</br>

第3层：网络层(Network Layer)：这一层主要负责数据传输导航，换句话说，它就是网络传输中的google map。上一层传输层把数据分成了一小段一小段的数据段(segment)，而这层会把数据拆分成更小的数据包(packet)，然后它根据接收端的地址来选择不同的最佳路径，最终抵达接收方，这就是我们通常说的路由(Routing)。到了接收方之后，再把这些数据包(packet)组装层数据段(segment)，供给传输层使用。我们之前讲的IP就是属于这一层。这一层其他比较出名的协议还有ICMP(Internet Control Message Protocol 你经常使用的ping命令就是用了这个协议), IGMP(Internet Group Message Protocol), IPSec等。值得注意的是这一层的导航只负责在不同网段之间的导航，而在同一个网段之间的导航是由接下来这层数据链路层负责。</br>

第2层：数据链路层(Data Link Layer)：这一层和网络层很像，除了它是负责相同网段之间的数据导航。这就好像送外卖，网络层只负责送到公寓门大厅，至于公寓具体哪一层哪一间房间，这是这一层主要负责的。在这一层里，数据会再进一步被拆分，变成更小的帧(frame)，并且和传输层一样，它也用流量控制(flow control)和错误控制(error control)这两个功能，只不过它针对的完全是同一网段内而已。</br>

第1层：物理层(Physical Layer)：这一层是最”接地气“的一层，因为它负责的都是传输使用的材料，比如光纤或电缆等。它负责把以上所有信息转换成计算机能读懂的一连串的0和1。你只有经过这一层的包装设计，不同材料的设备之间才能区分出啥是0啥是1。</br>

最后，我们把上面的理论连起来，看看你每次在按下邮件发送键后，计算机和网络是如何配合着把你的邮件送达对方的。首先，你的邮件应用软件会把邮件传送给OSI最高层，第7层应用层(Application Layer)，在这一层会使用SMTP协议封装，然后传给下一层第6层表达层(Presentation Layer)，在这一层会压缩一下邮件大小，方便之后在网络上更加高效的传输。然后把这个缩小版的邮件发给下一层，第5层会话层(Session Layer)，开启一段传输。之后传给了第4层，传输层(Transpart Layer)，在这层会被分割成数据段(Segement)，加上TCP端口的信息，然后再发给网络层(Network Layer)，再近一步分割成更小数据包(Packet)，打上IP地址，然后送给第2层数据链路层(Data Link Layer)，再分割成更小的帧(Frame)，最后到达最后一层，物理层(Physical Layer)，转化成一连串的0和1，在数据线和路由器上传输，最后到达对方设备上，反向一层一层把信封扒开，最后把信里的内容呈现在对方的邮件应用软件里。这就是一封信经历的全部旅程。</br>

最后的最后，再提一嘴，虽然OSI七层理论是网络的基础，但是实际生活中使用的是更简化版本的TCP/IP四层，分别是应用层（Application Layer)，传输层(Transport Layer)，网络层(Network Layer)和网络接口层(Network Interface)。你可以大致理解为，OSI七层的应用层，表示层，会话层相当于TCP/IP的应用层，然后传输层和网络层大家都差不多，最后OSI七层的数据链路层和物理层相当于TCP/IP的网络接口层。

其他所有Azure知识点，请查看：https://github.com/chance2021/devopsdaydayup/blob/main/cloud/azure/README.md