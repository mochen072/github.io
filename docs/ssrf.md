# SSRF

## SSRF原理和防御
</figure>
     <figure class="thumbnails">
        <img src="picture/ssrf/ssrf1.png">
</figure>

## SSRF高危触发点
- **图片加载与下载:通过URL地址加载或下载图片**
- **从远程服务器请求资源**
- **数据库内置功能( Oracle，MongoDB，MSSQL, Postgres，CouchDB )**
- **WebMail收取其它邮箱邮件**
- **文件处理、编码处理、属性信息处理( FFmpeg、ImageMagick、DOCX、 PDF、 XML处理器)**
