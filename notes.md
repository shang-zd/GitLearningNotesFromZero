# git 常用命令

## git init
**在现有目录中初始化仓库**：初始化命令，把当前目录变成git可以管理的仓库`repository`，具体表现为在当前目录下创建一个`.get`目录，并且这个目录是隐藏的，可以用`ls -ah`命令看见  
`.git`目录尽量**不要乱改**  
当前目录可以通过在bash中输入`pwd`指令查看  


## git config
`config` 编辑git的配置
例如，在安装完git后在命令行输入一下命令来配置用户名和邮件，**必须过程**：  
`$ git config --global user.name "Your Name"`  
`$ git config --global user.email "email@example.com"`

## git status
**状态简览**：获取仓库的当前状态，显示哪些文件被更改了  
`git status -s` 或 `git status --short` 命令使得以更加紧凑的格式输出


## git diff
**查看未暂存**的修改 `git diff <filename> `显示具体修改了哪些内容  
**查看已暂存**的将要添加到下次提交里的内容，可以用 git diff --cached 命令。（Git 1.6.1 及更高版本还允许使用 git diff --staged，效果是相同的，但更好记些。）



## git add
`git add <filename>` 
**暂存已修改文件**： 添加文件到仓库等待提交，可以多次使用，且只有`add`后的更改才会被提交  
**跟踪新文件**：对于新创建的文件，`add`命令使其更改被git跟踪

## git commit
`git commit -m <message>` 完成将更改添加到仓库，注意，此时远程的仓库并没有改变  
<message>信息是必须的，告诉仓库你进行了什么更改，可以避开这个参数，但是最好不要


## git log
显示从最近到最远的提交`commit`日志， 有多种方式可以控制输出显示形式  
`--pretty=oneline` 参数使每次`commit`只输出为一行，末尾是`git commit -m <message>`的`<message>`内容


## git reset
回退到之前的版本
git中用`HEAD`来表示当前版本，也就是最新的提交的版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。

也可以用`git reset --hard <version>`来实现往任意指定版本的回退，其中版本号`<version>`（就是文件某个版本对应的hash码）可以不用写全，仅写前几个字母即可，git会自动去找。当然也不能只写前一两位，因为Git可能会找到多个版本号，就无法确定是哪一个了。


## git reflog
显示在git的每一次操作命令

## git log


## git pull
取回远程仓库中的内容


## git push




 
## .gitignore
**忽略文件**：将不需要git管理的文件创建一个列表，存储到`.gitignore`文件，便可实现git对该部分文件的忽略  
GitHub 有一个十分详细的针对数十种项目及语言的 .gitignore 文件列表，你可以在https://github.com/github/gitignore 找到它.  

























