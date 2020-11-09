# 皮卡丘靶场
    


[![NPM](https://img.shields.io/npm/v/docsify-themeable.svg?style=flat-square)](https://www.npmjs.com/package/docsify-themeable)
[![Codacy grade](https://img.shields.io/codacy/grade/860d40719cbd4e0f91e145b87ec7c29a.svg?style=flat-square)](https://www.codacy.com/app/jhildenbiddle/docsify-themeable?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=jhildenbiddle/docsify-themeable&amp;utm_campaign=Badge_Grade)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://github.com/jhildenbiddle/docsify-themeable/blob/master/LICENSE)
[![jsDelivr](https://data.jsdelivr.com/v1/package/npm/docsify-themeable/badge)](https://www.jsdelivr.com/package/npm/docsify-themeable)
[![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?url=https%3A%2F%2Fgithub.com%2Fjhildenbiddle%2Fdocsify-themeable&hashtags=css,docsify,developers,frontend)
<a class="github-button" href="https://github.com/jhildenbiddle/docsify-themeable" data-icon="octicon-star" data-show-count="true" aria-label="Star jhildenbiddle/docsify-themeable on GitHub">Star</a>

## <font color = #1E90FF>暴力破解（基于表单）</font>
### **<font color=#FF0000>什么是暴力破解？？</font>**
**连续性尝试+字典+自动化**

### **<font color=#FF0000>暴力破解概述</font>**
- **是否要求用户设置了复杂的密码;**
- **是否每次认证都使用安全的验证码;**
- **是否对尝试登录的行为进行判断和限制;**
- **是否在必要的情况下采用了双因素认证;**

### **<font color=#FF0000>暴力破解漏洞测试流程</font>**
- **确认登录接口的脆弱性**
    - 确认目标是否存在暴力破解的漏洞。( 确认被暴力破解的"可能性”)
比如:尝试登录一抓包-- 观察 验证元素和response信息 ,判断否存在被暴力破解的可能。
- **对字典进行优化**
    - 根据实际的情况对字典进行优化,提高爆破过程的效率。
- **工具自动化操作**
    - 配置自动化工具(比如线程、超时时间、重试次数等)， 进行自动化操作。

### **<font color=#FF0000>暴力破解实验演示</font>**

#### 环境：
- burpsuite
- pkq

#### 目标：
- 基于表单的暴力破解

### **<font color=#FF0000>BurpSuite</font>**

<figure class="thumbnails">
    <img src="picture/bp/1.png"   >
</figure>

- **target选项卡**
        设置攻击目标，可以通过proxy发送
- **Pasitions选项卡**
        指定需要暴力破解的参数，并设置成变量，同时选择攻击模式
    - Sniper: 狙击手
            设置一个payload,先将第一个变量使用字典进行测试，然后再将第二个变量使用字典进行测试。
    - Battering ram: 冲撞车
            设置一个payload,所有的变量一起用字典内容被替换，然后一起尝试。
    - Ptichfork:草叉性
            每个变量设置一个payload，分别使用对应的字典对变量进行同时替换。
    - Cluster bomb:焦束炸弹
            需要为每个变量是在一个payload，分别使用字典内容祝贺对变量进行替换