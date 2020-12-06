# SQL注入


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