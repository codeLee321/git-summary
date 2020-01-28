# Git使用总结

### 用户信息配置
```sh
$ git config --list [--local|worktree|global|system]                    #查看git配置信息
$ git config --show-origin user.name                                    #查看某条配置信息的源文件
$ git config --global user.name glorylee                                #设置用户名
$ git config --global user.email dennisglorylee@gmail.com               #设置用户邮箱
$ git config --global alias.hist 'log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short' #像这种比较长的git命令，可以通过别名设置来简化：git hist

```
### 远程仓库创建&变更提交
```sh
$ git init  								#创建本地仓库
$ echo "# git-summary" >> README.md  					#创建说明
$ git add README.md 							#添加本地文件
$ git commit -m "first commit"   					#添加提交说明
$ git commit -am "add and commit"   					#添加变更并提交
$ git commit --amend   					                #修正上次提交            
$ git remote add origin https://github.com/codeLee321/git-summary.git 	#关联远程仓库
$ git push --set-upstream origin master  				#将本地文件推向远程仓库
$ git push -u origin master 						#效果同上
$ git push -f								#强推
$ git branch --set-upstream-to=origin/dev dev				#指定本地dev分支与远程dev分支链接
$ git remote								#查看远程库的信息
$ git remote -v								#查看更多的远程库的信息
$ git clone https://github.com/codeLee321/git-summary			#从远程仓库clone
```
### 分支管理

1.创建/删除/合并分支
```sh
$ git checkout -b dev 							#-b参数表示创建并切换分支
$ git branch								#查看当前分支
$ git checkout master							#切到master分支
$ git merge dev								#将dev分支合并到当前分支
$ git branch -d dev 							#删除dev分支
$ git branch -D dev 							#强制删除dev分支

#高版本git提供switch
$ git switch -c dev							#创建并切换分支
$ git switch master							#切到master分支
```
2.冲突解决
```sh
$ git status								#查看当前分支状态以及文件冲突
$ git log --graph --pretty=oneline --abbrev-commit			#查看合并记录
$ git merge --no-ff -m "merge with no-ff" dev				#合并禁用Fast forward
```
3.保存/恢复分支变更
```sh
$ git stash								#保存当前分支的变更
$ git stash list							#查看保存的列表
$ git stash apply							#恢复保存的变更，但是不删除stash中的内容
$ git stash drop							#删除stash中的内容
$ git stash pop								#恢复保存的变更，同时删除stash中的内容

#复制某次提交，注意：如果复制了这次变更再merge就会出现冲突
#因为同时更改了相同的文件
$ git cherry-pick 4c805e2						#可以将提交变更直接复制到另一个分支上面
```

### 版本控制
```sh
$ git reset --hard HEAD^						#回退到上一次的提交版本
$ git reset --hard 64b640d6c66088238e4fb6b01ae140e639bf0e6c		#回退到某次特定提交
$ git reflog								#记录每一次的命令
$ git diff HEAD -- README.md						#工作区与远程库README.md文件的区别
$ git checkout -- README.md						#撤销当前文件的修改
$ git rm README.md							#删除某个文件
```
### 标签管理
```sh
$ git tag v1.0								#打一个标签
$ git tag v0.9 f52c633							#给某次提交打上标签
$ git tag								#查看标签
$ git tag -a v0.1 -m "version 0.1 released" 1094adb			#打标签系列操作
$ git show v1.0								#查看某个标签的描述信息
$ git tag -d v0.1							#删除某个标签
$ git push origin :refs/tags/v0.9					#执行此操作使上面的删除操作推到远程库
$ git push origin v1.0							#推送某个标签到远程
$ git push origin --tags						#一次性推送全部尚未推送到远程的本地标签
```
### 文件跟踪
```sh
$ git log -p ./path         #跟踪某个文件的变更记录
```
