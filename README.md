# Git使用总结

### 远程仓库创建
```sh
$ git init  								#创建本地仓库
$ echo "# git-summary" >> README.md  					#创建说明
$ git add README.md 							#添加本地文件
$ git commit -m "first commit"   					#添加提交说明
$ git remote add origin https://github.com/codeLee321/git-summary.git 	#关联远程仓库
$ git push --set-upstream origin master  				#将本地文件推向远程仓库
$ git push -u origin master 						#强推
```
### 分支管理

##
```sh
$ git checkout -b dev 							#-b参数表示创建并切换分支
$ git branch								#查看当前分支
chongtuceshi
```
