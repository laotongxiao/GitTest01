### Git开发测试项目
## 开发者
* 姓名01
* 姓名02
## 常用命令=========================================================beign

查看状态
git status

查看分支
git branch -av

查看本地运程分支
git remote show
git remote show origin

查看标签
git tag
git show v1.0

设置用户名
git config --local user.name "lao tong xiao"

设置用户邮箱
git config --local user.email "252122327@qq.com"

查看用户名
git config --local user.name

查看用户邮箱
git config --local user.email

添加远程仓库别名
git remote add origin git@github.com:laotongxiao/GitTest01.git

添加远程仓库别名默认分支
git -u origin master


## 常用命令=========================================================end

## 第04讲 Git重要命令操练---------------------------------------------------------
项目初始化
git init

克隆仓库
git clone git@github.com:laotongxiao/GitTest02Parent.git

文件从工作区加入暂存区
git add test.txt

文件从工作区加入暂存区(所有一起加)
git add .

文件从暂存区加入版本区
git commit -m "test say!"

文件从工作区加入暂存区加入版本区
git commit -am "test say!"

从远程服务器拉取到本地
git pull

从本地推送到远程服务器
git push

查看日记
git log

查看日记带图
git log --graph

查看head日记
git reglog

## 第05讲 Git添加、删除、修改与日志---------------------------------------------------------

给工作区加文件
cd.>test.txt

文件从工作区加入暂存区
git add test.txt

文件从版本区删除
git rm test.txt
git commit -m "delect say!"

将删除未提交文件即在暂存区恢复到工作区
git reset head test.txt

文件从暂存区切消对工作区修改
git checkout -- test.txt

文件重命名
git mv test.txt test2.txt
git commit -m "edit name!"

文件重命名未提交文件即在暂存区恢复到工作区
git reset head hello.txt
git reset head hello2.txt
del hello2.txt

修改提交的说明
git commit --amend -m "edit say!"

## 第06讲 .gitignore与分支---------------------------------------------------------
.gitignore文件里是配置不给git管理文件如
config.proterties
.gradle/
.idea/
build.gradle
build/
settings.gradle
src/
*lao.txt
!lao.txt
*lao.txt
!lao.txt
/lao.txt
/*/lao.txt

查看分支
git branch

查看分支(更详细)
git branch -av

创建分支
git branch test

创建分支并让它做为当前分支
git checkout -b test

切换分支
git checkout test

删除分支(要切换分支)
git branch -d test

删除本地远程未追踪分支
git remote prune origin

合并分支
git merge test
git status
git commit -m "merge commit!" 解决冲突再提交

分支回退(回退一条)
git reset --hard head~1

分支回退
git reset --hard 9b883842fb1af4418780026cb17f79da30199d9f

暂存当前的分支开发切到另一分支应急再切回暂存分支
git stash save "say!"

回到暂存分支回复
git stash list
git stash pop
git commit -m "say!"

## 第10讲 标签与diff---------------------------------------------------------

查看标签(什么分支都可以)
git tag

查看标签(其体标签详细)
git show v1.0

创建轻量标签
git tag v1.0

创建重量标签
git tag -a v1.0 -m "say version"

删除标签
git tag -d v1.0

查找标签
git tag -l *1.0

工作区和暂存区两文件差别
git diff

工作区和版本区两文件差别
git diff head

暂存区和版本区某个提交两文件差别
git diff --cache 9b883842fb1af4418780026cb17f79da30199d9f

## 第12讲 Git远程操作---------------------------------------------------------

添加远程仓库别名
git remote add origin git@github.com:laotongxiao/GitTest01.git

查看本地远程仓库别名
git remote show

查看本地远程仓库别名详细讯息
git remote show origin

添加远程仓库别名默认分支
git -u origin master

克隆选程仓库
git clone git@github.com:laotongxiao/GitTest02Parent.git mytest

本地分支推送到远程仓库分支
git push

本地分支推送到远程仓库分支(完整命令)
git push origin test:master     本地分支名如(test):远程仓库分支名(master)

从远程仓库分支拉取到本地分支
git pull

从远程仓库分支拉取到本地分支(完整命令)
git pull origin master:test     远程仓库分支名(master):本地分支名如(test)

删除远程分支
git push origin :test

删除本地远程未追踪分支
git remote prune origin

推送标签到远程
git push origin v1.0 v2.0

推送标签到远程(未推送一次推)
git push origin --tags

删除远程标签
git push origin :refs/tags/v1.0


## 第16讲 Git远程分支、别名、gitk与git gui---------------------------------------------------------

创建别名
git config --global alias.br 'branch'

创建别名(运行外部命令)
git config --global alias.ui '!gitk'

运行gitk
gitk

运行gui
git gui

## 第21讲 Git裸库与submodule---------------------------------------------------------

建立裸库(服备器是不要工作区)
git init --bare

父仓库中创建子仓库
git submodule add git@github.com:laotongxiao/GitTest02Child.git mymodule
git add .
git commit -am "add submodule"
git push

克隆仓库(父仓库中带有子仓库)办法01常用
git clone git@github.com:laotongxiao/GitTest02Parent.git --recursive

克隆仓库(父仓库中带有子仓库)办法02
git clone git@github.com:laotongxiao/GitTest02Parent.git
cd mymodule
git submodule init
git submodule update --recursive
git checkout master

如果子仓库修改了要拉取到本地办法01(一个个拉取一个仓库)
cd mymodule
git pull
git add .
git commit --m "add edit submodule"

如果子仓库修改了要拉取到本地办法02(全部拉取仓库)常用
git submodule foreach git pull
git add.
git commit --m "add edit submodule"

删除子仓库
git rm --cached mymodule
rd/s mymodule
git commit -m "delete mymodule"
del .gitmodules
git commit -am "delete mymodule"
git push

## 第22讲 Git subtree---------------------------------------------------------

办法01
父仓库中创建subtree( --squash很危险，要使用全使用，要不全不用)
1.在父仓库中加入别一个仓库别名
git remote add subtree-origin git@github.com:laotongxiao/GitTest02Child.git
git remote show
2.真实创建subtree
git subtree add --prefix=subtree01 subtree-origin master --squash
git push

如果subtree仓库修改了要拉取到本地办法
git subtree pull --prefix=subtree01 subtree-origin master --squash
git push

把父仓库中的subtree推送到子subtree中(--squash不要用)
git push
git subtree push --prefix=subtree01 subtree-origin master

办法02
父仓库中创建subtree( 都不用--squash)
1.在父仓库中加入别一个仓库别名
git remote add subtree-origin git@github.com:laotongxiao/GitTest02Child.git
git remote show
2.真实创建subtree
git subtree add --prefix=subtree01 subtree-origin master
git push

如果subtree仓库修改了要拉取到本地办法
git subtree pull --prefix=subtree01 subtree-origin master
git push

把父仓库中的subtree推送到子subtree中
git push
git subtree push --prefix=subtree01 subtree-origin master

## 第25讲 Git cherry-pick(注意当前分支是那个如master)---------------------------------------------------------
git cherry-pick 9cfc249f5fb0f328e3acb551219815c6131efd81

去掉在分支上的误操作(注意当前分支是那个如develop)
git checkout 166397bf8f102734210ae4e11d8e4ae58e5a25ea
git branck -d delvelop
git checkout -b develop

## 第26讲 Git rebase原理深度剖析---------------------------------------------------------
最好不用，它合并会修改历史记录