# Git使用环境配置

## Git安装过程
在你开始使用 Git 前，需要将它安装在你的计算机上。 即便已经安装，最好将它升级到最新的版本。 你可以通过软件包或者其它安装程序来安装，或者下载源码编译安装。
详细的安装教程可以从[这里](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)找到。

**以windows下安装** 为例  
在 Windows 上安装 Git 也有几种安装方法。 官方版本可以在 Git 官方网站下载。 打开 http://git-scm.com/download/win，下载会自动开始。 要注意这是一个名为 Git for Windows的项目（也叫做 msysGit），和 Git 是分别独立的项目；更多信息请访问 http://msysgit.github.io/。

另一个简单的方法是安装 GitHub for Windows。 该安装程序包含图形化和命令行版本的 Git。 它也能支持 Powershell，提供了稳定的凭证缓存和健全的 CRLF 设置。 稍后我们会对这方面有更多了解，现在只要一句话就够了，这些都是你所需要的。 你可以在 GitHub for Windows 网站下载，网址为 http://windows.github.com。


## 使用`git config`指令配置

// TODO


## 配置文本编辑器
以**notepad++** 为例，命令：
git config --global core.editor \
"'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
注意书写格式，C:/Program Files/Notepad++为notepad++.exe的实际安装路径

**设置在bash中用notepa++打开文档** 以供编辑：

在git的安装目录下有个etc的文件夹，在bash.bashrc的文件（C:\Program Files\Git\etc\bash.bashrc）最后添加上：
alias notepad++=\
"'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"

此时，在git bash环境中调用notepad++的方法是：
notepad++ 文件名

上面alias 后面的notepad++就是一个别名，可以替换为任何你想要的名字，如pad，不过这时调用notepad++打开文档的命令也相应的变为了： pad 文件名

## .gitignore
**忽略文件**：将不需要git管理的文件创建一个列表，存储到`.gitignore`文件，便可实现git对该部分文件的忽略  
GitHub 有一个十分详细的针对数十种项目及语言的 .gitignore 文件列表，你可以在https://github.com/github/gitignore 找到它.  


## 在Atom下使用Git

此时你需要在Atom下安装几个package，如`Git diff`, `Github`, `Git Plus`

安装方法也很简单，`Ctrl + ,`打开`Atom`的`Setting` 菜单，找到`Install`， 在Install Packages下输入需要安装的package名称，找到对应的package，安装即可。
