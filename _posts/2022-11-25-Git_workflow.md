---
title: GitHub工作流
tags: 杂项
mathjax: true
mode: immersive
comment: true
pageview: true
key: A2301
header:
  theme: dark
article_header:
  type: cover
  image:
    src: //photos/mounts.jpg






---


* content
{:toc}






# github工作流

1. 将远程GitHub仓库使用`git clone`命令到本地
2. `git checkout -b my_branch`本地建立一个新的分支*my_branch*，代码改动不会影响到main分支
3. 在新的分支*my_branch*中修改代码，使用`git diff`命令查看修改情况
4. 使用`git add <changed_name>`将需要commit的代码放入暂存区
5. 使用`git commit`命令将修改的代码放到本地git
6. 使用`git push origin my_branch`将本地分支提交到GitHub中
7. 若此时发现main分支中的代码更新了，需要将main分支中的改动同步到*my_branch*分支中
8. 本地main分支与远端GitHub仓库中的main分支不一致，使用`git checkout main`命令切换到main分支
9. 使用`git pull origin main`命令更新本地main分支
10. 再使用`git checkout my_branch`命令切换到*my_branch*分支
11. 使用`git rebase main`命令将main中的改动同步到分支中，同步时可能会与当前分支的改动产生冲突
12. 手动选择需要保留哪一份改动，rebase成功之后，相当于在最新的main分支上添加了自己的改动
13. 更新完本地分支后，使用`git push origin my_branch`命令再次将本地分支提交到GitHub
14. 通过pull request将GitHub上的新分支合并到main分支中
15. 面对pull request使用squash and merge将分支上的所有改变合并成一个改变，将commit放到main分支中
16. 此时可以将远端GitHub仓库中的my_branch分支使用delete branch删除
17. 本地使用`git checkout main`切换到main分支中，使用`git branch -D my_branch`将本地的my_branch分支删除
18. 再使用`git pull origin main`命令更新本地main分支

