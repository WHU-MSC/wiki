# 提问的智慧[极速版]

## 在提问之前

1. 联想之前遇到过的相似问题，尝试用相似的解决方法
1. 在搜索引擎中查找关键词（技巧：在`error``fatal`以及冒号等提示词后的技术名词可能是关键词）
1. 向大语言模型（例如：ChatGPT, New Bing, 文心一言，星火大模型等）提问
1. 在 FAQ/Help 等类似的文档中查找相似的问题
1. 在 Github Issues 查找相似的问题

## 提问的步骤

1. 寻找适合自己问题的社区平台（例如有的论坛欢迎新人，而有的论坛只适合某方面的资深开发者）

2. 根据以下的模板构造自己的提问
    - 问题描述
    - （可选的）问题背景
    - 操作步骤
    - 出现结果
    - （可选的）预期结果
    - （可选的）通过搜索引擎了解的信息
    - 已尝试过的解决方案以及对应的结果
    - （可选的）尚未尝试的解决方案以及未尝试的原因
    - 硬件版本/软件版本/软件包列表
    - 完整代码/部分代码/命令行输出/相关日志的文本/截图
    - （可选的）能否复现以及复现步骤
    - （可选的）补充说明

例如这个比较短的例子：

> 我无法使用我的 Python。我在 python.org 中下载 python-3.12.0-amd64.exe 并安装，然后在命令行中输入 Python，然后我的 Windows Store 就被打开了！（附上命令行截图和…… Windows Store 截图 (^^;) ）这完全不是我希望的，我希望命令行会输入 Python 的版本号并进入交互模式（网上的图片，显示一个进入交互模式的 Python 命令行）。我的环境变量如下：（图片），命令 where python 结果如下：（文本）

又例如以下这个比较长的例子 [source](https://github.com/ManimCommunity/manim/issues/3378)：

> `AddTextLetterByLetter()` with blank `MarkupText` renders broken partial movie #3378（问题的简要描述）
> 
> ## Description of bug / unexpected behavior（问题的详细描述）
> When use `AddTextLetterByLetter()` to render an animation for a blank `MarkupText`(e.g. `MarkupText('<span bgcolor="#777777"></span>')`), manim will render a broken video, which cannot be opened by Media Player in Windows or decoded by ffmpeg. In `--preview`, a `FileNotFoundError` will be thrown by manim. This bug will occur when another scene's movie has been rendered before.
> 
> ## Expected behavior（预期结果）
> Just be like `AddTextLetterByLetter(Text(""))`.
> 
> ## How to reproduce the issue（复现步骤）
> 1. Delete `media/videos/problem_recurrence` if exists.
> 2. Run `manim problem_recurrence.py TextCreateScene`.
> 3. Run `manim problem_recurrence.py MarkupTextAddTextLetterByLetterScene`.
> 4. Try open `media/videos/problem_recurrence/1080p60/partial_movie_files/MarkupTextAddTextLetterByLetterScene/1413466013_3861299098_223132457.mp4`(hash maybe change) with Media Player, failed with some info: [![pPTjqZF.png](https://z1.ax1x.com/2023/09/24/pPTjqZF.png)](https://imgse.com/i/pPTjqZF)
> 5. Try encode it by `ffmpeg -i 1413466013_3861299098_223132457.mp4 -r 1 %03d.png`, failed with info `Output file #0 does not contain any stream`.
> <details><summary>Code for reproducing the problem（完整代码）</summary>
> （过长，省略）
> </details>
> 
> 
> ## Logs（相关日志）
> 
> <details><summary>Terminal output</summary>
> （过长，省略）
> </details>
> 
> 
> ## System specifications（软件版本）
> 
> <details><summary>System Details</summary>
> 
> - OS: Windows 10 22H2 19045.3448
> - RAM: 16.0 GB
> - Python version: Python 3.8.18
> - Installed modules (provide output from `pip list`):
> （过长，省略）
> </details>
> 
> <details><summary>LaTeX details</summary>
> 
> + LaTeX distribution: Version 3.141592653 (TeX Live 2022)
> + Installed LaTeX packages: default, see
> [Installed LaTeX packages.txt](https://github.com/ManimCommunity/manim/files/12708286/Installed.LaTeX.packages.txt)
> 
> </details>
> 
> <details><summary>FFMPEG</summary>
> 
> Output of `ffmpeg -version`:
> （过长，省略）
> </details>
> 
> ## Additional comments（补充说明）
> `visualcode` is a conda environment.
> <details><summary>Output of `conda list`</summary>
> （过长，省略）
> </details>

3. 耐心等待回复，并及时补充相关信息

### 在提问之后

**向帮助过你的人表示感谢。**然后继续工作，写一篇博客，或者将这份互助精神传递下去。

## FAQ for Git

以下是群内经常被提出的关于 Git 的问题，包括问题描述、原因分析、解决方法。仅供参考，具体问题仍需具体分析。

### 不能访问 GitHub

问题描述：不能通过浏览器访问 [github.com](github.com)，尝试使用 Git 进行网络相关操作时报错：
```
$ git clone https://github.com/xxx/yyy.git
Clone into 'yyy'...
fatal: unable to access 'https://github.com/xxx/yyy.git/': Failed to connect to github.com port 443 after 21080 ms: Couldn't connect to server
```

原因分析：网络问题。因不可抗因素，Github 在国内很难访问。

解决方法：使用网络加速器（例如 [Watt Toolkit(原 Steam++)](https://steampp.net/)）或其他技术（例如 Clash 等）改善。

### SSL 证书问题

问题描述：尝试使用 Git 进行网络相关操作时报错：
```
$ git push origin branch-XYZ
fatal: unable to access 'http://github.com/xxx/yyy.git/': SSL certificate problem: unable to get local issuer certificate
```

原因分析：Git 无法获取本地颁发者证书，因此不能相信这个网站。

解决方法：先测试能否正常访问 GitHub。如果不能，则先按照上一个问题的解决方法操作。

### 权限不足

问题描述：尝试使用 `git push` 时报错：
```
$ git push origin branch-XYZ
remote: Permission to xxx/yyy.git denied to zzz.
fatal: unable to access 'https://github.com/xxx/yyy.git/': The requseted URL returned error: 403
```

原因分析：你正在试图向一个你无权推送的仓库推送分支。

解决方法：将原仓库 fork 为自己的仓库，向自己的仓库推送分支，然后发起从自己仓库到原仓库的 Pull Request。

### 远程库不存在

问题描述：尝试使用 Git 进行网络相关操作时报错：
```
$ git pull origin branch-XYZ
fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

原因分析：本地仓库中未设置远程仓库，或无权访问远程仓库，或远程仓库不存在。

解决方法：检查本地仓库的 remote 是否设置正确。

### 本地仓库不存在

问题描述：尝试使用 Git 进行本地仓库相关操作时报错：
```
$ git add xxx.yyy
fatal: not a git repository (or any of the parent directorues): .git
```

原因分析：Git 在路径下找不到 .git 目录，因此判定该目录不是 Git 仓库。

解决方法：利用 `cd` 命令切换到正确的 Git 仓库路径。

### master 对象名无效

问题描述：尝试使用 Git 切换分支时报错：
```
$ git branch branch-XYZ
fatal: not a valid object name: 'master'
```

原因分析：仓库未初始化，`master` 分支尚未创建。

解决方法：使用 `git commit` 创建一个初始提交。

