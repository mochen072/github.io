## ARP攻击及原理

Kali Linux是基于Debian的Linux发行版， 设计用于数字取证操作系统.


 ### <font color =#B22222 size=1>ARP欺骗原理及复现</font>
* <font color =#FF4500 >什么ARP协议</font><br>

    即地址解析协议，是根据IP地址解析物理地址的一个TCP/IP协议。主机将包含目标IP地址信息的ARP请求广播到网络中的所有主机，并接收返回消息，以此确定目标IP地址的物理地址；收到返回消息后将该IP地址和物理地址存入本机ARP缓存中并保留一定时间，以便下次请求时直接查询ARP缓存以节约资源.<br>
    <font color =#FF0000>(工作在数据链路层)</font>
*   <font color =#FF4500 size=9px>ARP欺骗</font><br>

    是针对以太网地址解析协议（ARP）的一种攻击技术，通过欺骗局域网内访问者PC的网关MAC地址，使访问者PC错以为攻击者更改后的MAC地址是网关的MAC，导致网络不通。此种攻击可让攻击者获取局域网上的数据包甚至可篡改数据包，且可让网络上特定计算机或所有计算机无法正常连线。<br>
    
   <center> arp攻击原理</center>
<figure class="thumbnails">
    <img src="assets/img/通信方式1.png" alt="Screenshot of coverpage" title="Cover page">
    
</figure>

### <font color =#B22222 size=1>ARP欺骗复现</font>

#### 实验环境：
  
  - Kali LInux
  - window7
  - 局域网内
  - arpspoof(kali自带)
```IP
win7      192.168.2.207
kali      192.168.2.244
注：目标主机（win7）ping一下百度确定能够上网
```
  * 1.安装dnsiff
```dnsiff是一个著名的网络嗅探工具包，高级口令嗅探工具，综合性网络嗅探工具包
 apt-get install dnsiff      #root用户环境下
```  
  * 2.使用arpspoof
```命令
 arpspoof -i eth0 -t 192.168.1.112 192.168.1.1     
-i 网卡
-t 目标主机Ip  目标主机网管
```
#### <center> Kali</center>  
<figure class="thumbnails">
    <img src="assets/img/Kali.png" alt="Screenshot of coverpage" title="Cover page">
</figure>

#### <center> 目标主机</center>  
<figure class="thumbnails">
    <img src="assets/img/目标主机.png" alt="Screenshot of coverpage" title="Cover page">
</figure>



### Arp防御

  - 1. ARP 高速缓存超时设置
  

  在ARP高速缓存中的表项一般都要设置超时值，缩短这个这个超时值能够有用的避免ARP表的溢出。

  - 2. IP+MAC访问操控   -----推荐使用

        单纯依托IP或MAC来树立信赖联系是不安全，抱负的安全联系树立在IP+MAC的根底上，这也是咱们校园网上网有必要绑定IP和MAC的因素之一。

  - 3. 静态ARP缓存表

      每台主机都有一个暂时寄存IP-MAC的对应表ARP攻击就经过更改这个缓存来到达诈骗的意图，运用静态的ARP来绑定正确的MAC是一个有用的办法，在命令行下运用arp -a能够检查当时的ARP缓存表。

  - 4. 自动查询

      在某个正常的时间，做一个IP和MAC对应的数据库，以后定时检查当时的IP和MAC对应联系是否正常，定时检查交流机的流量列表，检查丢包率。

      ARP本省不能形成多大的损害，一旦被联系使用，其风险性就不可估量，因为ARP自身的疑问，使得防备ARP的攻击很棘手，经常检查当时的网络状况，监控流量对一个站长来说是个很好的风气
    
## ss asa as 