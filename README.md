# Introduction

**说明**：个人技术笔记，部分内容出自网络，归纳整理而来。


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
```
```
gitbook serve  //编译书籍
```
### 1.4 GitBook绑定GitHub
GitBook网站上新建图书，在setting选择中有GitHub一项，选择绑定指定仓库。
### 1.5 本地编写推送GitHub
在本地图书目录做git版本控制，推送到已绑定GitHub仓库中，便会自动关联同步到GitBook网站。
