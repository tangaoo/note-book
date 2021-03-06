### 1. 安装google输入法

1. sudo apt-get install fcitx-googlepinyin
2. 搜索栏 搜language support，安装完全语言支持。
3. 键盘输入法系统，选择fcitx，重启。
4. 单击在右上角键盘图标，添加谷歌拼音输入法，就ok。
5. 文本框可能有分辨率问题，重新启动一次键盘输入法系统ok。

### 2. 安装chromium插件

1. 高版本chrom浏览器不支持直接拖拽。
2. 先把插件重命令成.tar，然后解压成文件夹。
3. 进入chrome://extensions/，然后在拖拽，即ok。

### 3. 启用点击左边dock图表最小化

- gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'minimize'

### 4. markdown语法

- [markdown语法参考](https://shd101wyy.github.io/markdown-preview-enhanced/#/markdown-basics?id=links)

### 5. ubuntu安装、卸载程序
1. 安装
    ```
    dpkg -i xxx
    ```
2. 卸载
   ``` 
   apt-get remove   
   #删除已安装的软件包（保留配置文件），不会删除依赖软件包，保留配置文件；
   
   apt-get purge    
   #删除已安装的软件包（不保留配置文件)，删除软件包，同时删除相应依赖软件包；
   
   apt-get autoremove 
   #删除为了满足依赖而安装的，但现在不再需要的软件包（包括已安装包），保留配置文件；

   apt-get clean
   删除已经安装过的的软件安装包；即自动将/var/cache/apt/archives/下的所有deb删掉，相当于清理下载的软件安装包；
   ```
### 6. rar文件解压

1. 默认无法解压rar，需要rar工具
2. rar压缩工具
   ```
   sudo apt-get install rar
   ```
3. rar解压工具
   ```
   sudo apt-get install unrar
   ```
4. 压缩
   ```
   rar a FileName.rar DirName
   ```
5. 解压
   ```
   rar x FileName.rar
   ```
### 7. 安装oh-my-zsh
1. 安装 **zsh sudo apt install zsh**
2. 从改默认shell，重启 **chsh -s /bin/zsh**
3. 下载oh-my-zsh脚本，并执行 
   ```
   wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh
   sh install.sh
   ```
4. 更改zsh配置文件，主题 **ZSH_THEME="robbyrussell"**
5. 增加插件 **pplugins=(git pip z history-substring-search extract vi-mode)**
   
### 8. 安装monaco字体

1. sudo mkdir -p /usr/share/fonts/truetype/ttf-monaco && \
2. sudo wget https://gist.github.com/rogerleite/b50866eb7f7b5950da01ae8927c5bd61/raw/862b6c9437f534d5899e4e68d60f9bf22f356312/mfont.ttf -O - > \
/usr/share/fonts/truetype/ttf-monaco/Monaco_Linux.ttf && \
3. sudo fc-cache

### 9. happypeter网站更改
   [happypeter网站](http://haoduoshipin.com/all.html )

### 10. 中文文件夹改英文
使用 LC_ALL=C xdg-user-dirs-update --force 命令可以强制创建英语目录

### 11. ssh
1. ssh是网上两台计算机互联的一套协议。
2. 默认端口22.
3. 安装
   ```
   sudo apt-get update  # 更新 apt-get 工具
   sudo apt-get install openssh-server
   sudo apt-get install openssh-client 	
   ``` 
4. 修改配置文件sudo vim /etc/ssh/sshd_config
   ```
   Port 22                       # 默认22端口，如果有端口占用可以自己修改
   PermitRootLogin yes           # 如果配置文件中没有这行内容，需要手动添加
   PasswordAuthentication yes    # 密码验证登录
   ```
5. 重启服务 sudo service ssh start
6. 登陆 ssh name@ip
7. 上传下载 scp -r tao@192.168.31.205:~/Desktop/test.txt ./  (重远端下载文件到本地，上传反之，类似cp操作) 

### 12. ack 字符串查找（擅长源代码查找）
1. install
   ```
   sudo aptitude install ack-grep
   sudo ln -s `which ack-grep` /bin/ack
   ```
2. ack默认忽略许多文件格式，下面命令查看具体哪些。
   ```
   ack --help-types|less
   ```
3. example
   ```
   ack hello          #查找hello字符串
   ack -a hello       #取消默认忽略
   ack --js hello     #查找某特定语言
   ack --nojs hello   #排除某特定语言
   ```

### 13. lsusb 查看usb相关属性（device id ...）

### 14. `ubuntu` 添加环境变量
1. 在profile文件中追加环境变量
   ```
   sudo vim /etc/profile
   ```
2. 插入环境变量（追加在profile文件末尾）
   ```
   export PATH=$PATH:/opt/EmbedSky/4.3.3/bin
   ```
3. 立即生效profile
   ```
   source profile
   ```
### 15. Embedded device setting time
1. set system time
   ```
   date -s "20210-04-04 18:00:00"
   ```
2. write time back RTC(hardware)
   ```
   hwclock -w
   ```
3. recover system for RTC(hardware)
   ```
   hwclock -s
   ```
### 16. Cross Compiler 交叉编译工具
1. 获取途径 ？

### 17. Linux kernel移植
1. 获取官方源码 https://www.kernel.org/
   
2. 配置编译环境
   * 交叉编译工具
   * arch 选择
3. 选择mach芯片（例如 arch/arm/mach-s3c2440/mach-smdk2440.c） 
   
4. 改开发版对应时钟频率
   * 例如 TQ2440开发板对应修改文件在 arch/arm/mach-s3c2440/mach-smdk2440.c 
  
5. make menuconfig
   * 选择最加载接近模版 （arch/arm/configs/）
   * 修改相关配置，保存
  
6. 配置文件另存为 .config
   
7. 修改机器码
   * 与uboot对应，在目录 arch/arm/tools/mach-types

8. 编译内核
   ```
   make zImage
   ```

### 18. 编译驱动（要在 kernel 内部实现驱动编译）
1. 在内核相关目录添加驱动源码（例如 drives/char）

2. 改同级目录下 Kcongfig 文件，为了能在 make menuconfig 工具中显示
   
3. 改同级目录下 Makefile 文件
   
4. make menuconfig 配置添加该驱动
   * M 表示编译进模块，或直接编译进来内核，或不编译

5. 编译
   * make SUBDIR=drives/char/ modules

6. 装载与卸载
   * insmod
   * rmmod

### 19. TFTP设置（宿主机与开发版传数据）
1. 安装软件
   ```
   $ sudo apt install tftpd-hpa
   ```
2. 配置
   ```
   $ sudo vim /etc/default/tftpd-hpa
   ```
   * 改tftp路径
   * OPTIONS 增加 --create

3. 重启tftp
   ```
   $ sudo systemctl restart tftpd-hpa
   ```

4. 详见链接 https://linuxhint.com/install_tftp_server_ubuntu/
   
### 20. 内核编译问题
1. 需要用root命令编译
   * sudo su  然后在编译。应该有其他方法？

### 21. nfs
0. ref
   https://www.howtoforge.com/how-to-install-nfs-client-and-server-on-ubuntu-2004/
   https://blog.csdn.net/niepangu/article/details/50274111

1. PC is server, Embeded board is client.
   
2. install
   ```
   $ sudo apt install nfs-kernel-server
   ```

3. config
   ```
   $ sudo mkdir /var/nfs/general -p
   $ sudo chown nobody:nogroup /var/nfs/general
   ```
   * change /etc/exports file
   * add `/var/nfs/general    client_ip(rw,sync,no_subtree_check)` to the file end
   * restart
   ```
   $ sudo systemctl restart nfs-kernel-server
   ```

4. try mount from Embeded board side(client)
   ```
   # mount –t nfs 192.168.1.8:/var/nfs/general /mnt –o nolock
   # cd /mnt
   # ls
   ```

