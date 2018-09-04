1.安装git

2.配置用户名，邮箱
命令：git config  --global user.name "yourname"
      git config  --global user.email "youremail"

3.创建一个仓库
命令：git init(可以先建立一个文件夹，然后进入这个文件夹执行这条命令，这个文件夹就是仓库)

4.把文件添加到仓库
命令：git add 文件路径（文件必须放到仓库里面（仓库文件夹或者其子文件夹）才能提交成功）

5.把文件提交到仓库
git commit -m "对本次提交文件的说明" （git commit命令，-m后面输入的是本次提交的说明，可以输入任意内容，

当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录）

6.版本回退
git log  查看提交日志
git reflog 记录每一次提交或回退操做
git reset --hard HEAD^(^的个数表示回退几个版本，或者直接写版本号，版本号可以不写全)
git checkout -- <filename>  意思就是，{把filename文件在工作区的修改全部撤销}，这里有两种情况：

一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态

7.远程库
1.(创建SSH KEY（用来连接））   --第1步：在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。
如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key
命令：ssh-keygen -t rsa -C "youremail.com".

第2步：登陆GitHub，打开“settings”，“SSH and GPG Keys”页面：

然后，点“New SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容（id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人）

SSH Key添加成功.

2.远程库新建仓库
点击New repository,然后远程库随便取个名字，其他默认就可以;

现在将本地库与新建的这个远程库关联起来
命令：git remote and orgin git@hib.com:此处为你自己的github账户名/此处为你刚才仓库名.git

将本地库的内容推送到远程库
命令:git push -u orgin master（master表示推送的分支的名字）

再点击repository,就可以看到本地的内容已经同步上去了.

接下来，只要本地有提交，就可以通过
命令:git push origin master  把本地master分支的最新修改推送到Github.

3.从远程库克隆到本地
首先自己创建一个远程库(模拟你要克隆的库),创建的时候初始化;
接下来在本第git客户端运行命令
git clone git@github.com:<github用户名>/要克隆的库名.git

8.分支管理
(1)创建与合并分支
用命令: git checkout -b example   创建并转到example分支;
用命令: git brach 查看所有分支，当前分支前有个“*”号;
用命令：git checkout example      来切换到example分支
用命令：git merge example    把example分支的内容合并到当前分支
用命令：git branch -d example   删除example分支）（-D表示强行删除）

(2)解决冲突
命令：git log --graph --pretty=oneline --abbrev=commit
分支冲突或者本地与远程冲突;
当本地与远程冲突，你往远程推送失败的时候;
首先用命令  git pull把最新的提交更新下来，然后在本地合并，解决冲突之后，再推送;
如果还是失败，可以先用命令  git branch --set-upstream-to=origin/dev dev指定本地dev与远程origin/dev分支的链接,
在git pull

(3)分支管理策略
禁用Fast forward模式
在merge后加上参数 --no-of; 例如 git merger --no-off -m(-m参数表示提交) "此次提交的描述"  分支名

(4)bug分支
当出现bug的时候，但当前工作又未完成，可以用
命令:git stash 储存当前工作区未完成的工作.

修复bug后，用
命令:git stash pop	来恢复内容（可以多次stash，但恢复的时候，可以先用命令git shtash list查看，
再用git stash apply status@{0}来恢复）

rebase命令可以将提交历史变成一条干净的直线

9.标签管理
(1)创建标签
首先，切换到需要打标签的分支上
用命令：git tag <标签名(例如v1.0)>，可以用命令:git tag 查看所有标签(标签默认是打在最新的commit上)

给历史commit打标签：首先用 git log ...   查看所有commit id，然后用命令git tag <标签名> <commit id>打上标签

标签按字母顺序列出，可以用命令 git show <标签名> 查看标签 

(2)修改标签
如果打错标签，可以用命令:git tag -d <标签名>删除标签;
推送某个标签到远程： git push origin <标签名>;
推送全部标签到远程： git push origin --tags;
如果推送标签到远程错误，必须先删除本地标签，命令见上，再删除远程标签：git push origin :refs/tags/标签名
再登陆GitHub查看.

(3)使用git
进入作者仓库，点击右上边的fork按钮，就可以把作者的仓库克隆到你的远程仓库，再从远程仓库克隆到本地
(尽量不要直接从作者的仓库直接克隆到本地，这样你修改后将没有权限推送上去)

如果你希望bootstrap的官方库能接受你的修改，你就可以在GitHub上发起一个pull request.
当然，对方是否接受你的pull request就不一定了.(未练习)

(4)使用码云
当访问github网站太慢时，可以使用国内的Git托管服务--码云(gitee.com)(暂留)

10.自定义git
git config --global color.ui true  Git会适当地显示不同的颜色，比如git status命令

1.忽略特殊文件：(适用于放在git目录下，但又不能提交的文件，例如数据库配置文件)
方法：在Git工作区的根目录下新建一个.gitignore文件，然后把要忽略的文件名填进去，Git就会自动忽略掉这些文件

1,忽略操作系统自动生成的文件，比如缩略图等；
2,忽略编译生成的中间文件、可执行文件等，也就是如果一个文件是通过另一个文件自动生成的，那自动生成的文件就没必要放进版本库，比如Java编译产生的.class文件；
3,忽略你自己的带有敏感信息的配置文件，比如存放口令的配置文件

https://github.com/github/gitignore  这里可以查看需要忽略的一些文件(需自行整理)


强行添加文件到git，命令：git add -f 文件名
用命令 git check-ignore -v .gitignore 检查.gitignore文件规则是否有问题

2.配置别名
git config --global alias st status    将st作为status的别名
(global表示对当前用户起作用，如果不加global，那么配置的别名只对当前仓库起作用)
（也可以同时为多个单词取一个单词的别名，多个单词用单引号引起来）

如果要删除别名，可以打开.gitconfig文件夹，删除相应的行即可

git config --list --show-origin 可以查看相关配置文件以及文件内容

3.搭建git服务器（需要在Linux上搭建）

https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137583770360579bc4b458f044ce7afed3df579123eca000

另外，git学习笔记  Git Cheat Sheet

git英文官网：http://git-scm.com
