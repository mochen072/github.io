# 网络基础

[![NPM](https://img.shields.io/npm/v/docsify-themeable.svg?style=flat-square)](https://www.npmjs.com/package/docsify-themeable)
[![Codacy grade](https://img.shields.io/codacy/grade/860d40719cbd4e0f91e145b87ec7c29a.svg?style=flat-square)](https://www.codacy.com/app/jhildenbiddle/docsify-themeable?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=jhildenbiddle/docsify-themeable&amp;utm_campaign=Badge_Grade)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://github.com/jhildenbiddle/docsify-themeable/blob/master/LICENSE)
[![jsDelivr](https://data.jsdelivr.com/v1/package/npm/docsify-themeable/badge)](https://www.jsdelivr.com/package/npm/docsify-themeable)
[![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?url=https%3A%2F%2Fgithub.com%2Fjhildenbiddle%2Fdocsify-themeable&hashtags=css,docsify,developers,frontend)
<a class="github-button" href="https://github.com/jhildenbiddle/docsify-themeable" data-icon="octicon-star" data-show-count="true" aria-label="Star jhildenbiddle/docsify-themeable on GitHub">Star</a>

## VM与系统命令

- **虚拟机运行架构** <br>
      1. 寄居架构 
      2. 原生架构 
  


## IP地址详解（初级）

  - **单局域网的构成：** <br>
  
      - <P>交换机，网线，其他终端 <P> 

  - **交换机：** <br>
      - <P>用来组建内网的局域网的设备 <P> 

### IP
    Ip地址范围:	  0-255

### 子网掩码：	
**局域网通信规则:** <br>
  
<font color = #FF0000>在同一局域网中，所有的IP必须在同一网段中才可以互相通信</font>
- IP地址构成：<font color = #FF0000>网络位+主机位（网络位相同的IP地址 ，为同一网段）</font>
- 子网掩码：<font color = #FF0000>用来确定IP地址的网络位</font>
- 如何确认网络位：<font color = #FF0000>与255对应的数字为网络位，与0对应的数字为主机位</font>
	    例如：	
            255.0.0.0
		    255.255.0.0
		    255.255.255.0


<!-- GitHub Buttons -->
<script async defer src="https://buttons.github.io/buttons.js"></script>

### Ip地址5大类

```
A   1-126       默认子网掩码：255.0.0.0
B   128-191     默认子网掩码：255.255.0.0
C   192-223     默认子网掩码：255.255.255.0
D   224-269     组播地址
E   240-254     科研地址

``` 
<table><tr><td bgcolor=PowderBlue>注：127.0.0.1指的是本机</td></tr></table>

__<font color = #FF0000>案例1：</font><BR>10.1.1.1<BR>255.255.0.0<BR>属于哪个网段？所在广播地址？ 可用范围？__
```
答：	网段：	    10.1.0.0
	    广播地址：	10.1.255.255
	    可用范围：	10.1.255.254
```

- 网关：一个网络的出口，GW（Gateway）,一般网关都在路由器上

- 路由器：可用连接外网的设备

### PC向外发包：
1. 首先判断目标IP地址是否与自己在同一网段
2. 如在同一网段，则直接发送出去，而不找网关
3. 如不在同一网段，则直接发包给网关

## 网络测试命令
- __1. 查看IP地址__

```
1. win+R            #打开运行窗口
2. ipconfig         #查看IP信息
3. ipconfig /all    #查看IP详细信息    
```

- __2. 测试网络连通性__

```
1. ping 目标Ip地址              #ping
2. ping -t 目标Ip地址           #一直ping
3. ping -n 数字 目标Ip地址      #修改ping包的数量  
4. ping -l 数字 目标Ip地址      #修改ping包的大小

```
<table><tr><td bgcolor=PowderBlue>注：如ping不同，可能对方不在线或者对方开了防火墙</td></tr></table>

- __3. 手工解析域名__
```
Nslookup  www.jd.com    #手工解析域名IP地址
```
## 进制转换

- __1. 数制类型__

```
1.1           二进制
                0
                1
                10      =   2
                11      =   3
                100     =   4
                101     =   5
```
<table><tr><td bgcolor=PowderBlue>二级制特点：2种符号（0-1）逢二进一
</td></tr></table>

- __2. 二转十__

```
二：	1	0	1	1	0	1
位权：	32	16	8	4	2	1
```

<table><tr><td bgcolor=PowderBlue>位权：个位永远为1 其余为是几进制就×几<BR>十：32+8+4+1=45
</td></tr></table>








