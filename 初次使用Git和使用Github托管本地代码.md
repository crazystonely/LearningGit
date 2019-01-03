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

+ 在本地的代码仓库中添加需要上传的文件