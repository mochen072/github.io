# Linux基础

## Kali更新源
       #中科大
      deb http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib
      deb-src http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib

      #阿里云
      deb http://mirrors.aliyun.com/kali kali-rolling main non-free contrib
      deb-src http://mirrors.aliyun.com/kali kali-rolling main non-free contrib

      #清华大学
      deb http://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free
      deb-src https://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free

      #浙大
      deb http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free
      deb-src http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free

      #东软大学
      deb http://mirrors.neusoft.edu.cn/kali kali-rolling/main non-free contrib
      deb-src http://mirrors.neusoft.edu.cn/kali kali-rolling/main non-free contrib




## CentOS基本命令

   * linux操作系统中一切皆文件,<mark>（文件名） sd(硬盘类型)<nbsp>    a(第一块)
   * <mark>linux操作系统树状结构，目录==文件夹 <mark>


         fdisk -l	   # 硬盘大小
         /dev/sda	   # 操作系统中第一块硬盘名称及所在路径   
         cat/proc/meminfo	   # 内存大小
         cat/proc/cpuinfo	   # cpu型号
         reboot	   # 重启
         poweroff	   # 关机
         /root	      # 管理员的加目录
         /media	#光驱的挂载目录
         /mnt	   # 临时设备的挂载目录
         /proc	   #里面的数据都在内存中，进程所在目录
         /tmp	   #临时文件存放目录
         /usr	   #软件的安装目录
         cd..	返回上一级目录
         pwd	列出当前所在目录路径
         ls	列出当前目录内容
         /	操作系统的起始路径和根路径
         /bin	普通用户和管理员都可以执行的命令
         /sbin	只有管理员才能执行的命令
         /boot	主引导目录 独立的分区，启动菜单。。
         /dev	device设备 设备文件存放目录
         /etc	配置文件存放的目录
         /home	普通用户的家目录
         /var	常变文件存放目录 日志文件，右键文件

   * 快捷功能

         ctrl+l	清屏
         ctrl+c	终止

