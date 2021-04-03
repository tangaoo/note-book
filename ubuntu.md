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
