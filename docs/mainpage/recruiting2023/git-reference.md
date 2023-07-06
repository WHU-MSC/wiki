# 1. Git & Github

Git 是一个分布式版本控制系统，可以高效地处理项目的版本管理。换句话说，它能跟踪和记录一个或多个文件的内容变化，让你可以在任何时候回到特定的版本。

GitHub 则是一个基于 Git 的线上服务平台，它不仅提供 Git 版本库的托管服务，还提供了一些额外的功能，比如协作功能、任务管理、bug 跟踪等。另外，GitHub 也是一个开源社区，许多优秀的开源项目都托管在上面。

在现实生活中，我们常常会在不同的方面用到他们。对于 Git ，我们会使用他去跟踪我们的项目版本，以记录我们的增删改。在小组合作中，我们也往往会使用 Git 来对我们的项目进行版本管理，并且通过推送到 GitHub 这一个线上服务平台来在组内共享代码。同时， GitHub 上面有很多开源的项目，我们可以借鉴，可以学习他们。

以下我们会用比较正式的 Refer 语言教会你一些基本的 Git 知识。

同时，如果你觉得本教程有难度，可以也了解更加接地气的：[WHUCAO Git Refer](https://whucodingandopen.github.io/whucao/tech/git.html) 版本。

# 2. Git 的安装

打开 Git 的官网：[Git](https://git-scm.com/)。找到 `Download for Windows ` 然后点击，选中 `64-bit Git for Windows Setup` 下载并安装。

在接下来的页面中，依次选择你需要的必要项以完成安装，以下给你可能需要更改的地方：

1. **Choosing the default editor used by Git**：推荐选择 Use Visual Studio Code as Git's default editor。

除以上说明外，其余你均可以选择 **默认选项**。

# 3. Git 的基本操作

假设我们在 D 盘的 `testGit` 文件夹中。

右键文件夹任意空白处，选择菜单的从此处打开终端。

Tips: 终端可以理解为一个黑盒，像其中输入指令，计算机根据指令执行对应的更改然后输出给用户（或者输出空，也就是没有输出）。

我们假设你的 testGit 文件夹中是这个样子

```bash
    Directory: D:\testGit

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---            2023/7/4    11:43              0 123.txt
-a---            2023/7/4    11:43              0 123456.txt
```

## 3.1 建立 Git 仓库

```bash
git init
```

此命令会在你的目录下面初始化 Git 仓库。

输入后，你会看到：

```bash
Initialized empty Git repository in D:/testGit/.git/
```

PS：你可能会见到：

```bash
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint:   git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint:   git branch -m <name>
Initialized empty Git repository in D:/testGit/.git/
```

值得注意的是，黄色字段是说明提示，并非报错，大意是提示你默认的分支名是 master，你可以通过他提及的命令修改默认分支名。

# 3.2 Git 基本操作

本节我们会说明如何让 Git 追踪某个文件

```bash
git add [filename]
```



例如，我们可以输入：

```bash
git add 123.txt
```

这表示我们想让 Git 追踪我们 123.txt 文件的变动。



如果有很多文件，我们不想一个一个添加的话，可以使用：

```bash
git add .
```

这表示我们将整个目录的所有文件（含文件夹以及文件夹的子文件）都让 Git 所追踪。



追踪后，我们对文件做的一切更改会与上一次进行比较，这称为 **版本管理**。

此外，我们通过 commit 来标记上一个更改达到下一个更改的 **过程**。



输入命令：

```bash
git commit -m "something"
```

其中，something 是你对这个过程的描述。



例如，我们给出一个输入和输出：

```bash
PS D:\testGit> git commit -m "s"
[master (root-commit) f794987] s
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 123.txt
 create mode 100644 123456.txt
```



# 3.3 Git 的分支

```bash
git branch -v
```

得到输出：

```bash
PS D:\testGit> git branch -v
* master f794987 s
```

对于 `master f794987 s` 这行数据，第一个为分支名，也就是 3.1 所说的在我们没有指定分支名下，刚开始创建项目时自动的分支名，第二个我们暂时忽略，第三个就是最后一次提交的更改信息，也就是上面 3.2 我们所 commit 的 "s" 

PS：对于 `git branch -v` 的 `-v`，其表示的是 `version` ，也就是查看分支的版本。

# 3.3.1 分支的建立

```bash
git branch newBranch
```

输入后我们即可建立一个名为 `newBranch` 的分支。

# 3.3.2 切换分支

```bash
git checkout newBranch
```

输出：

```bash
Switched to branch 'newBranch'
```

这表示我们进入了 `newBranch` 的分支。



此时输入：

```bash
git branch -v
```

会得到：

```bash
  master    f794987 s
* newBranch f794987 s
```

此时我们发现 newBranch 基于 master 分支，拷贝了一份到自己的分支中。并且前面被 `*` 标记，这个符号标记了我们所在的分支。



# 3.3.3 分支的作用

不同的分支让文件之间分离开来，例如我们在 newBranch 做的一切操作，在切换到 master 后将会看不见，也就是两者是独立的。

例如我们添加一些文字在 123.txt 中，比如 "123456" ，然后进行提交更改：

```bash
git add .
git commit -m "s2"
```

得到输出：

```bash
[newBranch b387d28] s2
 1 file changed, 1 insertion(+)
```

然后我们切换到主分支：

```bash
git checkout master
```

我们会发现我们添加的文字不见了！这就是分支之间文件是隔离的。

# 3.3.4 分支合并

有时候我们在其他分支所做的更改想要合并到另一个分支中，可以使用：

```bash
git merge [branch-name]
```

例如：

```bash
git merge newBranch
```

得到输出：

```bash
Updating f794987..b387d28
Fast-forward
 123.txt | 1 +
 1 file changed, 1 insertion(+)
```

我们再检查 123.txt，发现出现了我们之前的内容。



# 4. GitHub Clone & Push

首先打开 GitHub 的某个项目地址：[武汉大学微软学生俱乐部2023年招新 (github.com)](https://github.com/WHU-MSC/WHUMSC2023New)

然后点击绿色的Code按钮，并选择 Clone-HTTPS 分页，点击复制。



在任意一个文件夹打开终端，输入：

```bash
git clone [url]
```

url即为你复制的内容：

```bash
git clone https://github.com/WHU-MSC/WHUMSC2023New.git
```

然后进入文件夹中操作即可，在做了必要的更改并 commit 后，即可推送到 GitHub。

输入：

```bash
git push origin [branch-name]
```

其中 origin 是远端仓库的别名，暂时我们就理解为 `origin` 是一个定值。

branch-name为分支名，在 Github 仓库下，与 Clone 同行的左边有一个分支的图标，下拉框中的均为分支名。其中下拉框默认显示的就是你当前看到的文件所在的分支的分支名。

例如，在 WHUMSC2023New 仓库中，你默认看到的分支就是 master。

因此我们输入：

```bash
git push origin master
```

然后得到反馈：

```bash
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 20 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 315 bytes | 157.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: Bypassed rule violations for refs/heads/master:
remote:
remote: - Changes must be made through a pull request.
remote:
To github.com:WHU-MSC/WHUMSC2023New.git
   7409cf4..fe85e95  master -> master
```

PS：你可能无法操作，这是因为你对这个仓库没有管理权，需要通过 PR 来完成，以下将会介绍

# 5. Github Fork

GitHub Fork 是 PR 的前提，他的作用是在你的账号下创建一个与 fork 仓库一模一样的仓库，而这个仓库你是具有管理权限的。

我们只需要在项目界面点击 Fork ，然后点击 Create Fork 即可。

在 Fork 结束后，我们会看到一模一样的项目文件。

# 6. GitHub PR

我们在 Fork 后，利用相同的方式 clone ，编辑并上传文件到我们自己的 fork 后的仓库。

然后在原来的项目地址中，点击 Pull requests -> New Pull Request-> Create pull request 即可。

你会发现，这个过程可以宏观的理解为 Github 上面两个仓库的 `merge`。



# 7. 结束

以上只是面向笔试题的基本讲解，Git 和 Github 远远不止这些功能，希望你以后可以尽情探索！