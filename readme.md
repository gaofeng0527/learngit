# 创建SSH Key

前面已经学习了Git在本地的基础操作，之前也说过，Git是分布式版本管理系统，如果只是在本地操作，怎么能叫分布式呢。

实际情况是这样，找一台电脑充当服务器的角色，每天24小时开机，其他每个人都从这个“服务器”仓库克隆一份到自己的电脑上，并且各自把各自的提交推送到服务器仓库里，也从服务器仓库中拉取别人的提交

有个叫[GitHub](https://github.com/)的神奇的网站，从名字就可以看出，这个网站就是提供Git仓库托管服务的，所以，只要注册一个GitHub账号，就可以免费获得Git远程仓库。

本地仓库和远程Git仓库是通过SSH传输的，因此要在github帐号配置本地公钥。

<!-- more -->

## 创建SSH Key

1.   创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有`id_rsa`和`id_rsa.pub`这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：

     ```shell
     $ ssh-keygen -t rsa -C "youremail@example.com"
     ```

2.   登陆GitHub，打开“Account settings”，“SSH Keys”页面：

     然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴`id_rsa.pub`文件的内容

为什么GitHub需要SSH Key呢？因为GitHub需要识别出你推送的提交确实是你推送的，而不是别人冒充的，而Git支持SSH协议，所以，GitHub只要知道了你的公钥，就可以确认只有你自己才能推送。

当然，GitHub允许你添加多个Key。假定你有若干电脑，你一会儿在公司提交，一会儿在家里提交，只要把每台电脑的Key都添加到GitHub，就可以在每台电脑上往GitHub推送了。

最后友情提示，在GitHub上免费托管的Git仓库，任何人都可以看到喔（但只有你自己才能改）。所以，不要把敏感信息放进去。

## 创建远程仓库

其实就是在Github上创建一个仓库

1.   New repository 创建一个新仓库，填写仓库名称，点击 create new repository

2.   创建成功后，页面会有提示

     1.   >    echo "# learngit" >> README.md
          >    git init
          >    git add README.md
          >    git commit -m "first commit"
          >    git remote add origin git@github.com:gaofeng0527/learngit.git
          >    git push -u origin master

          …or create a new repository on the command line

          上面的意思是，在本地创建一个仓库，并编写README.md文件，把该目录初始化Git本地仓库，然后通过`git remote add origin git@github.com:gaofeng0527/learngit.git`命令和远程创建的仓库关联。然后通过`git push -u origin master`命令，把本地的内容，推送到远程仓库上。

     2.   >    git remote add origin git@github.com:gaofeng0527/learngit.git
          >    git push -u origin master

          …or push an existing repository from the command line

          上面的意思是：本地已经有库了，直接用命令关联远程库，并推送内容。

     总结：`gaofeng0527`这个是Github的帐号；learngit这个是新创建的仓库名称。`git remote add origin ....`命令是关联远程仓库。把本地库的内容推送到远程，用`git push`命令，实际上是把当前分支`master`推送到远程。

     远程库的名字就是`origin`，这是Git默认的叫法，也可以改成别的，但是`origin`这个名字一看就知道是远程库。

     由于远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。

现在在看，远程仓库的内容，就和本地的内容一样了。

## 修改本地内容，提交远程练习

1.   修改本地README.md文件内容

