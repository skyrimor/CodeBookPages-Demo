#### 创建仓库

```bash
# 初始化
$ git init 
# 当前目录加入到仓库
$ git add .
# 提交到仓库
$ git commit -m "xxx" 
# 关联远程仓库
$ git remote add origin https://github.com/xxx/xxx
$ git remote add origin git@gitee.com:skyrimor/spring-boot-scheduling-master.git
# 推送到远程库上
$ git push -u origin master
# 查看目录
$ ls
```

由于远程库是空的，第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送到远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来

```bash
$ git push origin master
```

#### 日常操作

```bash
# 暂存工作区
$ git stash
# 拉取git上最新的代码
$ git pul
# 恢复暂存工作区
$ git stash apply
# 查看状态
$ git status
# 添加文件
$ git add
# 提交
$ git commit -m ""
# 查看状态
$ git status
# 推送
$ git push
```

#### 远程仓库

```bash
# 显示远程仓库信息
$ git remote
# 更新远程仓储
$ git remote update
# 下载远程仓库的所有变动
$ git fetch [remote]
# 显示所有远程仓库
$ git remote -v
# 显示某个远程仓库的信息
$ git remote show [remote]
# 增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]
```

#### 同步

```bash
# 取回远程仓库的变化，并与本地分支合并
$ git pull [remote] [branch]
# 上传本地指定分支到远程仓库
$ git push [remote] [branch]
# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force
# 推送所有分支到远程仓库
$ git push [remote] --all
```

#### 分支

```bash
# 查看分支，会列出所有分支，当前分支前面会标一个`*`号
$ git branch
# 列出所有远程分支
$ git branch -r
# 创建分支
$ git branch <name>
# 切换分支
$ git checkout master
# 创建并切换分支
$ git checkout -b <name>
# 合并分支
$ git merge dev
# 删除分支
$ git branch -d <name>
# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
# 拉取远程新建的分支
$ git remote update origin --prune
# 分支合并图
$ git log --graph
# 禁用`Fast forward`模式
$ git merge --no-ff -m "merge with no-ff" dev
```

通常，合并分支时，如果可能，Git会用`Fast forward`模式，但这种模式下，删除分支后会丢掉分支信息。强制禁用`Fast forward`模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。

#### 文件操作

```bash
# 添加文件，并添加到暂存区
$ git add
# 删除文件，并且将这次删除放入暂存区
$ git rm 
# 停止追踪指定文件，但该文件会保留在工作区
$ git rm --cached [file]
# 改名文件，并且将这个改名放入暂存区
$ git mv 
```

#### 文件对比

```bash
# 尚未缓存的改动
$ git diff
# 查看已缓存的改动
$ git diff --cached
# 查看已缓存的与未缓存的所有改动：
$ git diff HEAD
# 显示摘要而非整个diff
$ git diff --stat
# 显示两次提交之间的差异
$ git diff [first-branch]...[second-branch]
# 显示某次提交的元数据和内容变化
$ git show [commit]
# 显示某次提交发生变化的文件
$ git show --name-only [commit]
# 显示某次提交时，某个文件的内容
$ git show [commit]:[filename]
# 显示当前分支的最近几次提交
$ git reflog
```

#### 撤销操作

```bash
# 恢复暂存区的指定文件到工作区
$ git checkout [file]
# 恢复某个commit的指定文件到暂存区和工作区
$ git checkout [commit] [file]
# 恢复暂存区的所有文件到工作区
$ git checkout .
# 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
$ git reset [file]
# 重置暂存区与工作区，与上一次commit保持一致
$ git reset --hard
# 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
$ git reset [commit]
# 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
$ git reset --hard [commit]
# 重置当前HEAD为指定commit，但保持暂存区和工作区不变
$ git reset --keep [commit]
# 新建一个commit，用来撤销指定commit
# 后者的所有变化都将被前者抵消，并且应用到当前分支
$ git revert [commit]
```

#### 查看信息

