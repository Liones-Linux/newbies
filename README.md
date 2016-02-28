# newbies
linux的入门

1. 学习 Linux 基本命令之前必需了解的基本内容和概念

    1). 目录结构：Linux 采用树型结构组织目录
    
            /                 根目录，一切文件都源自这里
            
            /bin            普通用户的命令文件
            
            /sbin          超级用户的命令文件
            
            /boot          Linux 的内核及 grub 等相关文件
            
            /dev           系统设备放在这里(Linux下所有设备都是文件)
            
            /etc            系统配置文件放在这里
            
            /home        用户的根目录(通常普通用户只有自己目录的写权限)
            
            /lib             Linux 的程序通用动态库文件
            
            /mnt           Linux 预留的磁盘挂载目录
            
            /proc          内在中的设备信息挂载在这里
            
            /tmp           临时文件目录
            
            /usr            应用程序目录
            
            /usr/src     对应程序源代码文件
            
            /usr/bin      对应普通用户程序编译后的文件
            
            /usr/sbin     对应超超级用户程序编译后的文件
            
            /var            存放变动信息的文件的位置，比如：日志文件、缓存文件
            
    2). 基本概念：
    
            a. Linux 是真正的多用户、多任务的操作系统
            
            b. 绝对路径从 /(根) 开始，相对路径从当前目录开始
            
            c. 调用命令帮忙信息的几种方法
            
                help 命令    或者    命令 --help    简单帮助
                
                man 命令                                    命令手册(如果有的话)
                
                info 命令                                     同 man
                
            d. 输入命令时连按两次 Tab 键，可以补全命令或操作目录、文件
            

