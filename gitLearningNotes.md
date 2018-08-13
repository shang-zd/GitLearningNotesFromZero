# git 常用命令

** 所有指令都可以通过 `git command --help` 查看其帮助文档 **  

## git init
**在现有目录中初始化仓库**：初始化命令，把当前目录变成git可以管理的仓库`repository`，具体表现为在当前目录下创建一个`.get`目录，并且这个目录是隐藏的，可以用`ls -ah`命令看见  
`.git`目录尽量**不要乱改**  
当前目录可以通过在bash中输入`pwd`指令查看  


## git config
`config` 编辑git的配置
例如，在安装完git后在命令行输入一下命令来配置用户名和邮件，**必须过程**：  
`git config --global user.name "Your Name"`  
`git config --global user.email "email@example.com"`

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
**提交更新**： `git commit -m <message>` 完成将更改添加到仓库，注意，此时远程的仓库并没有改变  
<message>信息是必须的，告诉仓库你进行了什么更改，可以避开这个参数，但是最好不要
**跳过使用暂存区域提交更新**：给 `git commit` 加上 `-a` 选项，Git就会自动把所有已经跟踪过的文件暂存起来一并提交，从而跳过 `git add` 步骤
 
## git rm
**移除文件**：要从 Git 中移除某个文件，就必须要从已跟踪文件清单中移除（确切地说，是从暂存区域移除），然后提交。可以用 `git rm` 命令完成此项工作，并连带从工作目录中删除指定的文件，这样以后就不会出现在未跟踪文件清
单中了。  
**从 Git 仓库中删除** :亦即从暂存区域移除，但仍然保留在当前工作目录,` git rm --cached <filename>`

## git mv
**移动文件**  
**在 Git 中对文件改名** ： ` git mv <file_from> <file_to>`  
以上一条命令相当于执行如下三条命令：  
* `mv <file_from> <file_to>`  
* `git rm <file_from>`  
* `git add <file_to>`  

## git log
**查看提交历史**：显示从最近到最远的提交`commit`日志， 不用任何参数的话，git log 会按提交时间列出所有的更新，最近的更新排在最上面。  
有多种方式可以控制输出显示形式，如：  
* `git log --pretty=oneline` 参数使每次`commit`只输出为一行，末尾是`git commit -m <message>`的`<message>`内容   
* `git log -p -<n>` 显示上`-n`次提交历史    
* `git log --stat` 显示到每次提交的简略的统计信息  
* `git log --pretty=<oneline	short	full	fuller>` 以指定的方式显示提交历史
* `git log --pretty=format:"%h - %an, %ar : %s"
`git log --pretty=format`常用的选项  
<table>
   <tr>
      <td> 选项 </td>
      <td> 说明 </td>
      <td>  </td>
   </tr>
   <tr>
      <td> %H </td>
      <td> 提交对象（commit）的完整哈希字串 </td>
      <td>  </td>
   </tr>
   <tr>
      <td>%h  </td>
      <td>提交对象的简短哈希字串</td>
      <td>  </td>
   </tr>
   <tr>
      <td>%T </td>
      <td> 树对象（tree）的完整哈希字串</td>
      <td>  </td>
   </tr>
   <tr>
      <td>%t </td>
      <td> 树对象的简短哈希字串</td>
      <td>  </td>
   </tr>
   <tr>
      <td>%P </td>
      <td> 父对象（parent）的完整哈希字串</td>
      <td>  </td>
   </tr>
   <tr>
      <td>%p </td>
      <td> 父对象的简短哈希字串</td>
      <td>  </td>
   </tr>
   <tr>
      <td>%an </td>
      <td> 作者（author）的名字</td>
      <td>  </td>
   </tr>
   <tr>
      <td>%ae </td>
      <td> 作者的电子邮件地址</td>
      <td>  </td>
   </tr>
   <tr>
      <td>%ad </td>
      <td> 作者修订日期（可以用 --date= 选项定制格式）</td>
      <td>  </td>
   </tr>
   <tr>
      <td>%ar </td>
      <td> 作者修订日期，按多久以前的方式显示</td>
      <td>  </td>
   </tr>
   <tr>
      <td>%cn </td>
      <td> 提交者（committer）的名字</td>
      <td>  </td>
   </tr>
   <tr>
      <td>%ce </td>
      <td> 提交者的电子邮件地址</td>
      <td>  </td>
   </tr>
   <tr>
      <td>%cd </td>
      <td> 提交日期</td>
      <td>  </td>
   </tr>
   <tr>
      <td>%cr </td>
      <td> 提交日期，按多久以前的方式显示</td>
      <td>  </td>
   </tr>
   <tr>
      <td>%s </td>
      <td> 提交说明</td>
      <td>  </td>
   </tr>
</table>
> 作者指的是实际作出修改的人，提交者指的是最后将此工作成果提交到仓库的人。


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

























