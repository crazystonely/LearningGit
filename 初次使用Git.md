# 初次使用Git

+ 打开Git Bash，首先配置自己的身份

```git
git config --global user.name liuyan
git config --global user.email crazystone_ly@sina.com
```

+ 然后开始创建代码仓库，以测试项目LearningGit为例

```git
liuyan@DESKTOP-87KJQ3D MINGW64 /d/LearningGit
$ cd D:/LearningGit

liuyan@DESKTOP-87KJQ3D MINGW64 /d/LearningGit
$ git init
Initialized empty Git repository in D:/LearningGit/.git/
```

+ 代码仓库创建完成可以提交本地代码，使用add添加和commit提交两个命令

```git
# add . 提交目录下所有文件
# add + 文件名 提交单个文件
# git commit -m "First Commit" 提交，-m参数后面添加提交消息

liuyan@DESKTOP-87KJQ3D MINGW64 /d/LearningGit (master)
$ git add .

liuyan@DESKTOP-87KJQ3D MINGW64 /d/LearningGit (master)
$ git commit -m "First Commit"
[master (root-commit) 58d8d7f] First Commit
 1 file changed, 21 insertions(+)
 create mode 100644 20190103.md
```

## 使用Github托管本地代码

+ 进入Github官网个人主页，点击`New repository`按钮新建版本库，并获取远程版本库地址
+ 在GitBash中，把远程版本克隆到本地

```git
liuyan@DESKTOP-87KJQ3D MINGW64 /d
$ git clone https://github.com/crazystonely/LearningGit.git
Cloning into 'LearningGit'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
```

+ 在本地的代码仓库中添加需要提交的文件

```git
liuyan@DESKTOP-87KJQ3D MINGW64 /d/LearningGit (master)
$ git add .

liuyan@DESKTOP-87KJQ3D MINGW64 /d/LearningGit (master)
$ git commit -m "First Commit"
[master 2a364ae] First Commit
 1 file changed, 53 insertions(+)
 create mode 100644 "\345\210\235\346\254\241\344\275\277\347\224\250Git\345\222\214\344\275\277\347\224\250Github\346\211\230\347\256\241\346\234\254\345\234\260\344\273\243\347\240\201.md"
```

+ 将代码库中的文件提交到Github，使用`git push origin master`同步

```git
liuyan@DESKTOP-87KJQ3D MINGW64 /d/LearningGit (master)
$ git push origin master
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 1.12 KiB | 1.12 MiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/crazystonely/LearningGit.git
   a65fd79..2a364ae  master -> master
```

#其他Git命令及上传Github方法

```git
git init //把这个目录变成Git可以管理的仓库

git add README.md //文件添加到仓库

git add . //不但可以跟单一文件，还可以跟通配符，更可以跟目录。一个点就把当前目录下所有未追踪的文件全部add了 

git commit -m "first commit" //把文件提交到仓库

git remote add origin git@github.com:crazystonely/LearningGit.git //关联远程仓库

git push -u origin master //把本地库的所有内容推送到远程库上
```

# 为Github账户设置SSH Key

+ 首先检查是否生成密钥

```git
cd ~/.ssh
ls
```

如果存在三个文件，则密钥已经生成，id_rsa.pub是公钥

+ 如果没有生成密钥，则通过以下命令来生成

```git
liuyan@DESKTOP-87KJQ3D MINGW64 ~
$ ssh-keygen -t rsa -C "crazystone_ly@sina.com"
```

+ 生成后将id_rsa.pub文件（公钥）使用记事本打开

+ 设置Github账户中的SSH key

  打开个人主页Settings - SSH and GPG keys - 点击`New SSH key`按钮，将id_rsa.pub中的内容粘贴到页面，并对该SSH Key命名，即可完成配置

  

