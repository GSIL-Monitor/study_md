### dd

---



####一. 前言

> 以前第一眼看到githug, 以为是把github拼错. 
>
> 见过了git, github, github pages, git workflow. 一定好奇githug是什么. 
>
> 原来... 是个游戏!  所以如果不玩一把, 就白当游戏玩家了. 
>
> 关于Git的学习, 大学时候写过一篇: [git小玩](http://www.xiefayang.com/2016/03/25/git%E5%B0%8F%E7%8E%A9/) . 
>
> 虽然很多IDE都有集成git插件, 在了解git命令和使用场景后再去使用IDE才会更加明白. 
>
> 甚至我认为很多操作使用git bash远比IDE更效率! 



---



#### 二. 介绍

当然, githug不是什么RPG, FPS之类的游戏. 

而是一个围绕git知识, 每一关都会帮你自动搭建好实验场景, 告诉你任务背景, 来完成这些关卡. 

其实这个跟github提供的在线练习很像, 但是我觉得githug更加好玩! 

* [git命令在线练习](https://try.github.io/levels/1/challenges/1)
* [git分支在线练习](https://learngitbranching.js.org/)

github地址: https://github.com/Gazler/githug

花了一天时间去通关. 当中也有去翻译和查通关攻略. 



---



#### 三. 安装使用

##### 1. 安装
首先, Githug可以使用在Linux, Windows, OS X下. 

我以 CentOS 7 为例: 

在安装Githug之前首先确认有Ruby环境. 

查看是否安装: ```ruby --version```

这里我选择自动安装的方式: ```sudo yum install ruby```

接着通过gem安装githug: ```gem install githug```

安装完成. 

##### 2. 使用

Githug只有四个游戏命令, 很简单: 

* ```githug play```: 开始玩, 会验证是否完成当前关卡, 完成则进入下一关(可缩写成```githug```), 

  没完成则会提示你并提示任务要求

* ```githug hint```: 给你一点当前关卡的提示

* ```githug reset```: 重置当前关卡

* ```githug levels```: 列出所有关卡

在第一次输入```githug```开始游戏时, 会提示```No githug directory found, do you wish to create one?```

意思要初始化一个游戏目录. 输入```y```即可创建. 

然后会出现一个git_hug目录, 以后所有关卡都会在该目录下生成文件和git对象. 每完成一关都会重新初始化游戏场景.

##### 3. 关卡列表

为了方便查看, 所以列出所有关卡. 这里摘抄一个极客学院的wiki. 

|                                          |                          |                    |
| ---------------------------------------- | :----------------------- | ------------------ |
| **关卡名称**                                 | **学习内容**                 | **Git 命令**         |
| [第1关 init](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-1.html) | 初始化仓库                    | git init           |
| [第2关 config](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-2.html) | 设置用户名和电子邮箱地址             | git config         |
| [第3关 add](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-3.html) | 把文件添加到暂存区                | git add            |
| [第4关 commit](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-4.html) | 提交                       | git commit         |
| [第5关 clone](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-5.html) | 克隆远程仓库                   | git clone          |
| [第6关 clone_to_folder](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-6.html) | 克隆远程仓库，并指定本地目录名          | git clone          |
| [第7关 ignore](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-7.html) | 配置不被 Git 管理的文件           | vim .gitignore     |
| [第8关 include](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-8.html) | 配置不被 Git 管理的文件           | vim .gitignore     |
| [第9关 status](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-9.html) | 查看仓库状态                   | git status         |
| [第10关 number_of_files_committed](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-10.html) | 查看仓库状态                   | git status         |
| [第11关 rm](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-11.html) | 删除文件                     | git rm             |
| [第12关 rm_cached](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-12.html) | 从暂存区中移除文件，系 git add 的逆操作 | git rm --cached    |
| [第13关 stash](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-13.html) | 保存而不提交                   | git stash          |
| [第14关 rename](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-14.html) | 文件改名                     | git mv             |
| [第15关 restructure](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-15.html) | 整理目录结构                   |                    |
| [第16关 log](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-16.html) | 查询日志                     | git log            |
| [第17关 tag](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-17.html) | 打标签                      | git tag            |
| [第18关 push_tags](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-18.html) | 把标签推送到远程仓库               | git push --tags    |
| [第19关 commit_amend](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-19.html) | 修改最后一次提交                 | git commit --amend |
| [第20关 commit_in_future](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-20.html) | 指定提交的日期                  | git commit --date  |
| [第21关 reset](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-21.html) | 从暂存区中移除文件，系 git add 的逆操作 | git reset          |
| [第22关 reset_soft](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-22.html) | 撤销提交，系 git commit 的逆操作   | git reset --soft   |
| [第23关 checkout_file](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-23.html) | 撤销对一个文件的修改               | git checkout       |
| [第24关 remote](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-24.html) | 查询远程仓库                   | git remote         |
| [第25关 remote_url](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-25.html) | 查询远程仓库的 URL              | git remote -v      |
| [第26关 pull](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-26.html) | 从远程仓库拉取更新                | git pull           |
| [第27关 remote_add](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-27.html) | 添加远程仓库                   | git remote         |
| [第28关 push](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-28.html) | 把提交推送到远程仓库               | git push           |
| [第29关 diff](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-29.html) | 查看文件被修改的细节               | git diff           |
| [第30关 blame](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-30.html) | 查询每一行代码被谁编辑过             | git blame          |
| [第31关 branch](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-31.html) | 创建分支                     | git branch         |
| [第32关 checkout](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-32.html) | 切换分支                     | git checkout       |
| [第33关 checkout_tag](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-33.html) | 切换到标签                    | git checkout       |
| [第34关 checkout_tag_over_branch](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-34.html) | 切换到标签                    | git checkout       |
| [第35关 branch_at](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-35.html) | 在指定的提交处创建分支              | git branch         |
| [第36关 delete_branch](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-36.html) | 删除分支                     | git branch -d      |
| [第37关 push_branch](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-37.html) | 推送分支到远程仓库                | git push           |
| [第38关 merge](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-38.html) | 合并分支                     | git merge          |
| [第39关 fetch](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-39.html) | 从远程仓库抓取数据                | git fetch          |
| [第40关 rebase](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-40.html) | 变基合并                     | git rebase         |
| [第41关 repack](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-41.html) | 重新打包                     | git repack         |
| [第42关 cherry-pick](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-42.html) | 合并分支上指定的提交               | git cherry-pick    |
| [第43关 grep](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-43.html) | 搜索文本                     | git grep           |
| [第44关 rename_commit](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-44.html) | 修改历史提交的说明                | git rebase -i      |
| [第45关 squash](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-45.html) | 把多次提交合并成一次提交             | git rebase -i      |
| [第46关 merge_squash](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-46.html) | 合并分支时把多次提交合并成一次提交        | git merge --squash |
| [第47关 reorder](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-47.html) | 调整提交顺序                   | git rebase -i      |
| [第48关 bisect](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-48.html) | 用二分法定位 bug               | git bisect         |
| [第49关 stage_lines](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-49.html) | 添加文件的部分行到暂存区             | git add --edit     |
| [第50关 file_old_branch](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-50.html) | 查看 Git 上的操作历史            | git reflog         |
| [第51关 revert](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-51.html) | 取消已推送到远程仓库的提交            | git revert         |
| [第52关 restore](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-52.html) | 恢复被删除的提交                 | git reset --hard   |
| [第53关 conflict](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-53.html) | 解决冲突                     |                    |
| [第54关 submodule](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-54.html) | 把第三方库当作子模块               | git submodule      |
| [第55关 contribute](http://wiki.jikexueyuan.com/project/githug-walkthrough/level-55.html) | 捐献                       |                    |



---



#### 四. 开始游戏



##### Level 1: init

> A new directory, `git_hug`, has been created; initialize an empty repository in it.
>
> 在```git_hug```目录下初始化一个仓库

```shell
[root@pipeline-cloud-test02 git_hug]# git init
Initialized empty Git repository in /home/githug/git_hug/.git/
[root@pipeline-cloud-test02 git_hug]# ls -a
.  ..  .git  .gitignore  .profile.yml
[root@pipeline-cloud-test02 git_hug]# githug
Congratulations, you have solved the level!
```

空目录和有文件的目录都可以初始化, 可以看到隐藏文件```.git```, 如同```.svn```一样. 该目录会被git所管理. 



##### Level 2: config

> Set up your git name and email, this is important so that your commits can be identified.
>
> 配置用户名和邮箱是为了提交代码时的团队标识

```
[root@pipeline-cloud-test02 git_hug]# git config --add user.name thank
[root@pipeline-cloud-test02 git_hug]# git config --add user.email coderthank@163.com
[root@pipeline-cloud-test02 git_hug]# githug
********************************************************************************
*                                    Githug                                    *
********************************************************************************
What is your name? thank
What is your email? coderthank@163.com
Your config has the following name: thank
Your config has the following email: coderthank@163.com
Congratulations, you have solved the level!
```

**补充**: 

```shell
git config --add [--global/--local] user.name xxx # 增加name配置信息
git config --get [--global/--local] user.name xxx # 查看name配置信息
# --global/--local参数用来表示是全局配置还是本地配置
# email的话换成user.email

git config –list # 查看git全局配置
```

当然, 有配置就会有配置的记录文件. 你可以到```~/.gitconfig```去编辑配置信息



##### Level 3: add

> There is a file in your folder called 'README', you should add it to your staging area.
>
> 添加README文件到暂存区

```shell
[root@pipeline-cloud-test02 git_hug]# git add README
[root@pipeline-cloud-test02 git_hug]# githug
********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

```



**补充:**

首先补充一个图:

 ![man](http://img.blog.csdn.net/20160325192928814?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

关于这三个工作区域:

* History 也可以叫repository(git仓库): 最终确定的文件能保存到仓库, 成为一个新的版本, 并且对他人可见
* Staging area (暂存区,Cache, Index): 暂存已经修改的文件
* Working directory(工作区):  也就是你实际看见的工作目录



##### Level 4: add

> The 'README' file has been added to your staging area, now commit it.
>
> 把暂存区的README文件提交

```shell
[root@pipeline-cloud-test02 git_hug]# git commit -m "add README file"
[master (root-commit) a3317a2] add README file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README
[root@pipeline-cloud-test02 git_hug]# githug
********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

```





##### Level 5: clone

> Clone the repository at <https://github.com/Gazler/cloneme>.

```shell
[root@pipeline-cloud-test02 git_hug]# git clone https://github.com/Gazler/cloneme
Cloning into 'cloneme'...
remote: Counting objects: 7, done.
remote: Total 7 (delta 0), reused 0 (delta 0), pack-reused 7
Unpacking objects: 100% (7/7), done.
[root@pipeline-cloud-test02 git_hug]# githug
********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

```

回一下第1关, 可以总结下创建git仓库大致有两种: ```git init```初始化和```git clone```克隆远程git项目



##### Level 6: clone

> Clone the repository at <https://github.com/Gazler/cloneme> to 'my_cloned_repo'.
>
> 还是克隆远程git项目, 只不过换个名字

```
[root@pipeline-cloud-test02 git_hug]# git clone  https://github.com/Gazler/cloneme my_cloned_repo
Cloning into 'my_cloned_repo'...
remote: Counting objects: 7, done.
remote: Total 7 (delta 0), reused 0 (delta 0), pack-reused 7
Unpacking objects: 100% (7/7), done.
[root@pipeline-cloud-test02 git_hug]# githug
********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

```



##### Level 7: ignore

> The text editor 'vim' creates files ending in '.swp' (swap files) for all files that are currently open. We don't want them creeping into the repository. Make this repository ignore '.swp' files.
>
> 有些零食文件什么的不需要git来管理. 忽略他们

```shell
[root@pipeline-cloud-test02 git_hug]# ls -a
.  ..  .git  .gitignore  .profile.yml  README.swp
[root@pipeline-cloud-test02 git_hug]# vim .gitignore
[root@pipeline-cloud-test02 git_hug]# more .gitignore
.profile.yml
.gitignore
*.swp
[root@pipeline-cloud-test02 git_hug]# githug
********************************************************************************
*                                    Githug                                    *
********************************************************************************
Congratulations, you have solved the level!

```

```.gitignore``` 在仓库的根目录下, 用于配置可忽略文件的规则



Level 7: ignore

41关rebase -onto参考: http://blog.csdn.net/huitailang1991/article/details/54289701