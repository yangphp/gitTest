# gitTest
git test 

##一：安装篇

安装包下载地址：https://gitforwindows.org/
官网慢，可以用国内的镜像：https://npm.taobao.org/mirrors/git-for-windows/。

下载后打开bash
输入 git --version 看是否有输出版本

全局设置名称和邮箱：
git config --global user.name "yangpeihao"
git config --global user.email "466146588@qq.com"

如果针对某个项目设置的话，去掉global即可
git config  user.name "yangpeihao"
git config  user.email "466146588@qq.com"

查看当前项目配置
git config --list

查看全局配置
git config --global --list

##二：创建版本库

创建版本库：
git init

git工作区：
就是你在电脑里能看到的目录

git暂存区：
英文叫 stage 或 index
一般存放在 .git 目录下的 index 文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。

版本库：
工作区有一个隐藏目录 .git，这个不算工作区，而是 Git 的版本库。

需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改

##三： 添加 和提交 文件 

添加工作区文件到暂存区
git add filename  			#添加filename文件到暂存区
git add . 		  			#添加当前目录下所有文件到暂存区 
git commit -m ' commit msg'   #提交暂存区内容到版本库

取消工作区的修改(未提交到暂存区或版本库)
git checkout -- filename  
注意：
a、git checkout -- filename 命令中的--很重要，没有--，就变成了“切换到另一个分支”的命令
b、只能针对某个文件取消工作区的修改 

取消暂存区的修改（已提交到暂存区，未提交到版本库）
git reset HEAD filename 
注意：取消暂存区的修改后，修改的内容仍然存在工作区，并不会消失，如果要取消工作区的修改，再执行
git checkout -- filename 

当执行 git checkout . 或者 git checkout -- <file> 命令时，
会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区中的改动。 

##四：删除文件 

1、从暂存区删除文件
git rm t3.txt 

2、提交删除到版本库，完成删除操作
git commit -m '提交删除文件 t3.txt'

##五、内容恢复

1、恢复工作区的修改(未提交到暂存区的文件)
git checkout -- filename  
注：不可恢复没有添加到缓存区的文件

2、恢复暂存区的修改（添加到缓存区但未提交到版本库）
git reset HEAD filename  
git checkout -- filename  
注：暂存区的恢复后，文件内容是不会改变的

3、恢复到某个版本

恢复到上个版本
git reset --hard HEAD^ 

恢复到上上个版本
git reset --hard HEAD^^

恢复到前100个版本
git reset --hard HEAD~100

恢复到某个版本
git reset --hard 473fb15dcda 

##六、相关查看命令

查看当前版本库的状态，显示有变更的文件
git status 

查看暂存区和工作区的差异
git diff 

查看某个文件暂存区和工作区的差异
git diff filename

查看暂存区和最后一次提交的差异
git diff --cached 

查看某个文件暂存区和最后一次提交的差异
git diff --cached filename

通过git log 查看当前的版本
git log 

通过 --pretty=oneline查看简介的日志
git log --pretty=oneline

查看分支合并情况
git log --graph --pretty=oneline --abbrev-commit

通过git reflog 可以看到每一个提交到版本库的命令
git reflog 

