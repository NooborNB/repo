1.安装完git之后

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
命令:git push -u orgin master

再点击repository,就可以看到本地的内容已经同步上去了.

接下来，只要本地有提交，就可以通过
命令:git push origin master  把本地master分支的最新修改推送到Github.

3.从远程库克隆到本地
首先自己创建一个远程库(模拟你要克隆的库),创建的时候初始化;
接下来在本第git客户端运行命令
git clone git@github.com:github用户名/要克隆的库名.git

8.分支管理
（1）创建与合并分支
用命令: git checkout -b example   创建并转到example分支;
用命令: git brach 查看所有分支，当前分支前有个“*”号;
用命令：git checkout example      来切换到example分支
用命令：git merge example    把example分支的内容合并到当前分支
用命令：git branch -d example   删除example分支

（2）解决冲突

