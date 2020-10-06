# 网络协议

[![NPM](https://img.shields.io/npm/v/docsify-themeable.svg?style=flat-square)](https://www.npmjs.com/package/docsify-themeable)
[![Codacy grade](https://img.shields.io/codacy/grade/860d40719cbd4e0f91e145b87ec7c29a.svg?style=flat-square)](https://www.codacy.com/app/jhildenbiddle/docsify-themeable?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=jhildenbiddle/docsify-themeable&amp;utm_campaign=Badge_Grade)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://github.com/jhildenbiddle/docsify-themeable/blob/master/LICENSE)
[![jsDelivr](https://data.jsdelivr.com/v1/package/npm/docsify-themeable/badge)](https://www.jsdelivr.com/package/npm/docsify-themeable)
[![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?url=https%3A%2F%2Fgithub.com%2Fjhildenbiddle%2Fdocsify-themeable&hashtags=css,docsify,developers,frontend)
<a class="github-button" href="https://github.com/jhildenbiddle/docsify-themeable" data-icon="octicon-star" data-show-count="true" aria-label="Star jhildenbiddle/docsify-themeable on GitHub">Star</a>

## <font color = #1E90FF>JS简介 </font>

- js的运行环境是浏览器
- 解释型语言
- 每次刷新页面，JS代码都会执行
- 从上到下依次执行
- 当直接访问JS脚本时候，返回存文本内容
- JS与HTML混编
- 任何位置

## <font color = #1E90FF>语法 </font> 
- **<font color = #FF0000>输出语句</font>**
```javascript
alert();	    //弹窗
console.log();	//在控制台输出
```

- **<font color = #FF0000>在HTML中引用JS代码</font>**
```javascript
<script></script>	    //内部JS
type="text/javascript"	//外部js
```

## <font color = #1E90FF>变量 </font> 
- **<font color = #FF0000>声明变量</font>**
```javascript
var a = 123;
a = 'abc';
int a = 1223; 
```

- **<font color = #FF0000>变量类型</font>**
    * 字符串
    * Number  1+1
    * 布尔类型变量
    *null和undefined
__<table><tr><td bgcolor=PowderBlue>null表示一个“空”的值，它和0以及空字符串' '不同，0是一个数值,表示长度为0的字符串，而null表“空"。</td></tr></table>__

## <font color = #1E90FF>数组 </font> 
**数组是一组按照顺序排列的集合，集合内每个值称为元素，<mark>Javascript的数组可以包含任意的数据类型<mark><BR>如：**
```javascript
[1,2,3,"helo",null,true];
```

- **<font color = #FF0000>数组的创建：</font>**
    * 另一种创建数据的方法是通过Array()函数实现：
```javascript	
new Array(1,2,3);
```

- **<font color = #FF0000>数组元素的访问</font>**
    * 数组元素可以通过索引访问。<mark>索引的起始值为0<mark>
```javascript
var arr =[1,2,3,"helo",null,true];
console.log(arr[0]);   //返回索引为0的
```

## <font color = #1E90FF>对象</font> 
**Javascript的对象是由一组键-值组成的无序集合<BR>如:**
```javascript
var person = {
	name: 'Tom',
	age: 20,
	tags: ['js','web'],
	hasCar: true,
};
```

## <font color = #1E90FF>While</font> 
- **基本语法**
    * while循环只有一个判断条件，条件满足，就不断循环，条件不满足时候则退出循环<BR>**例:计算100以内所有奇数和**
```javascript
	var x = 0;
	var n = 99;
	while (n>0){
		x = x + n;
		n = n-2;
	}
    x;
```
__<table><tr><td bgcolor=PowderBlue>在循环内部变量n 不断自减，直到变成-1时，循环退出</td></tr></table>__

## <font color = #1E90FF>浏览器对象</font> 

- **<font color = #FF0000>window</font>**
    * window对象不但充当全局作用域，而且表示浏览器窗口。
    * window对象有innerWidth和innerHeight属性，可以获取浏览器窗口的内部宽度和高度，内部宽高指去掉菜单栏，工具栏等占位元素后的宽高
    * 兼容性： IE<=8不支持
- **<font color = #FF0000>navigator</font><BR>navigator对象表示浏览器的信息，最常用的属性包括**
```javascript
 navigator.appName      //浏览器名称
navigator.appVersion    //浏览器版本
navigator. language     //浏览器设置的语言
```
   
- **<font color = #FF0000>screen</font><BR>screen对象表示屏幕的信息，常用的属性有：**
```javascript
screen.width:           //屏幕宽度，以像素为单位；
screen.height:          //屏幕高度，以像素为单位；
screen.colorDepth:      //返回颜色位数，如8,16,24；
```
- **<font color = #FF0000>浏览器操作DOM</font><BR>常用的方法有：**
```javascript
document.getElementById()
document.getElementByTagName()
document.getElementByClassName()
```

- **<font color = #FF0000>浏览器内置对象</font>**
```javascript
window                  //全局  代表浏览器
navigator
location
document                //非常重要
document.cookie();      //可以完成Cookie信息的读写
alert(document.cookie());
```
## <font color = #1E90FF>事件</font> 
 - **<font color = #FF0000>用户触发事件</font>**
    - 鼠标事件
```javascript
onclick
```
	
	- 键盘事件
    - form事件
 - **<font color = #FF0000>事件响应</font>**


