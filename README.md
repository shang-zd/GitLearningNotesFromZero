# LearningNote

=================
# git的小白学习笔记
=================

This is a collection of learning notes git

By a freshman in coding

Please contact me if you have any comments

# 配置文本编辑器
以notepad++为例，命令：
git config --global core.editor \
"'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
注意书写格式，C:/Program Files/Notepad++为notepad++.exe的实际安装路径

设置在bash中用notepa++打开文档以供编辑：

在git的安装目录下有个etc的文件夹，在bash.bashrc的文件（C:\Program Files\Git\etc\bash.bashrc）最后添加上：
alias notepad++=\
"'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"

此时，在git bash环境中调用notepad++的方法是：
notepad++ 文件名

上面alias 后面的notepad++就是一个别名，可以替换为任何你想要的名字，如pad，不过这时调用notepad++打开文档的命令也相应的变为了： pad 文件名

