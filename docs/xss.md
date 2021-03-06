# XSS跨站脚本攻击
## <font color = #1E90FF>XSS漏洞的定义</font>
__XSS又叫CSS（Cross Site Script）,跨站脚本攻击，它指的是恶意攻击者往Web页面里插入恶意JS代码，当用户浏览该页之时，嵌入其中的Web里面的JS代码会被执行，从而达到恶意的目的__

### <font color = #FF0000>XSS漏洞的分类</font>
- **反射型**
- **存储性**
- **DOM型**

## <font color = #1E90FF>Cookie</font>
- <b>一般 软件的存放地址:</b>
        C:UserslY4erAppDatalRoaming

- <b>IE浏览器Cookie数据位于:</b>
        %APPDATA%\MicrosoftlWindows\Cookies\目录中的xxx.txt文件( 里面可能有很多个.txt Cookie文件)

- <b>Firefox的Cookie数据位于:</b>
        %APPDATA%\Mozillal\Firefox\Profiles\目录中的xx.default目录，名为cookies.sqlite的文件。

- <b>Chrome的Cookie数据位于:</b> 
        %LOCALAPPDATA%\Google\ChromelUser Data\Default\目录中，名为Cookies的文件。

## <font color = #1E90FF>Session</font>
### <font color = #FF0000>两者区别</font>
- <b>Cookie存在客户端session存在服务端</b>
- <b>Cookie不是很安全，攻击者可以分析你的cookie进行<font color = #FF0000>cookie欺骗</font></b>
- <b>Cookie单个保存的数据不能超过4k</b>
- <b>Session存在服务端所以会在一点程度上占用服务器性能</b>



### <font color = #FF0000>XSS漏洞的修复方法</font>
- **HTML实体编码**
- **使用白名单过滤掉用户输入的恶意字符**
- **根据业务场景对症下药**

## <font color = #1E90FF>存储型XSS</font>
### <font color = #FF0000>原理</font>
__攻击者在页面上插入XSS代码，服务端将数据存入数据库，当用户访问到存在XSS漏洞的页面时，服务端从数据库中取出数据展示到页面上，导致XSS代码被执行，达到攻击效果__

## <font color = #1E90FF>DedeCMS_v5.7存储型XSS</font>
### <font color = #FF0000>POC</font>
**该漏洞 通过用户在编写订单收货地址的相关参数 注入 XSS Payload，导致 前台查看订单的页面和后台管理员查看订单详情的页面都会被 XSS，所以说，可以用来打管理员 Cookie 。**

### <font color = #FF0000>测试：</font>

- **首先管理员添加一项商城的商品**
- **前台用户选定商品添加购物车**
- **前台用户编辑订单的收货地址，在这里 address,des,email,postname 都是存在 XSS 的，插入 XSS Payload**
- **查看订单详情发现前台已经被 XSS**
- **管理员进入后台查看商城订单同样也会被 XSS**

## <font color = #1E90FF>反射型XSS</font>
### <font color = #FF0000>原理</font>
__攻击者在url中插入XSS代码，服务端将URL中的XSS代码输出到页面上，攻击者将带有XSS大马的URL发送给用户，用户打卡后受到XSS攻击<BR><font color = #FF0000>特点：</font><BR>只在用户单击时触发，而且只执行一次，非持久化，所以称为反射型跨站式脚本。<BR><font color = #FF0000>通常出现在网站的搜索栏、用户登入口等地方，常用来窃取客户端 Cookies 或进行钓鱼欺骗</font>__


### <font color = #FF0000>WordPress Brafton 3.3.10</font>


## <font color = #1E90FF>DOM型XSS</font>
### <font color = #FF0000>原理</font>
__攻击者在url中插入XSS代码，前端页面直接从URL中获取XSS代码并且输出到页面，导致XSS代码的执行，攻击者将带有XSS代码的URL发送给用户，用户打开后收到xss攻击__


## <font color = #1E90FF>CSRF</font>
<B>跨站请求伪造(英语: Cross-site request forgery),也被称为one-click attack或者session riding，通常缩写为CSRF或
者XSRF。CSRF是一种挟制用户在当前已登录的Web应用程序上执行非本意的操作的攻击方法。跟跨站脚本(XSS)相比，Xss利用的是
用户对指定网站的信任，CSRF利用的是网站对用户网页浏览器的信任。</B>

## <font color = #1E90FF>XSS辅助测试工具</font>
### <font color = #FF0000>Beef</font>
### <font color = #FF0000>XSS'OR</font>
```
https://xssor.io

```

## <font color = #1E90FF>Electron跨平台XSS</font>
