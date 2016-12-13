## 创建版本库
	$ git init # 初始化
	$ git add readme.txt # 将readme.txt添加到仓库
	$ git add . # 将该目录下所有文件添加到仓库
	$ git commit -m "wrote a readme file" # 将文件提交到仓库

## 版本修改
	$ git status # 查看工作区的状态
	$ git diff readme.txt # 查看具体文件修改
	$ git log # 显示从最近到最远的提交日志
	$ git log --pretty=oneline
	$ git reset --hard HEAD^ # 回退到上一个版本
	$ git reflog # 查看每一次命令
	$ git diff HEAD -- readme.txt # 查看工作区和版本库的区别
	$ git checkout -- file # 用版本库里的版本替换工作区的版本
	$ git reset HEAD file # 撤销掉当前版本暂存区的修改
	$ git rm test.txt # 从版本库中删除文件

## 远程仓库
	$ ssh-keygen -t rsa -C "youremail@example.com" # 创建SSH Key
	$ git remote add origin git@github.com:michaelliao/learngit.git # 关联远程仓库
	$ git push -u origin master # 把当前分支master推送到远程仓库
	$ git clone git@github.com:michaelliao/gitskills.git # 克隆到本地仓库
	$ git remote show <主机名> # 查看该主机的详细信息
	$ git remote rm <主机名> # 删除远程主机
	$ git remote rename <原主机名> <新主机名> # 用于远程主机的改名
	$ git fetch <远程主机名> # 将某个远程主机的更新，全部取回本地
	$ git fetch <远程主机名> <分支名> # 取回特定分支的更新
	$ git branch -a # git branch命令的-r选项，可以用来查看远程分支，-a选项查看所有分支
	$ git branch -r
	$ git checkout -b newBrach origin/master ＃　在origin/master的基础上，创建一个新分支
	$ git merge origin/master　 # 在本地分支上合并远程分支。
	$ git pull <远程主机名> <远程分支名>:<本地分支名> # 取回远程主机某个分支的更新，再与本地的指定分支合并
	$ git branch --set-upstream master origin/next # 指定master分支追踪origin/next分支
	
	
## 分支管理
	$ git checkout -b dev # 创建dev分支，然后切换到dev分支
	$ git branch dev # 切换到dev分支
	$ git branch # 查看当前分支
	$ git merge dev # 把dev分支合并到master分支上
	$ git branch -d dev # 删除dev分支
	$ git log --graph --pretty=oneline --abbrev-commit # 查看分支合并情况
	$ git merge --no-ff -m "merge with no-ff" dev # 禁用Fast forward合并分支
	$ git stash # 隐藏工作现场
	$ git stash list # 查看隐藏列表
	$ git stash pop # 恢复并删除stash列表
	$ git stash apply stash@{0} # 回复指定stash
	$ git stash drop # 删除stash
	$ git branch -D feature-vulcan # 强行删除分支

	$ git remote # 查看远程库的信息
	$ git remote -v # 显示更详细的信息 
	$ git push origin dev # 推送制定分支
	$ git pull # 抓取最新提交
	$ git branch --set-upstream dev origin/dev # 设置dev和origin/dev的链接

## 标签管理
	$ git tag v1.0 # 打一个新标签
	$ git tag # 查看所有标签
	$ git tag v0.9 6224937 # 对指定提交打标签
	$ git show v0.9 # 查看标签信息
	$ git tag -a v0.1 -m "version 0.1 released" 3628164 # 创建带有说明的标签，用-a指定标签名，-m指定说明文字
	$ git tag -s v0.2 -m "signed version 0.2 released" fec145a
 # 通过-s用私钥签名一个标签
	$ git tag -d v0.1 # 删除标签
	$ git push origin v1.0 # 推送标签到远程仓库
	$ git push origin --tags # 一次性推送全部尚未推送到远程的本地标签
	$ git push origin :refs/tags/v0.9＃　远程删除某标签

## git pull时出现冲突 放弃本地修改，使远程库内容强制覆盖本地代码
	$ git fetch --all //只是下载代码到本地，不进行合并操作
	$ git reset --hard origin/master  //把HEAD指向最新下载的版本
	
	
	




















