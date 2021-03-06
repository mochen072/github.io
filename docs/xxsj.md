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

### <font color = #FF0000>1.dirsearch:</font>
```
python3 dirsearch.py -u 目标网址 -e *     #需要python3环境
```

### <font color = #FF0000>2.Githack脚本:（拖取git泄露的源码）</font>
```
python GitHack.py 目标网址/git/   #需要python2环境
```

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
### <font color = #FF0000>常用的寻找方式:</font>
- <B>1.通过robots. .txt文件寻找</B>
- <B>2.通过谷歌语法寻找</B>
- <B>3.查看网站底部管理入口4.请求一些不存在的错误路径</B>
- <B>5.在线网站指纹识别</B>
- <B>6.猜解常见后台路径</B>
- <B>7.字典爆破后台路径</B>
- <B>8.目标子域名寻找</B>
- <B>9.通过xss插后台</B>

### <font color = #FF0000>源代码:</font>
<B>个别网站他的图片上传到了后台目录下，在引用的时候就可能会暴露自己的后台</B>

### <font color = #FF0000>robots.txt</font>
<B>(统一小写) 是一种存放于网站根目录下的ASCII编码的文本文件，它通常告诉网络搜索引擎的漫游器(又 称网络蜘蛛)，此网站中的哪些内容是不应被搜索引擎的漫游器获取的，哪些是可以被漫游器获取的。因为一些系统中的URL是大小写敏感的，所以robots.txt的文件名应统一为小写。<BR>
robots.txt应放置于网站的根目录下。</B>

### <font color = #FF0000>BurpSuite</font>
- **Spider---爬虫模块**

- **Scanner---扫描模块**


### <font color = #FF0000>扫描器</font>
- <B>御剑</B>
- <B>awvs</B>


## <font color = #1E90FF>谷歌语法</font>

## <font color = #1E90FF>JS文件爬取</font>
### <font color = #FF0000>JSFinder.py</font>
- **简单爬取**
```
python3 JSFinder.py -u https://example.com
```

- **深度爬取**

  ```
  python3 JSFinder.py -u https://example.com  -d -ou xx_url.txt -os_domain.txt
  - d    # 进项税深度爬取
  -ou     # 指定url保存的文件名
  -os     # 指定子域名所保存的文件名
  ```

  ## <font color = #1E90FF>CDN</font>
  <B>CDN,即内容分发网络，主要解决因传输距离和不同运营商节点造成的网络速"度性能低下的问题。说得简单点，就是一组在不同
  运营商之 间的对接节点上的高速缓存服务器，把用户经常访问的静态数据资源(例如CSS,HTML)直接缓存在CDN服务器上，当用户再
  次请求时，会直接分发到在离用户近的节点服务器上响应给用户，当用户有实际数据交互时，才会从远程web服务器上响应。</B>
  