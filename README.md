# Git

`gitk`  
启动图形查看模式

Git 配置文件：（优先级从高到低）  
- 文件夹中“.git”子文件夹内的config文件  
只对它所在的文档库有效；
- 登陆账号的home directory 中的.gitconfig文件  
只对此账号登录的用户有效；
- Git程序的安装文件夹中的etc/gitconfig文件  
对所有登录账号和所有Git文档库都有效。

`git config -l`  
显示上述三个配置文件中所有的设置项，顺序是先显示优先权最低的设置，再显示优先权高的设置。

`git config --system -l`  
显示git程序安装文件夹中的etc/gitconfig文件内的设置。

`git config --global -l`  
显示登录账号的home directory中的.gitconfig文件内的设置。

在登录账号的home directory 中的.gitconfig文件内记录，作者的姓名和email：  
`git config --global user.name 'xxx'`  
`git config --global user.email 'xxx'`

`git config`指令的选项来决定要将配置写入到哪一个配置文件内：  
`--global` 表示home directory中的.gitconfig配置文件；  
`--system` 表示Git程序文件夹中的etc/gitconfig配置文件。

删除配置文件中的项：  
`git config --unset user.name` 删除文档库配置文件中的操作者姓名   
删除其它配置文件中的项，视情况加入`--global`或者`--system`选项。

定义指令别名的方法：  
`git config alias.指令别名 '正式的指令和选项'`  
指令别名不可以包含空格  
示例：`git config alias.con 'config -l'`  
就是说`git con`等价于`git config -l`  
删除这个alias，同样使用`--unset`  
`git config --unset alias.con`

`git diff`  
用来执行文件对比的功能。

修改默认的文本编辑器和文件对比程序  
--TODO

Git追踪文件的方式；Git会将文件和文件夹分成以下三类：  
- 被追踪的（tracked）
- 忽略的（ignored）
- 不被追踪的（untracked）
> 一开始，所有的文件都是untracked。如果执行`git status`，它就会列出untracked文件列表，这是要提醒我们哪些文件还没有被归类。在正常情况下，文件夹中的所有的文件应该被分类成tracked或是ignored。tracked状态的文件就是已经加入Git文档库的文件。要让文件变成ignored状态（也就是让git不要检查这个文件），必须先在文件夹中创建一个名为".gitignore"的文件，然后把要忽略的文件逐一列在这个文件中（一个文件一行）。

关于.gitignore文件的用法：  
- '.gitignore'文件影响范围是它所在文件夹和所有的子文件夹。
- 每个文件夹都可以创建自己的'.gitignore'文件，如果它上层的文件夹也有'.gitignore'文件，这个文件夹也会受到它的影响。
- '.gitignore'文件中可以用`#`字符开头表示注释，文件夹路径是用`/`字符，文件名可以使用通配符`*`。另外还可以用`!`字符表示排除，例如以下设置表示要忽略所有拓展名是txt的文件，但是不包括note.txt：
> *.txt  
\# 设置不要忽略note.txt文件  
! note.txt

`git add`指令把文件内容加入Git的索引；  
`git commit`指令把Git索引中的文件内容加入文档库。

`git rm`是用来删除文档库中的文件或是Git索引中的文件，也可以删除文件夹中的文件  
`git rm 文件名`  
git先会执行两项检查：  
- Git索引中有没有该文件的内容（刚刚有没有`git add`过），如果有这个文件的内容和文档库中的不一样，为了避免丢失数据，Git会显示提示信息，然后放弃执行。
- 文件夹中的文件内容是不是和数据库中的一样，如果不一样，Git同样会显示提示信息，然后放弃执行。  

如果通过以上检查，Git会马上删除文件夹中的文件，然后在索引中记录要从文档库中删除该文件。

`git log --graph --oneline`  
以最简单的方式列出commit节点的演进图。

Git提供了一个叫做'HEAD'的节点标签，这个节点标签永远代表最新的commit。  
`git show HEAD` 显示最新的commit的详细数据

`git branch xxx`  
新建分支

`git branch -d xxx`  
删除分支

`git branch -m xxx`  
修改分支名称

`git checkout xxx`  
切换到xxx分支

`git merge xxx`  
合并分支

`git reset --hard HEAD^`  
恢复操作

`git checkout -b xxx`  
创建新分支

`git clone`  
克隆远程库到本地

`git push origin xxx`  
推送xxx分支到远程库

`git remote add 远程git文档库名称 远程git文档库的url`  
本地库与远程库建立联系

`git remote add` 补充说明：  
1. 远程git文档库的名称不一定要叫做origin，可以使用其它名称
2. 远程git文档库也不是唯一的，我们可以在本地git文档库中加入其它对应的远程git文档库

`git remote rm 远程git文档库名称`  
删除关系

`git remote rename 旧名称 新名称`  
重命名远程git文档库

`git remote set-url 远程库的名称 新的url`  
改变远程库的url

`git remote show 远程库的名称`  
显示某个远程库的详细信息

`git ls-remote`  
列出本地库对应的所有的远程库

`git remote -v`  
显示远程库的相关设置

`git push 远程库的名称 --delete 分支名称`  
把远程库的某一个分支删除

`ssh-keygen`  
创建ssh密钥（id_rsa是私钥，id_rsa.pub是公钥）

`git fetch`  
从刚刚指定的git文档库获取新内容
