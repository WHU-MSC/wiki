# 2022 WHU-MSC 新手任务

## 概述
- [ ] 了解 PGP
- [ ] 学会使用 git
- [ ] 向指定仓库提交 PR

## 细则
简言之，你所需要完成的任务是：
在[指定 git 平台](https://git.whumsc.wiki)中注册帐号（填写无真实性要求的邮箱等个人信息），Fork [指定仓库](https://git.whumsc.wiki/WHU-MSC/PR-playground)，在其中随便添加一个文件，但需要使用你自己的 GPG 密钥进行签名，然后向上游提交 PR.

可以参考 [GPG 简介](../../tech/beginners-guide/gpg-brief-introduction.md) 和 [Github 简介](../../tech/beginners-guide/github-brief-introduction.md).

### 创建密钥对
你需要创建 GPG 的密钥对用于对 commit 进行签名（如果你本来就有，那当然不用创建）。

你需要将公钥上传到该平台的你的帐号中。

### 设置你的 git
你可能需要配置 user.email，user.name，user.signingkey 等个人信息。

你可能还需要配置 gpg.program 等信息，设置 EDITOR，GPG_TTY 等环境变量。

### 添加文件
你需要 Fork 该仓库并且 clone 到本地，随意添加一个你喜欢的文本文件，并提交，记得使用你的私钥对提交进行签名。

别忘了将你的提交 push 到远程仓库。

### 提 PR
你需要向上游发起 Pull Request.

如果你所提交的内容基本符合要求，你的 PR 将会被接收，恭喜你完成了新手任务！


