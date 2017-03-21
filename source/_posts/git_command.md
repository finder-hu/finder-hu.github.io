---
title: git 命令总结
categories:
- git
date: 2017-02-09 18:40:52
---
### 基本操作
|命令|说明|
|:---|:---|
|git init| 初始化一个git项目|
|git add fileName <br/> git add directoryName	|	不同情况下功能不同，分别有：<br/>1. 开始追踪新文件。逆操作为git rm fileName。<br/> 2. 添加文件或者是文件夹下面已追踪的的文件变动到暂存区。逆操作为git reset HEAD fileName.<br/>3. 合并时把有冲突的文件标记为已解决状态。|
|git rm fileName|	不追踪文件fileName.|
|git reset HEAD fileName| 取消暂存文件fileName。|
|git checkout -- fileName| 忽略文件fileName的变动。|
|git status | 查看当前分支的状态|
|git diff	|查看文件改动的具体内容|

### 版本操作
|命令|说明|
|:---|:---|
|git commit -m "message"|	提交暂存区的文件到本地仓库|
|git commit -m "init message"<br/> git add forgoten_file <br/> git comit -amend|	在commit之后发现还有文件未添加，添加未添加的文件，然后运行git commit -amend 则只会有一次commit信息。|


git reset --hard HEAD^	退货到上一次提交的版本
git reset --hard HEAD^^	退货到上上一次提交的版本
git reset --hard hashcode	跳到hashcode指定的版本，hashcode可以为前几个数字，一般4、5个即可。
3. 日志
git log 	列出所有历史记录的详细信息
git log -n	前n条详细信息
git log --graph	显示提交历史图
git log --pretty=oneline	每次提交显示在一行
git log --pretty=format:"%h - %an, %ar : %s"	定制化显示格式
git reflog
4. 克隆远端仓库到本地
git clone git@github.com:userName/projectName.git	克隆远端仓库到本地，并在本地创建master分支，该master分支追踪远端仓库origin/master分支
git clone git@github.com:userName/projectName.git -b dev	克隆远端仓库到本地，并在本地创建dev分支，该dev分支追踪远端仓库origin/dev分支。
5. 远端仓库操作
git remote -v	查看远端仓库
git remote add [name][url]	添加远端仓库
git remote rm [name]	删除远端仓库
git remote set-url --push [nam][newUrl]	修改远端仓库
6. 分支管理
• 本地分支
git branch	查看本地分支
git branch -a	查看所有分支包括远端分支
git branch [name]	创建本地分支
git checkout -b dev origin/dev	创建本地分支dev，切换到dev分支，该dev分支追踪远端分支origin/dev
git checkout -b [name]	创建并切换到新分支
git chekcout [name]	切换分支
git branch -d [name]	删除已经合并的分支
git branch -D [name]	强制删除
• 远端分支
git branch -r	查看远程分支
git push origin branchName	创建远程分支
git push origin --delete branchName	删除远程分支
• 追踪远端分支
git checkout --track origin/dev	使当前分支追踪远端分支origin/dev
• 拉取和提交
git pull	拉取远端分支内容并与本地分支合并。
git push	推送本地分支内容到远端分支。
• 合并分支
git merge brancName	合并分支branchName到当前分支。
• 变基分支
git rebase branchName	变基分支branchName到当前分支。


#### 参考资料
1. [官方文档](https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E6%9F%A5%E7%9C%8B%E6%8F%90%E4%BA%A4%E5%8E%86%E5%8F%B2)
2. [廖晓峰教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
