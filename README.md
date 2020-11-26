# 说明

个人技术笔记，部分内容出自网络，归纳整理而来。


## 1. GitBook操作手册
### 1.1 简要概述
GitBook 是一个基于 Node.js 的命令行工具，可使用 Github/Git 和 Markdown 来制作精美的电子书。

GitBook重点是制作书，如果仅仅用来记笔记反而不够轻快。建议工作流程是:**Markdown做笔记-->整理笔记-->GitBook本地制作书-->推送GitBook网站（绑定GitHub做版本控制）**

GitBook分本地工具和GitBook网站，本地工具用来构建书，GitBook网站用来展示。用GitBook editor构建书最为方便，无需配置GitBook环境。
### 1.2 安装GitBook工具
安装GitBook前，要先安装Node.js。Node.js的安装，请移步这里：[在 Windows、Mac OS X 與 Linux 中安裝 Node.js 網頁應用程式開發環境](http://www.gtwang.org/2013/12/install-node-js-in-windows-mac-os-x-linux.html)安装完成这后，你可以在终端模式(win下打开cmd即可)下检验一下：
```
C:\Users\lenovo> node -v
v0.10.28
```
如果电脑上安装了Atom，则在相关目录下可以找到Node环境，仅需配置环境变量即可。

Gitbook是从NMP安装的，命令行（打开cmd，路径每个电脑不一）：
```
C:\Users\lenovo> npm install gitbook-cli -g
```
安装完之后，你可以检验下是否安装成功：
```
C:\Users\lenovo> gitbook -V
0.3.3
```
如果你看到了与上面类似的版本信息，则表示你已成功完装上了Gitbook。
### 1.3 GitBook使用
**必须的两个文件，README.md，SUMMARY.md()。**
README.md这个文件相当于一本Gitbook的简介，最上层(和SUMMARY.md同级)的是本书的Introduction。
SUMMARY.md()这个文件是一本书的目录结构，使用Markdown语法， 这个文件在使用gitbook命令行之前要先写好，以便之后生成书籍目录,如我们这本书的SUMMARY.md：
```
* [基本安装](howtouse/README.md)
 - [Node.js安装](howtouse/Nodejsinstall.md)
 - [Gitbook安装](howtouse/gitbookinstall.md)
 - [Gitbook命令行速览](howtouse/gitbookcli.md)
* [图书编辑](book/README.md)
 - [gitbook命令行&markdown编辑](book/gitbook-cli.md)
 - [gitbook editor编辑](book/editor.md)
* [图书输出](output/README.md)
 - [输出为静态网站](output/outfile.md)
 - [输出PDF](output/pdfandebook.md)
* [发布](publish/README.md)
  - [发布到gitbook.com](publish/gitbook.md)
  - [Github集成](publish/github.md)
  - [发布到Github Pages](publish/gitpages.md)
* [结束](end/README.md)
 ```
列表加链接，链接中可以使用目录，也可以不必使用。

两个基本命令：
```
gitbook init   //初始化目录结构
gitbook serve  //编译书籍
```
### 1.4 GitBook绑定GitHub
GitBook网站上新建图书，在setting选择中有GitHub一项，选择绑定指定仓库。
### 1.5 本地编写推送GitHub
在本地图书目录做git版本控制，推送到已绑定GitHub仓库中，便会自动关联同步到GitBook网站。
## 2. 创建GitHub公钥
### 2.1 首先启动一个Git Bash窗口（非Windows用户直接打开终端）
### 2.2 执行：
```
cd ~/.ssh
```
如果返回“… No such file or directory”，说明没有生成过SSH Key，直接进入第4步。否则进入第3步备份!
### 2.3 备份：
```
mkdir key_backup mv id_isa* key_backup
```
### 2.4 生成新的Key：（引号内的内容替换为你自己的邮箱）
```
ssh-keygen -t rsa -C "your_email@youremail.com"
```
输出显示：
> Generating public/private rsa key pair. Enter file in which to save the key (/Users/your_user_directory/.ssh/id_rsa):

直接回车，不要修改默认路径。
> Enter passphrase (empty for no passphrase): Enter same passphrase again:

设置一个密码短语，在每次远程操作之前会要求输入密码短语！闲麻烦可以直接回车，不设置。
### 2.5 成功：
> Your identification has been saved in /Users/your_user_directory/.ssh/id_rsa. Your public key has been saved in /Users/your_user_directory/.ssh/id_rsa.pub. The key fingerprint is: ... ..

### 2.6 提交公钥：
#### 2.6.1 找到.ssh文件夹，用文本编辑器打开“id_rsa.pub”文件，复制内容到剪贴板。
#### 2.6.2 打开 https://github.com/settings/ssh ，点击 Add SSH Key 按钮，粘贴进去保存即可。

### 2.7 push出错：
> ssh: connect to host github.com port 22: Bad file number
### 2.8 macos
在macos系统中还要执行如下命令：
```
ssh-keyscan -t rsa github.com >> ~/.ssh/known_hosts
```

**解决办法：**
在用户根目录(cd ~/.ssh)下的.ssh目录下新建一个config文件，指定端口为443，因为22端口被禁用了。
```
host github.com
hostname ssh.github.com
port 443
```
**测试：**
```
ssh -T git@github.com
```
出现“Are you sure you want to continue connecting(yes/no)?”输入yes按一下“Enter”，出现成功提示即可。

## 3. 资料收集
阮一峰文章：

[互联网协议入门（一）](http://www.ruanyifeng.com/blog/2012/05/internet_protocol_suite_part_i.html)

[互联网协议入门（二）](http://www.ruanyifeng.com/blog/2012/06/internet_protocol_suite_part_ii.html)

## 4. git常用命令
### 4.1 三个基本概念
* **工作区**(Workspace)是计算机中项目的根目录
* **暂存区**(Index)像个缓存区域，临时保存你的改动
* **版本库**(Repository)分为本地仓库（Local)和远程仓库(Remote)

几乎所有常用命令就是围绕这几个概念来操作的。

![simple](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015120901.png)

但只会使用以上命令是不够的，在这个复杂纷繁的程序世界，事情没你想的那么简单，不过有些事情想想就够了，不一定要去做，真要去做你也做不来，比如自己写个git来，但是，更多地的了解git是我们每个程序员都可以做得到的事。再看下图：  
![advance](http://ww4.sinaimg.cn/mw690/81b78497jw1eqnk1bkyaij20e40bpjsm.jpg)
### 4.2 新建代码库
```
# 在当前目录新建一个Git代码库
$ git init

# 新建一个目录，将其初始化为Git代码库
$ git init [project-name]

# 下载一个项目和它的整个代码历史
$ git clone [url]
```
### 4.3 配置
Git的设置文件为.gitconfig，它可以在用户主目录下（全局配置），也可以在项目目录下（项目配置）。
```
# 显示当前的Git配置
$ git config --list

# 编辑Git配置文件
$ git config -e [--global]

# 设置提交代码时的用户信息
$ git config [--global] user.name "[name]"
$ git config [--global] user.email "[email address]"
```
### 4.4 增加删除控制文件
```
# 添加指定文件到暂存区
$ git add [file1] [file2] ...

# 添加指定目录到暂存区，包括子目录
$ git add [dir]

# 添加当前目录的所有文件到暂存区
$ git add .

# 添加每个变化前，都会要求确认
# 对于同一个文件的多处变化，可以实现分次提交
$ git add -p

# 删除工作区文件，并且将这次删除放入暂存区
$ git rm [file1] [file2] ...

# 停止追踪指定文件，但该文件会保留在工作区
$ git rm --cached [file]

# 改名文件，并且将这个改名放入暂存区
$ git mv [file-original] [file-renamed]
```
### 4.5 代码提交
```
# 提交暂存区到仓库区
$ git commit -m [message]

# 提交暂存区的指定文件到仓库区
$ git commit [file1] [file2] ... -m [message]

# 提交工作区自上次commit之后的变化，直接到仓库区
$ git commit -a

# 提交时显示所有diff信息
$ git commit -v

# 使用一次新的commit，替代上一次提交
# 如果代码没有任何新变化，则用来改写上一次commit的提交信息
$ git commit --amend -m [message]

# 重做上一次commit，并包括指定文件的新变化
$ git commit --amend [file1] [file2] ...
```
### 4.6 分支
```
# 列出所有本地分支
$ git branch

# 列出所有远程分支
$ git branch -r

# 列出所有本地分支和远程分支
$ git branch -a

# 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]

# 新建一个分支，并切换到该分支
$ git checkout -b [branch]

# 新建一个分支，指向指定commit
$ git branch [branch] [commit]

# 新建一个分支，与指定的远程分支建立追踪关系
$ git branch --track [branch] [remote-branch]

# 切换到指定分支，并更新工作区
$ git checkout [branch-name]

# 切换到上一个分支
$ git checkout -

# 建立追踪关系，在现有分支与指定的远程分支之间
$ git branch --set-upstream [branch] [remote-branch]

# 合并指定分支到当前分支
$ git merge [branch]

# 选择一个commit，合并进当前分支
$ git cherry-pick [commit]

# 删除分支
$ git branch -d [branch-name]

# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
```
### 4.7 标签
```
# 列出所有tag
$ git tag

# 新建一个tag在当前commit
$ git tag [tag]

# 新建一个tag在指定commit
$ git tag [tag] [commit]

# 删除本地tag
$ git tag -d [tag]

# 删除远程tag
$ git push origin :refs/tags/[tagName]

# 查看tag信息
$ git show [tag]

# 提交指定tag
$ git push [remote] [tag]

# 提交所有tag
$ git push [remote] --tags

# 新建一个分支，指向某个tag
$ git checkout -b [branch] [tag]
```
### 4.8 查看信息
```
# 显示有变更的文件
$ git status

# 显示当前分支的版本历史
$ git log

# 显示commit历史，以及每次commit发生变更的文件
$ git log --stat

# 搜索提交历史，根据关键词
$ git log -S [keyword]

# 显示某个commit之后的所有变动，每个commit占据一行
$ git log [tag] HEAD --pretty=format:%s

# 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
$ git log [tag] HEAD --grep feature

# 显示某个文件的版本历史，包括文件改名
$ git log --follow [file]
$ git whatchanged [file]

# 显示指定文件相关的每一次diff
$ git log -p [file]

# 显示过去5次提交
$ git log -5 --pretty --oneline

# 显示所有提交过的用户，按提交次数排序
$ git shortlog -sn

# 显示指定文件是什么人在什么时间修改过
$ git blame [file]

# 显示暂存区和工作区的差异
$ git diff

# 显示暂存区和上一个commit的差异
$ git diff --cached [file]

# 显示工作区与当前分支最新commit之间的差异
$ git diff HEAD

# 显示两次提交之间的差异
$ git diff [first-branch]...[second-branch]

# 显示今天你写了多少行代码
$ git diff --shortstat "@{0 day ago}"

# 显示某次提交的元数据和内容变化
$ git show [commit]

# 显示某次提交发生变化的文件
$ git show --name-only [commit]

# 显示某次提交时，某个文件的内容
$ git show [commit]:[filename]

# 显示当前分支的最近几次提交
$ git reflog
```
### 4.9 远程同步
```
# 下载远程仓库的所有变动
$ git fetch [remote]

# 显示所有远程仓库
$ git remote -v

# 显示某个远程仓库的信息
$ git remote show [remote]

# 增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]

# 取回远程仓库的变化，并与本地分支合并
$ git pull [remote] [branch]

# 上传本地指定分支到远程仓库
$ git push [remote] [branch]

# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force

# 推送所有分支到远程仓库
$ git push [remote] --all
```
### 4.10 撤销
```
# 恢复暂存区的指定文件到工作区
$ git checkout [file]

# 恢复某个commit的指定文件到暂存区和工作区
$ git checkout [commit] [file]

# 恢复暂存区的所有文件到工作区
$ git checkout .

# 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
$ git reset [file]

# 重置暂存区与工作区，与上一次commit保持一致
$ git reset --hard

# 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
$ git reset [commit]

# 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
$ git reset --hard [commit]

# 重置当前HEAD为指定commit，但保持暂存区和工作区不变
$ git reset --keep [commit]

# 新建一个commit，用来撤销指定commit
# 后者的所有变化都将被前者抵消，并且应用到当前分支
$ git revert [commit]

# 暂时将未提交的变化移除，稍后再移入
$ git stash
$ git stash pop
```
### 4.11 其他
```
# 生成一个可供发布的压缩包
$ git archive
```
## 5. Atom相关
### 5.1 离线安装插件
`git clone`插件到本地`C:\Users\tango\.atom\packages`目录，从对应GitHub上。
```
apm install   #进入下载插件根目录
```
### 5.2 插件推荐
#### 5.2.1 linter
Linter is a **base linter** provider for the hackable Atom Editor. Additionally, you need to install a specific linter for your language. You will find a full list below in the Available linters section.
#### 5.2.1 linter write good
依赖linter，Naive linter for English prose for developers who can't write good and wanna learn to do other stuff good too.
### 5.3 和系统其他软件快捷键冲突
'ctrl-shift-alt-f'全局搜索无效，发现和搜狗输入法快捷键冲突。
## 6. 读ryf的js教程
[js标准参考教程-ryf](http://javascript.ruanyifeng.com/grammar/object.html)
### 6.1 不懂得地方
with区块内部，模板变量name可以被对象o的属性替换，而p依然是全局变量。这就是很多模板引擎的实现原理。
```
var str = 'Hello <%= name %>!';

var o = {
  name: 'Alice'
};

function tmpl(str, obj) {
  str = 'var p = [];' +
    'with (obj) {p.push(' + parser(str) + ')};' +
    'return p;'
  var r = (new Function('obj', str))(obj);
  return r.join('');
}

tmpl(str, o)
// "Hello Alice!"
```
