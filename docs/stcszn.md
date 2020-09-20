
# 《渗透测试完全初学者指南》

## 第零章 渗透测试导论

- 1.明确需求阶段
        和客户面对面沟通，确保双方对渗透项目理解一致。
            a.项目范围  (IP范围，是否可以使用导致服务器瘫痪的exploit....)
            b.测试窗口  (限定工作日，时间。。。)
            c.联系信息  (出现严重问题，联系谁。。。)
            d.支付条款  (支付方式，时间，金额。。保密协议)

- 2.信息收集阶段
        分析各种公开信息    (开源情报分析)

- 3.威胁建模阶段
        利用信息收集阶段获取的信息进行威胁建模，拟定破坏方案。

- 4.漏洞分析阶段
        探测客户系统漏洞，人工分析等

- 5.漏洞验证阶段
        人工，软件进行验证

- 6.深度攻击阶段
        内网资产收集，破解密码，内网渗透等

- 7.书面汇报阶段
        将问题整理为文档，通俗易懂,可分为`执行摘要`和`技术报告`：
        执行摘要:
            a.项目背景  (介绍测试目的，解释技术术语)
            b.整体评估  (问题总结)
            c.风险预测  (安全状况评级，高/中/低，补充相应标准)
            d.调查总结  (对已有安全措施的实际效果总结性描述)
            e.改进建议  (解决现有问题的初步建议)
            f.战略规划  (建议用于增强安全性的长短期规划)
            
        技术报告:
            a.项目简介  (项目范围，联系人信息等)
            b.信息收集  (信息收集发现的问题)
            c.漏洞评估  (漏洞分析阶段发现的所有技术细节)
            d.漏洞验证及攻击方法验证    (技术细节)
            e.深度攻击  (技术细节)
            f.风险及暴露程度分析    (对已知风险的定量分析，评估可能产生的各类损失。)
        结论


## 第一章 搭建虚拟渗透实验室
    
### 1.安装VMWare
    太傻逼，懒得记。。。
### 2.安装KALI
    版本更新快，百度更靠谱。。。
### 3.网络配置
 VM网络的三种虚拟网络模式
- 桥接  (并入物理机的本地局域网，使用独立的IP)
- NAT   (和物理机共用一个IP)
- 仅主机    (只能和物理机通信)

### 4.安装Nessus
是一款家庭版漏洞扫描程序 `免费版和收费版`,破解。。。。。哈哈哈哈
    
    官网:https://www.tenable.com/downloads/nessus

- Kali中安装步骤:
        文章在Kali栏目下

### 4.MingC编辑器
是用lINUX编译出能在windows上运行的应用程序

- Kali中安装步骤:
        ...

### 5.Hyperion
加密软件，使攻击程序规避反病毒软件的检测

- Kali中安装步骤:
        ...
  
### 6.Veil-Evasion
是一款生成载荷可执行文件的工具，用来绕过常见的防病毒解决方案

- Kali中安装步骤:
        ...
### 第一章完
## 第二章 使用kali Linux
### Linux命令行
        ls      #查看当前目录下文件
        ls -a   #查看当前目录下文件(包括隐藏文件，隐藏目录的前缀 . )
        ls -l   #查看详细详细
### Linux文件系统
<font color = #FF4500>在 Linux的概念里，所有的资源都视为文件</font>
        pwd     #查看当前目录的完整路径
        cd..    #返回上一级

        cd<目录名>      #切换目录
### 用户权限
        adduser mochen          #添加新用户mochen
        su mcohen               #切换到用户mochen

### 文件处理
        touch file              #创建文件
        mkdir                   #创建文件夹
        cp <源文件> [目标文件]   #复制文件
        mv <源文件> [目标文件]   #移动文件
        rm 文件名               #删除文件
        rm -r 文件夹名          #删除文件夹 
        echo 内容               #终端输入内容显示出来
        echo 内容 >file         #将内容保存到file文件中
        cat 文件                #查看文件内的内容
        
        >       #管道符，通过管道符添加的内容会覆盖原本的内容
        >>      #追加，不覆盖原本内容      
### 文件权限
        Linux的权限分为 读(R) 写(W) 执行(X)
        使用chmod命令可以改变访问权限
        7       #全部权限
        6       #读，写
        5       #读，执行
        4       #只读
        3       #写，执行
        2       #只写
        1       #只执行
        0       #拒绝访问
        chmod  7 file 
### 数据处理
        cat file        #查看文件内容
        grep September file     #在file文件中搜索September
### 软件包管理
        apt-get install 软件名          #安装软件

### 进程和服务
<font color = #FF4500>在命令中直接启动，停止，重启系统服务是，如：</font><BR>
```
   service apache2 start
```


### 网络管理
<font color = #FF4500>使用ifconfig查看网络信息</font><BR>

```
ifconfig
```
* ① 网路O接口名称
* ② IPV4地址
* ③ 子网掩码

</figure>
     <figure class="thumbnails">
    <img src="picture/two/22.png" alt="Screenshot of coverpage" title="Cover page">

</figure>

#### 设置静态IP地址
<font color = #FF4500>kali中在/etc/network/interfaces中</font><BR>

        kwrite /etc/network/interfaces
<font color = #FF4500>首先要在配置文件中添加网络接口eth0</font><BR>

- ① 声明了eth0采用了静态IP地址
- ② 子网掩码
- ③ 网关
- address IP地址
</figure>
     <figure class="thumbnails">
    <img src="picture/two/2.png" alt="Screenshot of coverpage" title="Cover page">

</figure>

#### 查看网络连接
        netstat -antp           #查看开放端口

</figure>
     <figure class="thumbnails">
    <img src="picture/two/3.png" alt="Screenshot of coverpage" title="Cover page">

</figure>

### Netcat——————TCP/IP连接的瑞士军刀
        查看kali栏目
### 第二章完