```bash
# 显示仓库状态
$ git status
# 查看历史记录
$ git log
# 如果输出信息太多，可以增加参数
$ git log --pretty=oneline
# 显示commit历史，以及每次commit发生变更的文件
$ git log --stat
# 搜索提交历史，根据关键词
$ git log -S [keyword]
# 显示某个commit之后的所有变动，每个commit占据一行
$ git log [tag] HEAD --pretty=format:%s
# 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
$ git log [tag] HEAD --grep feature
# 显示某个文件的版本历史，包括文件改名
$ git log --follow [file]
$ git whatchanged [file]
# 显示指定文件相关的每一次diff
$ git log -p [file]
# 显示过去5次提交
$ git log -5 --pretty --oneline
# 显示所有提交过的用户，按提交次数排序
$ git shortlog -sn
# 显示指定文件是什么人在什么时间修改过
$ git blame [file]
```

#### 版本回退

Git必须知道当前版本是哪个版本，在Git中，用`HEAD`表示当前版本，上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，同理前n个版本为HEAD~n。

```bash
# 使用下面命令回退到具体版本
$ git reset --hard HEAD^
$ git reset --hard HEAD~n
# 也可以使用 git reset --hard  id 命令到任一指定版本，版本号没必要写全，前几位就可以了，Git会自动去找
$ git reset --hard xxx
# 回退后提交
$ git push -u origin master --force

效果
原版记录 007 006 005 004 003 002 001 
回退到 005 
现版本记录 005 004 003 002 001 
```

（Git的版本回退速度非常快，因为Git在内部有个指向当前版本的`HEAD`指针，当你回退版本的时候，Git仅仅是把HEAD从指向xxx）

#### 标签

```bash
# 查看标签
$ git tag
# 添加标签
$ git tag v1.0
# 添加标签到版本
$ git tag v0.9 f52c633
# 显示标签
$ git show <tagname>
# 指定标签信息
$ git tag -a <tagname> -m "blablabla..."
# 删除标签
$ git tag -d v0.1
# 推送标签
$ git push origin v1.0
# 推送全部尚未推送到远程的本地标签
$ git push origin --tags
# 删除本地标签
$ git tag -d v0.9
# 删除远程标签
$ git push origin :refs/tags/v0.9
```

#### 工作区和暂存区概念

工作区：工作目录

版本库：.git

暂存区：版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支`master`，以及指向`master`的一个指针叫`HEAD`。

git add`命令实际上就是把要提交的所有修改放到暂存区（Stage），然后，执行`git commit`就可以一次性把暂存区的所有修改提交到分支。

所以，一旦提交后，如果你又没有对工作区做任何修改，那么工作区就是“干净”的。

```bash
# 暂存工作区
$ git stash
# 查看暂存工作区
$ git stash list
# 恢复暂存工作区
$ git stash apply
# 删除暂存工作区
$ git stash pop

```

当执行 git add 实际上就是把文件添加到暂存区

当执行 git reset HEAD 时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。

当执行 git rm --cached <file> 时，会直接从暂存区删除文件，工作区则不做出改变。

当执行 git checkout 命令时，会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区的改动。

当执行 git checkout  HEAD <file> 命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。（[摘自](http://www.runoob.com/git/git-workspace-index-repo.html)）

#### 多分支管理

我们可以为一个本地管理库添加多个远程仓库,用来做数据备份，或者上线仓库管理等操作。

- develop 开发仓库

- test 测试仓库

- release 发布仓库

当我们要进行版本发布的时候。就可以选择要将代码推送到不同的仓库。然后针对不同的仓库，各自又能够在不同的地方做不同的事

```bash
$ git remote add develop master
$ git remote add test master
$ git remote add release master
```

这样本地代码，就会关联上3 个不同的仓库。那么当我们提交代码的时候，具体要提交到哪个远程分支呢。这个时候，我们就需要在push 的时候明确远程分支。

```bash
$ git push develop master
$ git push test master
$ git push release master
```

大多数情况下，我们都是在一个远程分支上进行代码提交，只是偶尔有用到提交到不同的远程仓库 。所以有一个更简单的方式提交。那就是关联远程仓库分支跟本地的分支。使用`git branch --set-upstream-to` 命令。

```bash
$ git branch --set-upstream-to develop master 或者 git branch -u develop master
```

这样，后续只需要简单的使用 `git push` 或者 `git pull` 命令就可以了。

#### 变基

```bash
$ git rebase
```

#### 打包

```bash
# 生成一个可供发布的压缩包
$ git archive
```
