资料：

[git教程](https://www.runoob.com/manual/git-guide/)

# git与linux基本指令

隐藏文件

~ 根文件

ls

ll

mkdir

pwd

ls -a


暂存 —— 提交暂存 —— push提交
# git与vscode 
Git 全局设置:

 0. git config --global user.name "ASxx" 
git config --global user.email "123456789@qq.com"git remote -v //查看 
git remote add origin https://git.oschina.net/name/package.git   //用你仓库的url
git push -u origin master  //提交到你的仓库(-verbose)
 1. git.path 
 2. git remote orign http .
 3. git commit -m "***"
 4. git push origin master
并在 -m 自定义这次改变的信息

在vs中每次更新代码都会要输入账号密码，方便起见，可以配置一下让GIT记住密码账号。
git config --global credential.helper store   //在Git Bash输入这个命令就可以了