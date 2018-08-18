# Git使用环境配置

## Git安装过程
在你开始使用 Git 前，需要将它安装在你的计算机上。 即便已经安装，最好将它升级到最新的版本。 你可以通过软件包或者其它安装程序来安装，或者下载源码编译安装。
详细的安装教程可以从[这里](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)找到。

**以windows下安装** 为例  
在 Windows 上安装 Git 也有几种安装方法。 官方版本可以在 Git 官方网站下载。 打开 http://git-scm.com/download/win，下载会自动开始。 要注意这是一个名为 Git for Windows的项目（也叫做 msysGit），和 Git 是分别独立的项目；更多信息请访问 http://msysgit.github.io/。

另一个简单的方法是安装 GitHub for Windows。 该安装程序包含图形化和命令行版本的 Git。 它也能支持 Powershell，提供了稳定的凭证缓存和健全的 CRLF 设置。 稍后我们会对这方面有更多了解，现在只要一句话就够了，这些都是你所需要的。 你可以在 GitHub for Windows 网站下载，网址为 http://windows.github.com。


## 使用` git config` 指令配置Git环境

Git 自带一个 git config 的工具来帮助设置控制 Git 外观和行为的配置变量。 这些变量存储在三个不同的位置：

* ` /etc/gitconfig` 文件: 包含系统上每一个用户及他们仓库的通用配置。 如果使用带有 `--system` 选项的 ` git config` 时，它会从此文件读写配置变量。

* ` ~/.gitconfig` 或 ` ~/.config/git/config` 文件：只针对当前用户。 可以传递 `--global` 选项让 Git 读写此文件。

* 当前使用仓库的 Git 目录中的 ` config` 文件（就是 ` .git/config` ）：针对该仓库。

每一个级别覆盖上一级别的配置，所以 ` .git/config` 的配置变量会覆盖 ` /etc/gitconfig` 中的配置变量。
在 Windows 系统中，Git 会查找 ` $HOME` 目录下（一般情况下是 ` C:\Users\$USER）` 的 ` .gitconfig` 文件。 Git 同样也会寻找 ` /etc/gitconfig` 文件，但只限于 ` MSys` 的根目录下，即安装 Git 时所选的目标位置。

**必须的配置：用户信息**  
当安装完 Git 应该做的第一件事就是设置你的用户名称与邮件地址。 这样做很重要，因为每一个 Git 的提交都会使用这些信息，并且它会写入到你的每一次提交中，不可更改：

* ` git config --global user.name "John Doe"` 
*  ` git config --global user.email johndoe@example.com` 

再次强调，如果使用了 `--global` 选项，那么该命令只需要运行一次，因为之后无论你在该系统上做任何事情， Git 都会使用那些信息。 当你想针对特定项目使用不同的用户名称与邮件地址时，可以在那个项目目录下运行没有 `--global` 选项的命令来配置。很多 GUI 工具都会在第一次运行时帮助你配置这些信息。

**检查配置信息**  
如果想要检查你的配置，可以使用 ` git config --list` 命令来列出所有 Git 当时能找到的配置。

` git config --list` 
> user.name=John Doe  
> user.email=johndoe@example.com  
> color.status=auto  
> color.branch=auto  
> color.interactive=auto  
> color.diff=auto  
> ...  

你可能会看到重复的变量名，因为 Git 会从不同的文件中读取同一个配置（例如：` /etc/gitconfig ` 与 ` ~/.gitconfig` ）。 这种情况下，Git 会使用它找到的每一个变量的最后一个配置。

你可以通过输入 ` git config <key>` ： 来检查 Git 的某一项配置

` git config user.name` 


好了，说了这么多，` git congif` 的通用语法格式为 ` git config [<options>]`  

**标明要修改的配置文件位置**  
* `--global`              use global config file  
* `--system`              use system config file  
* `--local `              use repository config file  
* `-f, --file <file>`     use given config file  
* `--blob <blob-id> `     read config from given blob object  

**具体配置的修改命令**
* `--get `                get value: name [value-regex]
* `--get-all `            get all values: key [value-regex]
* `--get-regexp`          get values for regexp: name-regex [value-regex]
* `--get-urlmatch`        get value specific for the URL: section[.var] URL
* `--replace-all`         replace all matching variables: name value [value_regex]
* `--add`                 add a new variable: name value
* `--unset `              remove a variable: name [value-regex]
* `--unset-all`           remove all matches: name [value-regex]
* `--rename-section`      rename section: old-name new-name
* `--remove-section `     remove a section: name
* `-l, --list`            list all
* `-e, --edit`            open an editor
* `--get-color`           find the color configured: slot [default]
* `--get-colorbool`       find the color setting: slot [stdout-is-tty]

