# BurpSuite
**BurpSuite是一个集成化的渗透测试工具，集合了多种渗透测试逐渐，使我们自动化的或手工的能更好的完成对于web应用的渗透测试和攻击<BR>推荐配合插件SwtchyOmega使用**
## <font color = #1E90FF>Proxy代理模块</font>
__代理模块是burp的核心模块，主要用来接货并修改浏览器，手机app等客户端的HTTP/HTTPS数据包<BR>__
### <font color = #FF0000>设置代理端口</font><BR>
- __1.依次选择 Proxy--->Options--->Proxy Listeners--->Add增加代理__
- __2.在浏览器中添加代理(以火狐为例)__
</figure>
     <figure class="thumbnails">
        <img src="picture/bp/bp1.png">
        <img src="picture/bp/bp2.png">
</figure>

- __3.接下来在 Proxy-->Intercept选项卡下设置 Intercept is on,这样就能截获浏览器的数据包并进行修改等操作了<BR> Intercept is off 则不会拦截数据包，而是会在 HTTP history记录下来__
</figure>
     <figure class="thumbnails">
        <img src="picture/bp/bp3.png">
        <img src="picture/bp/bp4.png">
</figure>