# CSS

[![NPM](https://img.shields.io/npm/v/docsify-themeable.svg?style=flat-square)](https://www.npmjs.com/package/docsify-themeable)
[![Codacy grade](https://img.shields.io/codacy/grade/860d40719cbd4e0f91e145b87ec7c29a.svg?style=flat-square)](https://www.codacy.com/app/jhildenbiddle/docsify-themeable?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=jhildenbiddle/docsify-themeable&amp;utm_campaign=Badge_Grade)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://github.com/jhildenbiddle/docsify-themeable/blob/master/LICENSE)
[![jsDelivr](https://data.jsdelivr.com/v1/package/npm/docsify-themeable/badge)](https://www.jsdelivr.com/package/npm/docsify-themeable)
[![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?url=https%3A%2F%2Fgithub.com%2Fjhildenbiddle%2Fdocsify-themeable&hashtags=css,docsify,developers,frontend)
<a class="github-button" href="https://github.com/jhildenbiddle/docsify-themeable" data-icon="octicon-star" data-show-count="true" aria-label="Star jhildenbiddle/docsify-themeable on GitHub">Star</a>

## <font color = #1E90FF>样式</font>

- __层叠样式脚本__
    * HTML  CSS  都是前端的内容
    * 提倡HTML CSS分离

- __CSS样式__
    
```css
color	            #元素内容的颜色
background-color	#元素内容的背景色
font-size	        #字体大小

```
### __CSS与HTML组合有三种：__

- **1.内联样式**
    * 把样式表写在标签内部，标签中的style属性的属性值出现
    ```css
    <span style="color:#ffffff;background-color:red;font-size:30px;">道可道，非常道</span>

    ```

- **2.内部样式** 
    ```css
	<style type="text/css">
		span{
			color: red;·
			background: yellow;
		}
		.id{
			color: red;
		}
		#a{
			color: black;
		}
    </style>
    ```
- **3.外部样式**
    * 单独作为一个文件