2. Linux 基本命令的基本用法。详细用法参照：命令 --help 寻找更多信息


    1). 文件和目录管理类常用命令
    
         ls                    列出目录和文件。实列：ls /boot -lha    a表示全部，h表示友好方式，l表示详细列表
         
         touch              创建空文件。实例：touch a    创建一个名为 a 的空文件
         
         mkdir              创建空目录。实例：mkdir a    创建一个名为 a 的空目录
         
                                其它常用方法：mkdir d1 d2 /home/user1/d3 创建三个空目录
                                
         cat,less,more  查看文件内容。实例：cat a    区别：cat 一次次全部显示，less 分页显示内容可返回
                                查看，more 同 less 只是查看文件内容的过程里不能向上返回。
                                
         rm                   删除文件或目录。实例：rm a 删除文件a，rm -r a 删除目录 a 及所有子目录和文件
         
         rmdir               删除空目录
         
         cp                   复制文件或目录。实例：cp a b 复制文件 a 为文件 b，cp -r a b 复制目录 a 为目录 b
         
         mv                   移动文件或目录或改名。
         
         find                  查找文件。实例：find . -name a 在当前目录查找名为 a 的文件
         
                                 sudo find / -name ls 从根目录开始查找名为 ls 的文件在什么位置
                                 
         pwd                 显示当前目录
         
         cd                    改变目录    实例：cd /boot 切换到 /boot 目录。cd - 切换到上次工作目录 。cd 回主目录 
         

    2). 磁盘管理
    
         df            查看磁盘容量及使用情况。如：df -h 以友好方式显示磁盘使用情况
         
         du           查看目录体积。如： du -sh 列出当前目录体积。sudo du /etc -sh 列出 /etc 目录体积
         
         mount      挂载磁盘设备。如：sudo mount /dev/cdrom /mnt 将光驱挂载到 /mnt 目录
         
         unmount  卸载磁盘设备。如：sudo unmount /dev/cdrom 卸载设备与卸载挂载点等效。
         
         eject        弹出磁盘设备。如：eject /dev/cdrom 弹出光驱
         
         hdparm    测试磁盘速度。如：sudo hdparm -tT /dev/sda 测试磁盘 sda 的缓存和缓冲读取速度
         
         cfdisk       磁盘分区。
         
         mkfs         分区格式化。 如：sudo mkfs -T fat32 /dev/sda1 将sda上的第一个分区格式化为 fat32 格式
         
         sync         将已更改的数据写入磁盘。

    3). 用户管理
    
         useradd        添加一个用户。如：sudo useradd user1 添加一个名为 user1 的用户。
         
         userdel         删除一个用户。如：sudo userdel user1 删一个名为 user1 的用户。
         
         groupadd      添加一个用户组。如：sudo groupadd guest 添加一个名为 guest 的用户组。
         
         groupdel       删除一个用户组。如：sudo groupdel guest  删除一个名为 guest 的用户组。
         
         groups          查看用户所在组。如：groups user3 查看 user3 属性哪个组。
         
         usermod       更改一个用户的属性。如：sudo usermod -g guest user3 将 user3 移到 guest 这个组中。
         
         id                  显示用户的 ID 号。如：id user3 查看 user3 这个用户的 ID 号。
         
         passwd         修改用户密码。如：sudo passwd user3 回车后修改 user3 这个用户的密码。
         
                              sudo passwd    修改 root 密码
                              
         who               显示当前所有用户。
         
         whoami         显示当前用户。
         
         finger            显示用户信息。如：finger root 显示 root 的信息。
         
         su                 切换用户。如：su root 切换为root 身份，su - root 完全切换到
         
         sudo             切换用户并运行。如：sudo -u user3 ls 以 user3 身份列出当前目录

    4). 进程管理
    
          ps            查看当前进程。如：ps aux 显示当前所有进程
          
          pstree      树型显示进程。
          
          top           动态查看进程。
          
          kill [pid]    通过进程号结束进程。
          
          pkill [pname]  通过进程名结束进程。
          
          jobs          查看后台进程。

    5). 网络命令
    
         ping [ip/domain]        测试到指定电脑的网络是否畅通。
         
         ifconfig                      查看当前网络 IP 信息
         
         netstat -an                查看当前网络连接及端口信息
         

    6). 压缩包管理
    
            文件类型            相关命令
            
            .tar                     tar    常用参数：c 打包，v 可视进度，f 生成一个文件，x 解包
                                      sudo tar cvf backup.tar /var/log/*  将 /var/log 下所有文件打包为 backup.tar 文件
                                      tar xvf backup.tar    解包 backup.tar 文件
                                      
            .gz                      gzip,gunzip    对应 gz 的压缩与解压缩
            
            .bz2                    bzip2,bunzip    对应 bz2 的压缩与解压缩，压缩率比 gz 高点。
            
            .zip                     zip,unzip         对应 zip 格式的压缩与解压
            
            .rar                     rar a,rar x       对应 rar 格式的压缩与解压
            
            .Z                       compress,uncompress  也可使用 gz 工具解压
            
            7z                       7z 工具可以解压以上所有格式

            .tar.gz                通常是用 tar 打包，再用 gzip 工具压缩生成的
             
            .tar.bz2              通常是用 tar 打包，再用 bzip2 工具压缩生成的

    7). Ubuntu 任务管理
    
            单次任务：只执行一次的任务。                ( at 编辑，atq 查看，atrm 删除 )
            
            周期任务：按一定周期循环执行的任务。  ( crontab -e 编辑，crontab -l 查看，crontab -r 清空任务)
            
            实例：
            
            1). 在 0:00 分执行关机命令：# at 0:00 回车开始编辑命令：at>poweroff 按 Ctrl+D 保存并退出。
            
                  查看单次任务列表：#atq 回车，删除单次任务：#atrm [atid] 按任务 ID 号删除任务。
                  
            2). 每天零晨 2 点执行 back.sh 脚本
            
                   #crontab -e 进入编辑，选择一款编辑器开始编辑内容如：
                   
                   #m h dom mon dow command (格式)
                   
                    * 2 * * * back.sh (保存)
                    
                   重启计划任务即可将周期任务列入进程：#sudo /etc/init.d/cron restart
                   
                   每分钟执行，每一个参数用：*/1

    入门篇就讲这几个基本命令的基本用法，熟悉了解一下 Linux 服务器操作规则便可。

转载　　http://www.gaohelong.com/post/198
