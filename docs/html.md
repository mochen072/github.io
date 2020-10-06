# HTML

[![NPM](https://img.shields.io/npm/v/docsify-themeable.svg?style=flat-square)](https://www.npmjs.com/package/docsify-themeable)
[![Codacy grade](https://img.shields.io/codacy/grade/860d40719cbd4e0f91e145b87ec7c29a.svg?style=flat-square)](https://www.codacy.com/app/jhildenbiddle/docsify-themeable?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=jhildenbiddle/docsify-themeable&amp;utm_campaign=Badge_Grade)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://github.com/jhildenbiddle/docsify-themeable/blob/master/LICENSE)
[![jsDelivr](https://data.jsdelivr.com/v1/package/npm/docsify-themeable/badge)](https://www.jsdelivr.com/package/npm/docsify-themeable)
[![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?url=https%3A%2F%2Fgithub.com%2Fjhildenbiddle%2Fdocsify-themeable&hashtags=css,docsify,developers,frontend)
<a class="github-button" href="https://github.com/jhildenbiddle/docsify-themeable" data-icon="octicon-star" data-show-count="true" aria-label="Star jhildenbiddle/docsify-themeable on GitHub">Star</a>

## <font color = #1E90FF>常用标签 </font>

### <font color = #FF0000>HTML文档结构</font>
- __头部__	
    * 文档控制信息，包括整个页面的说明和编码等等
- __身体__	
    * 真正显示文档内容的部分

```html
<html>
	<head>  #头
		<body>  #身体
		</body>
	</head>
</html>

```
- __常用标签__

```html 
<title></title>	    #浏览器标签页标题
<meta charset="tuf-8">	# 编码utf-8
<h1></h1>	    #标题
<p><p>	    #段落
<hr />	    #水平线
<br />	    #换行
<span>	    #文字拼接（控制）
<div></div>	    #块级元素
<a></a>	    #超链接
href	    #跳转的地址

```

```html
target      #默认不用写（在当前页打开 ）
_blank      #在新标签页打开

```

## <font color = #1E90FF>元素</font>
- __表单元素__

```html
<input /> 	#单标签
type	    #属性
password	#密码框
text	    #文本框
radio	    #单选框
checkbox	#复选框
reset	    #重置按钮
file	    #文件域
```


- __下拉列表__

```html
<select name = "mon">
	<options></options>
</select>
selected="selected"	默认
```

- __文本域__

```html
<textarea></textarea>
```

## <font color = #1E90FF>form表单</font>
__form表单本身是一个框架__
```html
<form></form>
    action	//数据提交到服务器的url中
    methon	//提交方法

        get	
            url中有显示
            url中长度有限
        post	
            上传文件等
            HTTP请求正文

    enctype
    application/x-www-form-urlencoded	//默认值
    multipart/form-data	    //上传文件

```

## <font color = #1E90FF>ifare框架</font>
```html

<iframe 
		name="myifre" 
		width="100%" 
		height="400px" 
		frameborder="10"
>
			
</iframe>

```
- __常用属性__

| 属性 | 作用 | 举例 |含义 |
| :-----| :-----: | :--------: |------: |
| src | 在ifare中显示的文档的URL | src="http://www.baidu.com" | 引用url为http://www.baidu.com |
| height | ifare高度 | height="256" |ifare高度为256 |
| width | ifare宽度 | width="400" |ifare宽度为400 |
| frameborder | 是否显示框架周围的边框 | frameborder="1"<BR>frameborder="0 |显示边框<BR>为0不显示 |
| name | 框架标识名 | name="mainFrame" |框架标识名 |
| scrolling | 是否显示滚动条 | scrolling = "no"<BR>scrolling = "yes"<BR>scrolling = "auto" |不显示滚动条<BR>显示滚动条<BR>根据内容确定是否显示|
