## git命令

### git 安装
	配置信息
	git config --global user.email "<邮箱>"
	git config --global user.name "<NAME>"
### 代码上传流程
github操作：
```
创建好repository
```
本地操作：
```
	cd 文件地址
	git init
	git add .
	git status -s  # 查看是否添加到本地仓库
	git commit -m "frist commit"
	git remote add origin 'https://github.com/****/******.git'  # 关联远程代码库
	git push -u origin master  # 提交
```

### git init
	初始化一个Git仓库
	如 git init test
### git add
	git add 命令可将该文件添加到缓存
	用git status -s 可以查看与上次提交的修改
	A filename  # 添加到缓存区
	AM filename  # 添加到缓存区后又有改动，可以再次添加

### git clone
	git clone <协议> <地址> <自定义名称>
	协议有ssh,http,git
	如:
	git clone git@github.com:lwc/test.git
	git clone https://github.com:lwc/test.git
	git clone git://github.com:lwc/test.git

### git diff
	git diff 命令显示已写入缓存与已修改但尚未写入缓存的改动的区别
	尚未缓存的改动：git diff
	查看已缓存的改动： git diff --cached
	查看已缓存的与未缓存的所有改动：git diff HEAD
	显示摘要而非整个 diff：git diff --s（只显示文件名）

### ssh-keygen -t rsa -C "<邮箱>"
	密钥文件位于 ~/.ssh/id_rsa.pub

### git commit
	执行 git commit 将缓存区内容添加到仓库中
	git commit -m "describe"

### git remote add origin <地址>
	将本地仓库与远程仓库关联起来

### git pull [地址]
	将最新代码拉回本地
	已关联远程仓库：git pull origin master
	未关联远程仓库：git pull [地址]

## git push origin master
	将本地仓库的代码提交到远程仓库