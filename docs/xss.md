# XSS漏洞
## <font color = #1E90FF>XSS漏洞的定义</font>
__XSS又叫CSS（Cross Site Script）,跨站脚本攻击，它指的是恶意攻击者往Web页面里插入恶意JS代码，当用户浏览该页之时，嵌入其中的Web里面的JS代码会被执行，从而达到恶意的目的__

### <font color = #FF0000>XSS漏洞的分类</font>
- **反射型**
- **存储性**
- **DOM型**

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
__攻击者在url中插入XSS代码，服务端将URL中的XSS代码输出到页面上，攻击者将带有XSS大妈的URL发送给用户，用户打卡后受到XSS攻击__
### <font color = #FF0000>WordPress Brafton 3.3.10</font>
## <font color = #1E90FF>DOM型XSS</font>
### <font color = #FF0000>原理</font>
__攻击者在url中插入XSS代码，前端页面直接从URL中获取XSS代码并且输出到页面，导致XSS代码的执行，攻击者将带有XSS代码的URL发送给用户，用户打开后收到xss攻击__

## <font color = #1E90FF>XSS辅助测试工具</font>
### <font color = #FF0000>Beef</font>
### <font color = #FF0000>XSS'OR</font>
```
https://xssor.io

```

## <font color = #1E90FF>Electron跨平台XSS</font>
