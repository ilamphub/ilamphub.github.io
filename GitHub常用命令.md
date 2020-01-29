将GitHub的代码克隆到本地目录

```
git clone git@github.com:ilamphub/pydata-book.git
```



在GitHub下新建repo ，在本地新建Git 并将Git上传至新建的rpo下

```
echo "# Git-Test-Local-to-GitHub" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/ilamphub/Git-Test-Local-to-GitHub.git
git push -u origin master
```

将本地已有Git上传至repo

```
git remote add origin https://github.com/ilamphub/Git-Test-Local-to-GitHub.git
git push -u origin master
```

后面再上传时可无需git push -u origin master 直接git push origin master即可



本地新建Git库

```
git init
```

新建readme.md

将readme.md添加至暂存区

```
git add readme.md
```

将暂存区内读文件提交至仓库

```
git commit -m "wrote a readme file"
```

查看当前工作区状态

```
git status
```

Git管理的文件分为：工作区，版本库，版本库又分为暂存区stage和暂存区分支master(仓库)

工作区>>>>暂存区>>>>仓库

git add把文件从工作区>>>>暂存区，git commit把文件从暂存区>>>>仓库，

git diff查看工作区和暂存区差异，

git diff --cached查看暂存区和仓库差异，

git diff HEAD 查看工作区和仓库的差异，

git add的反向命令git checkout，撤销工作区修改，即把暂存区最新版本转移到工作区，

git commit的反向命令git reset HEAD，就是把仓库最新版本转移到暂存区。



查看文件差异

```
git diff readme.md
```