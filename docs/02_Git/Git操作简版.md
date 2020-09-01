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
$ git push -u origin master 第一次
$ git push origin master
# 查看目录
$ ls
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

#### 版本回退

```bash
# 查看版本
$ git log
# 回退到版本
$ git reset --hard id
# 回退后提交
$ git push -f
$ git push -u origin master --force

效果
原版记录 007 006 005 004 003 002 001 
回退到 005 
现版本记录 005 004 003 002 001 
```



