Git is a distributed version control system.
Git is free software distributed under the GPL. 
Git is a very powerful tool.

感觉大家把简单问题复杂化了，看着头晕，

Git管理的文件分为：工作区，版本库，版本库又分为暂存区stage和暂存区分支master(仓库)

工作区>>>>暂存区>>>>仓库

git add把文件从工作区>>>>暂存区，git commit把文件从暂存区>>>>仓库，

git diff查看工作区和暂存区差异，

git diff --cached查看暂存区和仓库差异，

git diff HEAD 查看工作区和仓库的差异，

git add的反向命令git checkout，撤销工作区修改，即把暂存区最新版本转移到工作区，

git commit的反向命令git reset HEAD，就是把仓库最新版本转移到暂存区。
/*************************************************************/
远程服务器操作
https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes
/*************************************************************/
您可以运行git remote rename以更改遥控器的简称。例如，如果您想重命名pb为paul，则可以使用git remote rename：

$ git remote rename pb paul
$ git remote
origin
paul
值得一提的是，这也会更改您的所有远程跟踪分支名称。pb/master现在曾经在引用paul/master。

如果您出于某种原因要删除远程服务器（已移动服务器或不再使用特定的镜像，或者贡献者不再提供帮助），则可以使用git remote remove或git remote rm：

$ git remote remove paul
$ git remote
origin
以这种方式删除对远程的引用后，与该远程关联的所有远程跟踪分支和配置设置也将被删除。

当您要共享项目时，必须将其推向上游。该命令很简单：git push <remote> <branch>。如果要将master分支推送到origin服务器（同样，克隆通常会自动为您设置这两个名称），则可以运行此命令将已完成的所有提交推送回服务器：

$ git push origin master

我们已经提到并给出了一些有关git clone命令如何origin为您隐式添加遥控器的示例。这是显式添加新遥控器的方法。要将新的远程Git存储库添加为短名称，您可以轻松引用，请运行git remote add <shortname> <url>：

$ git remote
origin
$ git remote add pb https://github.com/paulboone/ticgit
$ git remote -v
origin  https://github.com/schacon/ticgit (fetch)
origin  https://github.com/schacon/ticgit (push)
pb  https://github.com/paulboone/ticgit (fetch)
pb  https://github.com/paulboone/ticgit (push)
现在，您可以pb在命令行上使用字符串代替整个URL。例如，如果您想获取Paul拥有但存储库中尚未拥有的所有信息，则可以运行git fetch pb：

$ git fetch pb
remote: Counting objects: 43, done.
remote: Compressing objects: 100% (36/36), done.
remote: Total 43 (delta 10), reused 31 (delta 5)
Unpacking objects: 100% (43/43), done.
From https://github.com/paulboone/ticgit
 * [new branch]      master     -> pb/master
 * [new branch]      ticgit     -> pb/ticgit