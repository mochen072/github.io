# 主机发现
## <font color = #1E90FF>Nmap</font>
### <font color=#FF0000>安装</font>
- Mac os
```
brew install nmap
```

- CentOS
```
yum install nmap
```

- Ubuntu
```
apt-get intall nmap
```

### <font color=#FF0000>扫描方式</font>
- TCP:
        -sT
        __将与目标端口进行三次握手，尝试建立连接，如果连接成功，则端口开放，这种扫描很容易被检测到，在目标主机的日志中会记录大批的连接请求以及错误信息__
        - SYN:
                -sS
        __半开放扫描（非3次握手的tcp扫描），执行得很快，效率高，Nmap发送SYN包到远程主机，但是它不会产生任何会话，目标主机几乎不会把连接记入系统日志。（防止对方判断为扫描攻击），扫描速度快，效率高，在工作中使用频率最高__
- **ACK:**
        -sA
- **UDP:**
        -sU
- **RPC:**
        -sR
- **ICMP:**
        -sP
- **Disable Port Scan:**
        -sn

### <font color=#FF0000>常见的扫描方案</font>
 - **扫描100000端口，操作系统，版本**
        nmap -T4 -A <target>

- **版本探测**
        nmap -sV <target>

- **操作系统**
        nmap -O <target>

### <font color=#FF0000>其他一些技巧</font>
- **-host-timeout主机超时时间通常选值: 18000**
- **-scan-delay报文时间间隔通常选值: 1000**
- **-S<源地址> 定义扫描源地址，为了不被发现**

### <font color=#FF0000>示例</font>
- **随机选择10000台主机扫描是否运行Web服务器(80端口)**
```
nmap -v -iR 10000 -P0 -p 80
```

- **进行DNS区域传输，以发现compant.com中的主机，然后将IP地址提供给nmap**

```
host -l comany.com | cut -d -f 4 | nmap -v -iL
```

## <font color = #1E90FF>masscan</font>
### <font color=#FF0000>项目地址</font> 
```
https://github.com/robertdavidgraham/masscan
```
### <font color=#FF0000>安装</font>
```
sudo apt-get install git gcc make libpcap-dev
git clone https://github.com/robertdavidgraham/masscan
cd masscan
make
```
<table><tr><td bgcolor=PowderBlue>该工具兼容Nmap参数</td></tr></table>

### <font color=#FF0000>高级选项</font>
- **指定发包的Ip地址**
        --adapter-ip
- **指定发包的源端口**
        --adapter-port
- **指定发包的mac地址**
        --adapter-mac
- **指定网关的mac地址**
        --router-mac
- **IP地址范围黑名单，防止masscan扫描**
        --exclude
- **指定IP地址范围黑名单文件**
        --excludefile
- **读取一个范围列表进行扫描**
        --excludefile，-iL
- **指定发送完包之后的等待时间，默认为10秒**