---
layout: post
title:  "使用Git和Github管理你的项目"
date:   2011-04-27 03:49:27
categories: [Linux]
tags: [Linux, ssh, git, github, 公匙]
---

1、安装  sudo apt-get install git git-core2、git的初始设置  git config --global user.name "Your Name"  git config --global user.email miclle.zheng@gmail.com3、建立仓库  进入到项目目录。  git init  #这样在你的项目目录下就会有一个.git的隐藏目录（类似于.svn 但总个项目只会在项目根目录下有一个.git目录） 。4、初始化项目  git add .  #添加所有文件的情况，也可以添加特定的几个文件，比如git add README等等。  git commit -m 'first commit'  #-m 参数以及后面的字符串是添加说明信息。5、 注册github账号，创建项目！6、创建SSH密匙  ssh-keygen -C 'miclle.zheng@gmail.com'-t rsa  #确认使用默认路径，然后输入两次你要是用的密码就行，可以为空。  7、提交密匙  现在又要回到github的页面上，在“账户设置中”有一个“SSH 公匙”选择“添加新的公匙”。  填入标题，如"miclle@ubuntu"，或 "miclle.zheng@gmail.com"，work-pc都可以  公匙是刚刚上一步生成的一段代码  cd  #回到默认目录  cat .ssh/id_rsa.pub  #将里面的内容拷贝到“ 公匙”里，保存。  设置完成后可以通过下面命令测试连接  ssh -v git@github.com8、上传代码  git remote add origin git@github.com:miclle/test.git  git push -u origin master其它命令：创建和合并分支#git branch 显示当前分支是master 本地和远程合并，本地默认分支为master#git branch new-feature  创建分支# git checkout new-feature 切换到新分支提交到本地GIT# git commit -a -m "message..."合并到远程服务器# git push origin new-feature如果new-feature分支成熟了，觉得有必要合并进master#git checkout master更新本地master#git pull origin master合并new-feature#git merge new-feature更新至远程# git push origin master则master中也合并了new-feature 的代码