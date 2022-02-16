
## 前言

由于工作原因我需要经常使用 Gitee和 Github ，之前配置好了一个，但是不知道怎么同时配置两个，所以就有了这篇文章。<br/>


## 创建 ssh key

```
# 进入用户目录下的 .ssh 文件夹下，路径会因你使用的操作系统不同而略有差异
# 没有这个文件夹也无所谓，直接运行下一句命令也可以
cd ~/.ssh

# 生成 key，将邮件地址替换为你 Gitee 或者 Github 使用的邮件地址
ssh-keygen -t rsa -C "xxx@xxx.com"

```
接下来应该会看到下面的提示：
```
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/your_user_name/.ssh/id_rsa): id_rsa_gitee
```

这一步如果默认回车，会生成名为 id_rsa 的文件，你可以输入不同的名字来便于识别文件，比如生成 Gitee 的 ssh key
可以设置为 id_rsa_gitee，设置 Github 的 ssh key 可以设置为 id_rsa_github ，我这里设置为 id_rsa_gitee。<br/>

接下来的会看到：
```
Enter passphrase (empty for no passphrase):
```
直接回车，然后会看到：
```
Enter same passphrase again:
```
继续回车就行了。生成完毕：

```
Your identification has been saved in id_rsa_gitee.
Your public key has been saved in id_rsa_gitee.pub.
The key fingerprint is:
SHA256:F0K/ojCbFzgMPru11m4g/9uV03oHK+U0rKBLwOOye2c xxx@xxx.com
The key's randomart image is:
+---[RSA 2048]----+
|        .        |
|       . .       |
|  .     . o      |
| . + .   . o     |
|  o X . S o.     |
|  .+.O o.o o*    |
|  oo=o+. .+=.+   |
|   =++E. .oo+ .  |
|  ++.*=o. .o .   |
+----[SHA256]-----+
```

## 在 Gitee 和 Github 添加 public key

找到用户目录下的 .ssh 文件夹，查看并复制创建好的 id_rsa_gitee.pub 或 id_rsa_github.pub 的内容。

```
cd ~/.ssh
# 查看 id_rsa_gitee.pub 文件内容
cat id_rsa_gitee.pub
```
会显示这样一串东西，复制它：
```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC3vrw+zyYf+OiT0E0Fanbi+tVp6JvVp2qxrNCWDs4MauyFnDwMgaIxkEzG5yiuYw/oM2GOpl7bXGq49mvnHBVLfXhXP14GL9+knbO1ulVGdU2kaRCXatFFQYjnSSs5gFms1xTqWnRB4QoVrYFk+vFzaMQxppiwFTZyvyOg0L6WU1yueixhGfHhc9Thwb579It9grhYqharhhVMMEEt5Vr5tw6SKGmc91otW4dX3yeSB+nlJEa7LDqHiuIeYXra5ioxkBNvqCEAFz3isJjkE0wR7rkE26FrHV9bNzHd3xuNnysi1qmtI/+kBb4gd2uZIUeinbPGo5GqnWWrF/M4vgKD4L6VNEbri6kxajsTZQSGjJ3cWZ2MhmWy/a+vGT++Aiusq5jxhbNfoKTKJh0esM+kf0mZicDf7KHcUFlnRSjU06yF+jQJA4ykdS0o1QUIagqJ+GLblz2jb/2JHSiM6W+moJEMzyB3dsRCwdEj8iMuLUtVVTgIA04O1mf6rDbQSJ8= liuzhu116@126.com

```

打开 Gitee 和 Github 的网站找到设置，再找到 SSH Keys，添加复制的 public key 。如下图所示：

 <img src="./media/pictures/git/gitee.png" />
 <img src="./media/pictures/git/github.png" />

## 创建git config配置文件

在用户目录下的.ssh 文件夹中创建 config 文件，添加以下内容以区分两个 ssh key：

```
# gitee
Host gitee.com
HostName gitee.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa_gitee

# github
Host github.com
HostName github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa_github
```

## 测试连接是否正常

**在命令行输入：**

```
ssh -T git@github.com

```

**若返回如下内容，则 Github 连接正常：**
```
Hi yourname! You've successfully authenticated, but GitHub does not provide shell access.
```

**继续在命令行输入：**

```
ssh -T git@gitee.com
```

**若返回如下内容，则 Gitee 连接正常。**

```
Welcome to Gitee.com, yourname!
```

## 项目实战

以JavaStudy为例，修改该项目根目录下.git文件夹内的config文件

```
[core]
	repositoryformatversion = 0
	filemode = false
	bare = false
	logallrefupdates = true
	symlinks = false
	ignorecase = true
[remote "gitee"]
	url = https://gitee.com/farmer-it/javastudy.git
	fetch = +refs/heads/*:refs/remotes/origin/*
	
[remote "github"]
	url = git@github.com:farmer-liuz1024/javastudy.git
	fetch = +refs/heads/*:refs/remotes/origin/*

[branch "master"]
	remote = origin
	merge = refs/heads/master
[gui]
	wmstate = normal
	geometry = 841x483+78+78 189 218

```

将另一方 config文件内的[remote “origin”]，复制到该文件内，并且修改origin名称，名称可以自定义。

## 上传代码

```
git add .
git commit -m "update"
#提交到github
git push github master
#提交到码云
git push gitee master
```

## 更新代码
```
#从github拉取更新
git pull github
#从码云拉取更新
git pull gitee
```

## 参考

- https://zhuanlan.zhihu.com/p/78978851
- https://blog.csdn.net/zj7321/article/details/82222483


