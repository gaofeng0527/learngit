# Git

分布式版本管理系统，关键是免费。^_^

# windows install Git

直接从git官网下载安装程序即可，在开始-全部程序-git中有Git Bash 表示安装成功。

# version manager

创建仓库，添加文件，提交版本

<!-- more -->

## mark repository

第一步需要创建一个空目录（也可以是在其他目录下，建议创建新的目录，个人习惯哈）

```shll
#mkdir learngit   ---创建目录
#git init      ---初始化成git仓库  pwd 命令可以查看当前目录
```

## add file

在该目录下创建一个文件readme.md

Git is a version control system.

Git is free software.

把文件添加到仓库中，然后在提交到仓库。

```shll
#git add readme.md
#git commit -m "fisrt git file"
```

*git commit -m "message"* 文件提交命令，这里为什么需要`add`和`commit`命令呢，因为`add`可以多次添加文件，而`commit`命令只需要执行一次，就可以把之前所有添加的文件提交到仓库中去。 `-m`参数表示本次提交的描述信息。

## change file

打开文件，修改第一行内容  Git is a distributed version control system.

这个时候，可以输入`git status`命令查看文件状态

>    $ git status
>    On branch master
>    Changes not staged for commit:
>      (use "git add <file>..." to update what will be committed)
>      (use "git checkout -- <file>..." to discard changes in working directory)
>
>    ```
>        modified:   readme.md
>    ```
>
>    no changes added to commit (use "git add" and/or "git commit -a")

会告诉你，内容被修改，并且还没有提交，可以使用`git add`命令添加修改，或者`git checkout`放弃修改。

也可以使用`git diff`命令查看具体修改

>    $ git diff
>    diff --git a/readme.md b/readme.md
>    index 02086ec..5dfce89 100644
>    --- a/readme.md
>    +++ b/readme.md
>    @@ -1,3 +1,3 @@
>    -git is a version control system,
>    +git is a distributed version control system,
>
>     git is a free software.
>    \ No newline at end of file
>    warning: LF will be replaced by CRLF in readme.md.
>    The file will have its original line endings in your working directory.

看到具体修改后，可以进行提交了，操作步骤和添加文件一样，先执行一次`git add`命令后，在查看一下状态

>    $git add readme.md

>    $ git status
>    warning: LF will be replaced by CRLF in readme.md.
>    The file will have its original line endings in your working directory.
>    On branch master
>    Changes to be committed:
>      (use "git reset HEAD <file>..." to unstage)
>
>    ```
>        modified:   readme.md
>    ```

>    $ git commit -m "change file after commit"
>    [master warning: LF will be replaced by CRLF in readme.md.
>    The file will have its original line endings in your working directory.
>    02df42d] change file after commit
>    warning: LF will be replaced by CRLF in readme.md.
>    The file will have its original line endings in your working directory.
>     1 file changed, 1 insertion(+), 1 deletion(-)

提交完成后，再次查看状态

>    $ git status
>    On branch master
>    nothing to commit, working directory clean

可以看到没有内容需要提交。由此总结一下：

1.   修改某个文件，查看状态，会提示有内容修改，并且是未提交状态
2.   add命令之后，查看状态，提醒文件已经添加，但是还没有提交
3.   commit 状态恢复成初始状态


测试提交