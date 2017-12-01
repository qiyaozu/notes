---
title: git学习
---

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
  git commit -m "#77 [ADD] ..."
  git checkout dev
  git checkout -b 新任务分支
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
