# First-try
this repository is my first, and l begin to learn git&amp;github by myself. My Mentor and Buddy are both cool and warm-hearted ma. Fighting!!!
本文旨在给第一次使用 git 和 github 的同学提供快速的学习指引，分享我在学习中用到的资源及我对每一个步骤的个人理解。本文基于 Ubuntu 18.04 LTS 系统环境安装git。这是我的第一篇博文，给自己打气！思远  Fighting ！

# Git入门与实践

Git是分布式版本控制系统，简单来说，git将自动帮助开发者记录版本变动信息并直观呈现。

GitHub是用于版本控制和协作的代码托管平台，他支持开发者可以该平台共同处理研发项目。

git简明指南：[](https://www.runoob.com/manual/git-guide/)



## 创建版本库及文件的添加

> 版本库又名仓库，英文名 **repository**，可以简单理解成一个目录，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。git 只能跟踪文本文件的改动，比如TXT文件，网页，所有的程序代码。

1. 创建新文件夹，输入 `git init` 创建新版本库

   ```shell
   ~$ cd /home/fangsiyuan/Documents
   cd fsygit
   git init
   Initialized empty Git repository in /home/fangsiyuan/Documents/fsygit/.git/
   ```

2. ` git add` 添加文件至仓库，`git commit -m "代码提交信息"`  需要注意：所需添加的文件需在仓库目录里。

   > 你的本地仓库由 git 维护的三棵“树”组成。第一个是你的 `工作目录`，它持有实际文件；第二个是 `暂存区（Index）`，它像个缓存区域，临时保存你的改动；最后是 `HEAD`，它指向你最后一次提交的结果。

   ![img](https://www.runoob.com/manual/git-guide/img/trees.png)

   执行  `commit`  系统提示 `*** Please tell me who you are.` 。这个错误是因为在创建git文件夹的时候信息不完善导致的，需执行以下命令：

   ```shell
   git config --global user.email "你的邮箱"
   git config --global user.name "你的名字"
   ```



## 本地仓库连接远程仓库

Git命令均是在本地执行，若想要开源则需要将数据放到其他开发人员能够连接的服务器上，我们选择Github作为远程仓库。

1. 首先 Git 与 Github 间由SSH加密传输，所以我们需要配置验证信息：

   ```shell
   $ ssh-keygen -t rsa -C "youremail@example.com"
   ```

复制在根目录下生成的**.ssh/id_rsa.pub** 文件里的**key**, 打开个人github里的**Settings -> SSH and GPG keys -> New SSH key**， 设置标题并将key粘贴。

2. 点击 **create repository** 按照指示新建个人仓库，创建完后如下图所示。

![image-20201016113702625](/home/fangsiyuan/.config/Typora/typora-user-images/image-20201016113702625.png)


## 提取、推送到远程仓库

我们已经使用add和commit指令更改了仓库，现在需要执行如下命令把改动提交到远端仓库：

```shell
git push origin master
```

如果你还没有克隆现有仓库。并且想要将仓库连接到某个远程服务器，你可以使用如下命令：

```shell
git remote add origin <server>
```



## Branch分支

> 分支是用来将特性开发绝缘开来的。在你创建仓库的时候，*master* 是“默认的”分支。在其他分支上进行开发，完成后再将它们合并到主分支上。

在我的理解里，正是分支的存在让一个不断迭代的应用或者说仓库可以有序的、有迹可循的多人协作开发，不同的分支体现了不同版本的迭代过程且最后统一到master上。

![img](https://www.runoob.com/manual/git-guide/img/branches.png)

