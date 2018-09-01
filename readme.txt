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
