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
- ACK:
        -sA
- UDP:
        -sU
- RPC:
        -sR
- ICMP:
        -sP
- Disable Port Scan:
        -sn
