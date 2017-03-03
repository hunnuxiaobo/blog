##基本命令：
1. 克隆
>git clone https://blog.github.com/blog.git

2. 添加
>git add .

3. 提交
>git commit -m "我是注释"

4. 推送
>git push

5. 拉取
>git pull

6. 恢复
恢复某个已修改的文件（撤销未提交的修改）：
>$ git checkout file-name
例如：git checkout src/com/Android/.../xxx.Java
比如修改的都是java文件，不必一个个撤销，可以使用
>$ git checkout *.java
撤销所有修改
>$ git checkout .

7. git revert
撤销某次操作，此次操作之前和之后的commit和history都会保留，并且把这次撤销
作为一次最新的提交
    * git revert HEAD                  撤销前一次 commit
    * git revert HEAD^               撤销前前一次 commit
    * git revert commit-id （比如：fa042ce57ebbe5bb9c8db709f719cec2c58ee7ff）撤销指定的版本，撤销也会作为一次提交进行保存。
git revert是提交一个新的版本，将需要revert的版本的内容再反向修改回去，版本会递增，不影响之前提交的内容

##分支：
##master,beta,prod
```
git branch beta  #创建分支beta
git checkout beta #切换到分支beta

李银银 2016/12/8 15:58:10
git pull --all
git tag ts_v0.3 beta
git push origin ts_v0.3
git checkout beta
git merge master
git push --all
git tag
```

##分支操作

1. 列出所有本地分支
$ git branch

2. 列出所有远程分支
$ git branch -r

3. 列出所有本地分支和远程分支
$ git branch -a

4. 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]
例如，创建名称为dev的分支：
$ git branch dev

5. 新建一个分支，并切换到该分支
$ git checkout -b [branch]
例如，创建名称为dev的分支并切换到该分支上
$ git checkout -b dev

6. 切换到指定分支，并更新工作区
$ git checkout [branch-name]
例如，切换到dev分支上
$ git checkout dev

7. 合并指定分支到当前分支
$ git merge [branch]
例如，当前在master分支上，将dev分支合并到当前master分支上来
$ git merge dev

8. 删除分支
$ git branch -d [branch-name]
例如，删除本地dev分支
$ git branch -d dev

9. 将本地分支推送到远程服务器
10. 删除远程分支
$ git push origin --delete <branchName>
例如，删除远程的dev分支
$ git push origin --delete dev
否则，可以使用这种语法，推送一个空分支到远程分支，其实就相当于删除远程分支：
$ git branch -d <branchName>
$ git push origin :<branchName>

##标签（tag）操作
1. 列出所有tag
$ git tag

2. 打轻量标签
$ git tag [tag name]

3. 附注标签
$ git tag -a [tag name] -m [message]
例如，打v1.0标签
$ git tag -a v1.0 -m 'v1.0 release'

4. 后期打标签
$ git tag -a [tag name] [version]

5. 删除本地tag
$ git tag -d [tag]
例如，删除本地v1.0 标签
$ git tag -d v1.0

6. 删除远程tag
$ git push origin --delete tag <tagname>
还有另外一种方式来删除，推送一个空tag到远程
$ git tag -d <tagname>
$ git push origin :refs/tags/<tagname>

7. 查看tag信息
$ git show [tag]

9. 提交指定tag
$ git push [remote] [tag]
例如，将v1.0标签推送到远程服务器上
$ git push origin v1.0

10. 提交所有tag
$ git push [remote] --tags
重命名远程分支
在Git中重命名远程分支，其实就是先删除远程分支，然后重命名本地分支，再重新提交一个远程分支。
例如，把远程分支dev重命名为develop，操作如下：
1.删除远程分支：
$ git push --delete origin dev
2.重命名本地分支：
git branch -m dev develop
3.推送本地分支：
$ git push origin develop