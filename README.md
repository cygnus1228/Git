# 连接github
## [SwitchHosts](https://github.com/oldj/SwitchHosts/blob/master/README_cn.md)
```
下载后直接正常安装，接着以管理员身份打开，点击左下角+新建hosts
type选择Remote
URL:https://gitee.com/cnfeffery/GitHub520/raw/master/hosts
时间：每分钟
```

```
百度网盘：https://pan.baidu.com/s/18yEn7VGNoIWOg0H2N0_3gw 提取码: eh4d
备用秒传链接：e50e6df756ed094b2c4d6fceb5252be3#34272a00e92b9ed479f9b7706754a3fd#103944899#SwitchHosts._windows_installer_3.5.6.5551.exe
```
# [流程](https://www.bilibili.com/video/BV1tf4y1e7yt?p=1)
## 一、A端开始写代码
###### 1.初始化
```
Wndows:进入文件夹右键git bash here
Linux:mkdir xxx     cd xxx
```
###### 2.管理文件夹
```git init```
###### 3.检测文件夹
```git status```
###### 4.管理文件
```
git add 文件名 (单个)
git add . (所有)
```
###### 5.各状态切换
```
工作区：已控制文件:1     新文件或有变动文件：2      暂存区：3      版本库：4      远程仓库：5
1-2:自动检测     2-3：git add     3-4:git commit     4-5：git push origin 分支
2-1:git checkout  3-2:git reset HEAD  4-3:git reset --soft 版本号  5-4：git fetch origin 分支
4-1:git reset --hard 版本号     4-2：git reset --mix 版本号
4-1：git merge origin 分支   或   git rebase origin 分支
5-1：git pull origin 分支
git pull origin dev等同于git fetch origin dev和git merge origin/dev
```
###### 6.新增文件
```touch 文件名```
###### 7.查看
```
cat 文件名  查看代码
vim .   查看文件名
```
###### 8.编辑
```退出时按ESC输入:wq```
###### 9.个人信息配置
```
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```
###### 10.生成版本
```git commit -m 版本名```
###### 11.查看版本记录
```
git log/git reflog/git log --graph/git log --graph --pretty=format:"%h %s"
(之前/之后/图形/简化)
```
###### 12.给版本打标签
```
git tag -a v1 -m 第一版
git push origin --tags
```
###### 13.整合版本记录，保持代码提交整洁 rebase
```
(1)整合最近的几个版本记录
git rebase -i 版本号   或
git rebase -i HEAD~数字
注：
把被合并的pick改成s，并且用&连接被整合的版本名
合并未提交到版本库的（不要push）
Rebase f111e0f..71fa5b1 onto f111e0f (2 commands)
Commands:
p, pick <commit> = use commit
r, reword <commit> = use commit, but edit the commit message
e, edit <commit> = use commit, but stop for amending
s, squash <commit> = use commit, but meld into previous commit
f, fixup <commit> = like "squash", but discard this commit's log message
x, exec <command> = run command (the rest of the line) using shell
b, break = stop here (continue rebase later with 'git rebase --continue')
d, drop <commit> = remove commit
l, label <label> = label current HEAD with a name
t, reset <label> = reset HEAD to a label
m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
.       create a merge commit using the original merge commit's
.       message (or the oneline, if no original merge commit was
.       specified). Use -c <commit> to reword the commit message.
These lines can be re-ordered; they are executed from top to bottom.
If you remove a line here THAT COMMIT WILL BE LOST.
However, if you remove everything, the rebase will be aborted.
```
```
(2)合并不同分支的版本记录
git checkout dev
git rebase master
git checkout master
git merge dev
```
```
(3)合并忘记提交造成的分叉
git pull origin dev换成
git fetch origin dev
git rebase origin/dev
注：
产生冲突时
解决
git add xxx
git rebase --continue
使用Beyond Compare
在git中配置：
git config --local merge.tool bc3
git config --local mergetool.path '安装目录'
git config --local mergetool.keepBackup false
应用：git mergetool
```
[Beyond Compare](https://www.scootersoftware.com/download.php)
###### 14.分支
```
主：master   分支：dev
目前所处分支：git branch
创建分支：git branch 分支名称
切换分支：git checkout 分支名称
创建并切换分支：git checkout -b 分支名称
合并分支：
git checkout master
git merge 要合并分支名称
产生冲突：手动修改
删除分支：git branch -d 分支名称
```
###### 15.更换默认master(main)名称并删除远程分支
###### 更换本地分支名称
```git branch -m master(main) 其他名称```
###### 更改github默认分支
```settings-branches```
###### 删除远程分支
```git push origin --delete master(main)```
## 二、A端上传代码
###### 1.给远程仓库起名
``` git remote add origin 远程仓库地址```
###### 2.向远程仓库推送代码
```git push -u origin 分支```
## 三、B端第一次获取代码
###### 1.克隆远程仓库代码
```git clone 远程仓库地址```
###### 2.切换分支
```git checkout 分支```
## 四、B端进行开发
###### 1.切换到dev分支进行开发
```git checkout dev```
###### 2.把master分支合并到dev (仅一次)
```git merge master```
###### 3.修改代码
###### 4.提交代码
```
git add .
git commit -m xxx
git push origin dev
```
## 五、BA端继续写代码
###### 1.切换到dev分支进行开发
```git checkout dev```
###### 2.拉代码
```git pull origin dev```
###### 3.继续开发
###### 4.提交代码
```
git add .
git commit -m xxx
git push origin dev
```
## 六、B端继续
###### 1.切换到dev分支进行开发
```git checkout dev```
###### 2.拉代码
```git pull origin dev```
###### 3.继续开发
###### 4.提交代码
```
git add .
git commit -m xxx
git push origin dev
```
## 七、开发完毕要上线
###### 1.切换到master
```git checkout master```
###### 2.合并dev
```git merge dev```
###### 3.推送master
```git push origin master```
###### 4.推送dev
```
git checkout dev
git merge master
git push origin dev
```
## 八、开发新功能
```
git pull origindev
git pull master
```
## 九、多人协同开发 gitflow
###### 1.邀请合作
```
(1)new repository-settings-manage access-Invite a collaborator
(2)new organizations-creat a new repository
```
###### 2.审查代码配置
```settings-branches-```
[未完待续](https://www.bilibili.com/video/BV1tf4y1e7yt?p=26)
## 十、其他
###### 1.配置
```
(1)项目配置文件：项目/.git/config
git config --local user.email "you@example.com"
git config --local user.name "Your Name"
(2)全局配置文件：~/.gitconfig
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
(3)系统配置文件：/etc/.gitconfig    需要root权限
git config --system user.email "you@example.com"
git config --system user.name "Your Name"
(4)应用场景：
Beyond Compare配置
git remote add origin 地址：默认添加在本地配置文件（--local）
```
###### 2.免密登陆
```
(1)URL中体现
原来的地址：https://github.com/cygnus1228/git.git
vim .git/config修改
修改的地址：https://用户名：密码@github.com/cygnus1228/git.git
git push origin master https://用户名：密码@github.com/cygnus1228/git.git
git push origin master
```
```
(2)SSH实现
生成公钥和私钥(默认放在 ~/.ssh)
ssh-keygen
id_rsa.pub公钥  id_ras私钥
拷贝公钥内容并设置到git中-settings-ssh
在git本地配置ssh地址
git remote add origin git@github.com:cygnus1228/git.git
```
```
(3)git自动管理凭证
```
###### 3.git ignore
```
创建.gitignore
添加1.py  2.py  *.py(任意.py)  .gitignore  files/(文件夹内)  !a.h(a.h除外)  *.py[c|a|d]
```
[参考](https://github.com/github/gitignore)
###### 4.任务管理
```
(1)issues  提问、bug管理、任务管理
repositories-issues
(2)wiki  介绍
repositories-wiki
```
[更多](https://github.com/github)
