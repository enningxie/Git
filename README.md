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