**类型**  

* `-t, --type <>`         value is given this type
* `--bool`                value is "true" or "false"
* `--int`                 value is decimal number
* `--bool-or-int`         value is --bool or --int
* `--path`                value is a path (file or directory name)
* `--expiry-date`         value is an expiry date

**其它**

* `-z, --null`            terminate values with NUL byte
* `--name-only`           show variable names only
* `--includes`            respect include directives on lookup
* `--show-origin`         show origin of config (file, standard input, blob, command line)
* `--default <value>`     with --get, use default value when missing entry

**可以通过git congif 修改的配置项**

* core.symlinks=false
* core.autocrlf=true
* core.fscache=true
* color.diff=auto
* color.status=auto
* color.branch=auto
* color.interactive=true
* help.format=html
* rebase.autosquash=true
* http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
* http.sslbackend=openssl
* diff.astextplain.textconv=astextplain
* filter.lfs.clean=git-lfs clean -- %f
* filter.lfs.smudge=git-lfs smudge -- %f
* filter.lfs.process=git-lfs filter-process
* filter.lfs.required=true
* credential.helper=manager
* core.editor='C:\Program Files\Notepad++\notepad++.exe' -multiInst -notabbar -nosession -noPlugin
* filter.lfs.required=true
* filter.lfs.clean=git-lfs clean -- %f
* filter.lfs.smudge=git-lfs smudge -- %f
* filter.lfs.process=git-lfs filter-process
* user.name=userName
* user.email=emailAddress
* core.editor='C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin
* core.repositoryformatversion=0
* core.filemode=false
* core.bare=false
* core.logallrefupdates=true
* core.symlinks=false
* core.ignorecase=true
* remote.origin.url=yourGitHubUrlOrAnyRemoteGitAddress
* remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
* branch.master.remote=origin
* branch.master.merge=refs/heads/master

## 配置文本编辑器
既然用户信息已经设置完毕，你可以配置默认文本编辑器了，当 Git 需要你输入信息时会调用它。如果未配置，Git 会使用操作系统默认的文本编辑器。 如果你想使用不同的文本编辑器，例如 Emacs，可以这样做：  

 ` git config --global core.editor emacs` 

再以**notepad++** 为例，命令：  
` git config --global core.editor \
"'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"` ，注意书写格式，` C:/Program Files/Notepad++` 为notepad++.exe的实际安装路径

**设置在bash中用notepa++打开文档** 以供编辑：

在git的安装目录下有个etc的文件夹，在bash.bashrc的文件（C:\Program Files\Git\etc\bash.bashrc）最后添加上：
` alias notepad++=\
"'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"` 

此时，在git bash环境中调用notepad++的方法是：
notepad++ 文件名

上面alias 后面的notepad++就是一个别名，可以替换为任何你想要的名字，如pad，不过这时调用notepad++打开文档的命令也相应的变为了： pad 文件名

## .gitignore
**忽略文件**：将不需要git管理的文件创建一个列表，存储到 ` .gitignore` 文件，便可实现git对该部分文件的忽略  
GitHub 有一个十分详细的针对数十种项目及语言的 .gitignore 文件列表，你可以在https://github.com/github/gitignore 找到它.  


## 在Atom下使用Git

此时你需要在Atom下安装几个package，如 ` Git diff` , ` Github` , ` Git Plus` 

安装方法也很简单，` Ctrl + ,` 打开` Atom` 的` Setting` 菜单，找到` Install` ， 在Install Packages下输入需要安装的package名称，找到对应的package，安装即可。

这些插件的功能就是把一些Git命令给你封装好了，如果你不懂Git命令，但也能从字面意思上对这些功能判断个大概


## 在visual studio code下使用Git

vs code是我最喜欢的文本编辑器之一了，所以在这里也顺便提一句。

vs code已经内置了Git相关的ui（界面）了，只要你已经将Git安装到了你的电脑中，安装完vs code后不需要特别的配置，便可使用Git了。

vs code下有至少种使用Git的方法：

* 利用vs code提供的ui，这个比较简单，点击vs code界面左侧的一个叉子型的图标（source control）便可以看到
* REPL方式。打开终端（` ctrl + j` ），直接输入Git命令即可，这种方式比较灵活
* ` ctrl + shift + p` 打开vs code的命令输入条，直接输入Git的命令

各种方式功能大同小异，看个人喜好选择即可。








