## <font color = #1E90FF>渗透测试一般流程</font>

**拿到一个网站我们最直观的感受就是他的域名给我们反馈的东西，其次才是IP等其他东西，所以域名是做信息的第一步，也是最主要的一步，IP都有可能没啥用，但是域名是不会作假的**

### <font color = #FF0000>1.信息收集</font>
1. **域名信息whois**
>社工、弱口令
2. **IP、端口**
> nmap、msf
3. **找后台**
>弱口令
4.**子域名**
>旁站
5. **Web服务器指纹**
>寻找相应漏洞
6. **信息泄露**
> phpinfo、物理路径


### <font color = #FF0000>2.漏洞挖掘</font>

#### <font color = #FF0000>Web应用层</font>
- **编辑器**
- **文件包含**
- **文件上传**
- **文件下载**
- **SQL注入**
- **XSS**
- **CSRF**
- **越权**
- **弱口令**
- **逻辑漏洞**

#### <font color = #FF0000>服务器</font>
- **弱口令**
- **Shift后门**
- **msf**

### <font color = #FF0000>3.权限提升</font>
### <font color = #FF0000>4.权限维持</font>
- **隐蔽**
- **周期查看**
- **免杀最好**
- **多种后门维持权限**

### <font color = #FF0000>5. 日志清扫</font>
- **严谨**
- **伪装隐藏**
- **避免机警(删除了全部日志)**


## <font color = #1E90FF>信息收集</font>
### <font color = #FF0000>主动信息收集</font>
**主动信息搜集是与目标主机进行直接交互，从而拿到我们的目标信息**
### <font color = #FF0000>被动信息收集</font>
**不与目标主机进行直接交互，通过搜索引擎或者社交等方式间接的获取目标主机的信息。**

## <font color = #1E90FF>常用的几种方法</font>
### <font color = #FF0000>whois</font>
```
https://whois.chinaz.com/
```

### <font color = #FF0000>谷歌语法</font>
### <font color = #FF0000>子域名挖掘机Layer</font>
### <font color = #FF0000>在线子域名挖掘</font>

## <font color = #1E90FF>目标IP</font>
### <font color = #FF0000>没加CDN的网站</font>
```
ping 域名即可
```

### <font color = #FF0000>加了CDN:</font>

- **二级域名法**
- **域名历史解析**
```
https://x.threatbook.cn/
```

## <font color = #1E90FF>旁站C段</font>
**旁站是和目标网站在同一台服务器上的其它的网站;如果从目标站本身找不到好的入手点，这时候,如果想快速拿下自标的话，一般都会 先找个目标站点所在服务器上其他的比较好搞的站下手，然后再想办法跨到真正目标的站点目录中。<BR>C段是和目标机器ip处在同一个C段的其它机器;通过目标所在C段的其他任一台机器， 想办法跨到我们的目标机器上。**

```
http://webscan.cc/
```

- **Nmap**


## <font color = #1E90FF>CMS类型</font>
### <font color = #FF0000>识别方式: </font>
- **网站特有文件/templets/defaultstyle/dedecms.css --- dedecms**
- **网站独有文件的md5**
- **网站命名规则**
- **返回头的关键字**

### <font color = #FF0000>工具:</font>
- **网页关键字**
- **云悉:**
    ```
     http://yunsee.cn
    ```
- **Whatweb:**
    ```
      http://whatweb.bugscaner.com/look/
    ```
- **URL特征**
- **Script特征**
- **robots.txt**
- **网站路径特征**
- **网站静态资源**
- **爬取网站目录信息**

## <font color = #1E90FF>敏感文件</font>
- **.git .SVn .DB store源代码泄露**
- **扫描**
- **御剑**
- **dirbrute**

## <font color = #1E90FF>端口信息</font>
 - **Nmap**
 - **masscan**

## <font color = #1E90FF>服务器和中间件</font>
### <font color = #FF0000>Web容器:</font>
- **apache,nginx iis6.0>解析漏洞**

### <font color = #FF0000>服务器:</font>
 - **Windows**
- **Linux**

## <font color = #1E90FF>WAF(防火墙)</font>

## <font color = #1E90FF>后台查找</font>
### <font color = #FF0000>源代码:</font>
<B>个别网站他的图片上传到了后台目录下，在引用的时候就可能会暴露自己的后台<B>

### <font color = #FF0000>robots.txt</font>
<B>(统一小写) 是一种存放于网站根目录下的ASCII编码的文本文件，它通常告诉网络搜索引擎的漫游器(又 称网络蜘蛛)，此网站中的哪些内容是不应被搜索引擎的漫游器获取的，哪些是可以被漫游器获取的。因为一些系统中的URL是大小写敏感的，所以robots.txt的文件名应统一为小写。<BR>
robots.txt应放置于网站的根目录下。<B>

### <font color = #FF0000>BurpSuite</font>
- **Spider---爬虫模块**

- **Scanner---扫描模块**


### <font color = #FF0000>扫描器</font>
- <B>御剑<B>
- <B>awvs<B>



