###  使用SSH连接至GitHub
https://segmentfault.com/a/1190000015699824?utm_source=tag-newest

#### 官方文档地址: 
https://help.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh

错误处理

1. https://help.github.com/en/github/authenticating-to-github/error-agent-admitted-failure-to-sign
"Agent admitted failure to sign using the key"

eval "$(ssh-agent -s)"
$ ssh-add

2. https://help.github.com/en/github/authenticating-to-github/error-permission-denied-publickey

#### [git 设置了ssh key 还是需要输入账户和密码](https://www.cnblogs.com/blogxiao/p/10762070.html)

参考这篇文章https://blog.csdn.net/shahuhu000/article/details/86625987

git remote remove origin
git remote add origin git@github.com:Username/Your_Repo_Name.git



#### 小抄

https://gitee.com/liaoxuefeng/learn-java/raw/master/teach/git-cheatsheet.pdf



关于SSH
  使用SSH协议，你可以连接并且验证到远程服务器和服务。使用SSH Key,你可以不用每次提供你的用户名和密码就可以连接到GitHub。

检查已经存在的SSH Key
  在你创建一个SSH Key时，你要检查下你是否已经有了存在的SSH keys。

打开Git Bash
输入ls -al ~/.ssh看是否存在SSH Key
检查路径列表下是否已经存在一个公共的SSH Key
  如果你没有存在的公私秘钥对，或者你不希望使用已存在的去连接GitHub，你可以生成一个新的SSH Key.
  如果你看到了已经存在的公私秘钥对，并且你也想使用它们去连接GitHub，你可以将你的SSH Key导入到ssh-agent中。

创建一个新的SSH Key
  在已经检查了是否有存在的SSH Key之后，你可以生成一个新的SSH Key用来认证，并且添加到ssh-agent中。

打开Git Bash
复制如下代码，并将邮箱替换成你的GitHub Email
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
这将会使用你提供的email作为标签，创建一个新的SSH Key
当你确认“输入文件保存key”，按回车键。将会保存到默认的地址，也可以自定义保存地址：
/C/User/Lionel/.github/id_rsa
在确认的时候输入一个安全口令。

将SSH Key添加到ssh-agent
确保ssh-agent正在运行
eval $(ssh-agent -s)
输出：Agent pid 432
添加你的SSH私钥到ssh-agent，输入之前设置的安全口令
ssh-add ~/.github/id_rsa
添加SSH Key到你的Github账户

添加一个新的SSH Key到GitHub账户
将SSH Key复制到粘贴板
clip < ~/.ssh/id_rsa.pub
点击个人资料里面的Settings
点击SSH and GPG keys.
点击 New SSH key or Add SSH key.
输入Title和Key并保存

测试SSH连接
打开Git Bash
输入ssh -T git@github.com

问题处理
1.将公钥添加到GitHub后，每次提交还要输入用户名与密码
原因：本地仓库和远程仓库的连接是通过Https协议连接的，将Https协议换成SSH协议，重新导入本地仓库。

2.Permission denied (publickey)
确保打开ssh-agent：eval "$(ssh-agent -s)"
检查你的私钥添加到ssh-agent：ssh-add -l

