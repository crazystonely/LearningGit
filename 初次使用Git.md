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

  

## Notes

+ `git push`的一般形式为 git push <远程主机名> <本地分支名>  <远程分支名> 

  例如 `git push origin master：refs/for/master` ，即是将本地的master分支推送到远程主机origin上的对应master分支， origin 是远程主机名， 第一个master是本地分支名，第二个master是远程分支名。

  - **git push origin master**

    如果远程分支被省略，如上则表示将本地分支推送到与之存在追踪关系的远程分支（通常两者同名），如果该远程分支不存在，则会被新建 

  - **git push origin ：refs/for/master**  

    如果省略本地分支名，则表示删除指定的远程分支，因为这等同于推送一个空的本地分支到远程分支，等同于 git push origin --delete master 

  - **git push origin** 

    如果当前分支与远程分支存在追踪关系，则本地分支和远程分支都可以省略，将当前分支推送到origin主机的对应分支 

  - **git push** 

    如果当前分支只有一个远程分支，那么主机名都可以省略，形如 git push，可以使用git branch -r ，查看远程的分支名 

  -  **git push 的其他命令** 

    这几个常见的用法已足以满足我们日常开发的使用了，还有几个扩展的用法，如下：

    （1） git push -u origin master 如果当前分支与多个主机存在追踪关系，则可以使用 -u 参数指定一个默认主机，这样后面就可以不加任何参数使用git push，不带任何参数的git push，默认只推送当前分支，这叫做simple方式，还有一种matching方式，会推送所有有对应的远程分支的本地分支， Git 2.0之前默认使用matching，现在改为simple方式如果想更改设置，可以使用git config命令。git config --global push.default matching OR git config --global push.default simple；可以使用git config -l 查看配置

    （2） git push --all origin 当遇到这种情况就是不管是否存在对应的远程分支，将本地的所有分支都推送到远程主机，这时需要 -all 选项

    （3） git push --force origin git push的时候需要本地先git pull更新到跟服务器版本一致，如果本地版本库比远程服务器上的低，那么一般会提示你git pull更新，如果一定要提交，那么可以使用这个命令。

    （4） git push origin --tags //git push 的时候不会推送分支，如果一定要推送标签的话那么可以使用这个命令

  - **关于 refs/for** 

    refs/for 的意义在于我们提交代码到服务器之后是需要经过code review 之后才能进行merge的，而refs/heads 不需要 

    

    

    