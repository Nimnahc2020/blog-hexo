---
title: 命令笔记- Git
top: 21
essential: true
dropCap: false
cover: false
toc: true
mathjax: false
date: 2020-04-21 22:10:30
author: ruchan
summary: 笔记 
tags: 
  - Command
  - Git
  - 探索学习
categories: Command
---

时光流淌，记忆总要模糊淡去。
我写博客的一个初衷本来便是记录：记录学习，记录生活。

<!-- more -->

博客能让我这三分热度且健忘的人保留一份存档。它能让我在写的过程中审视自身的收获，在写完后的某一天重拾这份收获。
同时，它也能让我的收获帮助需要它的人。

本文记录一些对我而言较为常用的 git 命令。

## Git命令

1. 通过 Git 新建代码库（仓库）
```C
$ git init						# 在当前目录新建一个Git代码库 
$ git init [project-name]		# 新建一个目录，将其初始化为Git代码库
$ git clone [远程仓库地址]		# 下载一个项目和它的整个代码历史
```
2. 配置代码库（本地仓库）[^1]
```C
$ git config --list			# 显示当前的Git配置
$ git config user.name		# 查看配置的用户名
$ git config user.email		# 查看配置的用户邮箱

# 设置提交代码时的用户信息（此设置为全局设置）
$ git config --global user.name [userA]		
$ git config --global user.email [userA@Email.com]

# 取消全局（global）用户信息设置
$ git config --global --unset user.name
$ git config --global --unset user.email

# 可设置每个项目仓库的独立用户信息（需进入到项目的根目录中）
$ git config  user.name [userA]
$ git config  user.email [userA@Email.com]
```
..注意..:代码库配置是本地仓库与远程仓库链接过程中极为重要的一环。
Git 相关配置保存在`.gitconfig`文件中，全局配置的`.gitconfig`会在 C 盘用户目录下，本地仓库的 Git 配置文件`.gitconfig`则位于经`git init`生成的`.git`文件夹下（`.git`文件会被隐藏）。

3. 链接远程仓库
```C
$ git remote -v						# 显示所有远程仓库
$ git remote add [远程仓库地址]		# 增加一个新的远程仓库
$ git remote remove [远程仓库名称]	# 删除远程仓库的关联
$ git remote set-url origin [新的远程仓库地址]	# 修改远程仓库的关联
```
4. 熟悉 Git 流程
```C
$ git status	# 显示文件状态
$ git add .		# 将文件从工作目录添加至暂存区
$ git add -A	# 将文件从工作目录添加至暂存区
$ git commit -m "message"	# "message"是本次提交的简述内容
```
5. 将本地..新建的..项目提交到远程仓库
```C
$ git init		# 初始化本地仓库
$ git add .		# 将本地内容添加至 Git 本地暂存区中
$ git commit -m "first commit"	# 将暂存区添加至本地仓库中
$ git remote add origin [远程仓库地址]	# 添加远程仓库路径
$ git push -u origin master		# 将本地内容上传至远程仓库
```
`git push -u origin master`后若提示输入`git pull`，那便先`git pull `，然后`git push origin master -f`即可成功。

6. 更新仓库文件
```C
# 进入本地仓库根目录：
$ git status
$ git add -A
$ git commit -a -m "message"
$ git push origin master -f
```
7. 删除远程仓库某文件
```C
git rm -r --cached [文件名称]	#取消对该文件的追踪
```
然后`git pull`即可。

## 参考文章
<a href="https://www.jianshu.com/p/cdccfef91ae1" class="LinkCard">简书 | Git常用命令总结</a>
<a href="https://www.jianshu.com/p/b0dbc71497ff" class="LinkCard">简书 | 如何上传本地文件（夹）至GitHub及更新仓库文件</a>

[^1]: 可直接编辑`.gitconfig`文件