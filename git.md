---
title: git学习
---
# git学习

## 克隆远程仓库

  git clone xxxxx.git/https://xxxx

## 生成.git文件

  git init

## 然后自己去修改一些东西

  git status    // 查看哪些文件被修改，或者增加删除了哪些文件
  git diff      // 查看本地与暂存区的不同
  git diff master origin/master  // 查看本地与远程的不同

## 将本地的修改添加到暂存区

  git add .    // 将本地所有的修改都添加进去
  git add xxx  // 将某个文件添加到暂存区

## 如果中间发现有些东西不能提交， 想反悔

  git reset .   // 把暂存区都反悔  后面还能添加别的参数，需要度娘

## 添加一个本次更改了什么内容，也就是说明

  > 如果没有没有传更改内容的话，会弹出一个vim界面让你确定是不是真的不用提交参数
  > https://www.cnblogs.com/yangjig/p/6014198.html 常用的vim命令
  git commit -m "[FIX] [MRG] [ADD] #这里填写提交的内容"

### 把本地和远程仓库关联起来

  git remote add origin xxxxxx.git

### 提交到远程

  假如远程和本地有多个分支
  本地： git branch
  远程： git branch -a

  首次： git push -u origin master  // 提交到远程的哪个分支
  以后： git push

### 查看一个文件修改了哪些内容：

  git log -p filename

### 查看最近的提交

  git log
  git log -p -10    // -p显示最近提交的内容更改  -10最近十条记录
  git log -100      // 显示最近提交的100条记录

### 实际开发中的版本控制

* 接到任务后，先把本地的dev更新到最新（前提是本地的dev是主角儿）
* 创建一个分支，分支的命名和任务要相关，方便以后好切换
* 如果这个任务还没完   又接到了一个紧急的任务   就要先把没完成的任务先暂存起来

  git add -u          //把本地修改添加到缓存
  git reset .         // 撤销add的提交

  git commit -m "#77 [ADD] ..."
  git checkout .      // 撤销所有的commit
  
  git branch dev
  git branch -b 新任务分支
* 紧急任务处理完之后 切换到没有完成任务的分支上面    继续干活

###  commit 但还没push

  git log    //查看提交的ID
  git reset --hard commit_id   //完成撤销,同时将代码恢复到前一commit_id 对应的版本。
  git reset commit_id   //完成撤销,但不对代码进行修改

### 想修改commit的内容

  git commit --amend

### 撤销指定的提交

  git revert <commit_id>

### 撤销指定文件的修改

  git checkout <filename>

### refusing to merge unrelated histories  版本是2.13.0，网上说2.9.0之前的才会出现这种事，结果代码传码云的时候就出现了，解决方式：

```code
git pull origin master --allow-unrelated-histories
```

### 如果每次提交的时候都要输入用户名和密码

因为之前添加remote的时候，添加的是https的   不是ssh

1. 先把本地的origin删除掉

```code
 git remote rm origin
```

1. 重新添加
  
```code
git remote add origin xxxxxx.ssh
```

### git默认是不区分文件名大小写的，如果要区分，需要
```
git config core.ignorecase false
```

### git删除远端的文件/文件夹
```
1. 删文件
git rm -r --cached dir/file.txt
2. 删文件夹
git rm -r --cached dir

git commit -m "删除远程文件/文件夹"
git push
```