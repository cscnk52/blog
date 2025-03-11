+++
title = "Windows 上的 apt：Scoop 使用简明指南"
date = 2025-03-06T09:17:36Z
author = "cscnk52"
taxonomies.categories = ["tech"]
taxonomies.tags = ["Windows", "Scoop"]
+++

如果你用过 [Ubuntu](https://ubuntu.com/)、[Deepin](https://www.deepin.org/)、[Kali Linux](https://www.kali.org/) 或是 [Raspberry Pi OS](https://www.raspberrypi.com/software/) 等基于 Debian 的 Linux 系统，一定不会对 apt 感到陌生，[apt](https://deb.wiki/apt_usage/)（Advanced Packaging Tool）是一个在 [Debian](https://www.debian.org/) 及其衍生发行版中的 Shell 前端软件包管理器，使用 apt 快速地安装、管理、卸载软件，是非常自然且优雅的一件事情，不用去思考这个软件包到底 C 盘还是 D 盘，不用去担心这个软件包的依赖关系，不用去担心这个软件包的卸载是否会影响到其他软件包，这一切都是由 apt 来帮你处理的；而 Mac OS 上也有 [Homebrew](https://brew.sh/) 这样的软件帮助你来快速、简洁、高效地管理软件。

可再将目光转向 Windows 系统，要下载一个软件，你需要：

1. 在搜索引擎中输入软件名称
2. 从几十条搜索结果中筛选出一个可靠的下载地址
3. 下载下来一个打开就需要管理员权限的 exe 文件
4. 选择一个安装路径，可能还需要手动创建文件夹
5. 经过一步步的向导，选择一大堆选项
6. 等待安装完成

好麻烦！

## 为什么是 Scoop

这时候就需要包管理器出马了，但 Windows 上安装的选择很多，比如 Scoop、Chocolatey、winget 甚至是 Microsoft Store，为什么是 Scoop 呢？

### 需求分析

首先我们应该拆解我们对软件管理的需求：

#### 基本需求：

- 能够查看已安装的软件名称，版本，安装路径等信息
- 能够搜索查看软件包的信息
- 安装目标软件
- 能够根据自己意愿决定是否更新软件
- 卸载软件

#### 高级需求：

- 回滚或安装特定版本：某些情况下，我们需要安装特定版本的软件，或者是安装了新版本后出现了问题，需要回滚到之前的版本
- 锁定版本：有些软件在更新后可能会出现问题，我们需要锁定版本，不再更新
- 数据的管理与清理：软件安装后会产生一些数据，我们需要在卸载后清理这些数据
- 软件备份和迁移：需要将软件备份到其他地方，或者是迁移到另一台电脑

### 横向对比

| 评估指标             | Microsoft Store | Chocolatey | Winget | Scoop |
| -------------------- | --------------- | ---------- | ------ | ----- |
| GUI                  | ✅              | ✅         | ❌     | ❌    |
| 开源                 | ❌              | ❌         | ✅     | ✅    |
| 软件搜索、安装、更新 | ✅              | ✅         | ✅     | ✅    |
| 已安装软件查看与卸载 | ❌              | ✅         | ✅     | ✅    |
| 回滚版本与锁定版本   | ❌              | ✅         | ❌     | ✅    |
| 导出与备份           | ❌              | ✅         | ✅     | ✅    |
| 数据管理与清理       | ❌              | ❌         | ❌     | ✅    |

### 选择原因

除表格中列出的功能优势外，其他软件管理器的部分缺点也是我选择 Scoop 的因素：

1. Microsoft Store：只能安装 Store 中的软件，且部分软件是通过运行 exe 的方式安装的，会污染系统，只推荐通过 Store 安装 UWP 软件
2. Chocolatey：依然会污染系统，并且商业化过于严重，整体设计理念也不如 Scoop 清爽
3. Winget：是微软官方出品，但是功能较为简单，不支持回滚版本，不支持锁定版本，还是会污染系统

## Scoop 的安装与使用

### 安装

在安装之前，建议做一些准备工作，这些都是可选的，但是会提升你的 Scoop 使用体验：

#### 设置安装位置

你可以通过设置环境变量的方式来设置 Scoop 的安装目录

对于 Scoop 本身和安装软件的路径：

```powershell
$env:SCOOP='D:\Applications\Scoop'
[Environment]::SetEnvironmentVariable('SCOOP', $env:SCOOP, 'User')
```

对于全局安装的软件路径：

```powershell
$env:SCOOP_GLOBAL='F:\GlobalScoopApps'
[Environment]::SetEnvironmentVariable('SCOOP_GLOBAL', $env:SCOOP_GLOBAL, 'Machine')
```

#### 开启目录大小写敏感

开启目录大小写敏感，可以避免某些软件或第三方包因为 Windows 文件系统的大小写不敏感而导致的问题

```powershell
fsutil.exe file setCaseSensitiveInfo $env:SCOOP enable
fsutil.exe file setCaseSensitiveInfo $env:SCOOP_GLOBAL enable
```

我曾经就遇到过某个 Python 包因为大小写不敏感而导致的问题，这个命令可以避免这种问题，不过由于大部分软件正确适配了 Windows 大小写问题，大多数情况下不会遇到此问题

### 设置杀毒软件白名单

此选项是可选的，杀毒软件的实时扫描会拖慢 Scoop 的运行速度，你可以将 Scoop 的安装目录添加到白名单中。

请注意，Scoop 本身是安全的，但是由于 Scoop 的工作方式，会下载一些软件包，若关闭杀毒软件，请自行辨别与承担可能出现的安全问题。

#### 安装 Scoop

在此之前，你需要确定你的网络能够正常访问 GitHub，否则会安装失败。

参考[官网](https://scoop.sh/)的安装方式，打开 PowerShell，输入以下命令：

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```

现在 Scoop 就已经安装好了，你可以开始使用了！

### 使用

#### 基本使用

在开始使用前，你需要安装一些基础软件，顺便来了解第一个也是最常用的 Scoop 命令 `install`：

```powershell
scoop install 7zip git aria2
```

- `7zip` 是解压下载到的软件包
- `git` 是同步远程 bucket 更改
- `aria2` 是加速下载

这三个软件是 Scoop 的基础软件，安装后你就可以使用 Scoop 来安装其他软件了。

#### bucket

在继续之前，我们需要先了解 bucket 的概念：

bucket 是 Scoop 的软件仓库，类似于 Linux 下的软件源，Scoop 会从 bucket 中查找软件包，bucket 中的一个个 manifest 会包含软件的元数据，比如软件的名称、版本、下载地址等。官方维护了许多 bucket，你可以通过 `scoop bucket known` 来查看官方维护的 bucket。

推荐安装的 bucket：

- [Main](https://github.com/ScoopInstaller/Main): 包含许多常用的命令行软件
- [extras](https://github.com/ScoopInstaller/Extras): 包含许多常用的图形界面软件
- [Versions](https://github.com/ScoopInstaller/Versions): 包含许多软件的历史版本
- [dorado](https://github.com/chawyehsu/dorado): 包含许多官方库中没有包含的软件
- [cetacea](https://github.com/cscnk52/cetacea): 由我维护的 bucket，作为其他 bucket 的补充

你可以使用以下命令来添加这些 bucket：

```powershell
scoop bucket add main
scoop bucket add extras
scoop bucket add versions
scoop bucket add dorado https://github.com/chawyehsu/dorado
scoop bucket add cetacea https://github.com/cscnk52/cetacea
```

#### 进阶使用

##### 使用 `reset` 命令快速切换版本

假设你安装了多个版本的 Python，你默认是使用 python3 的，但是当前的项目需要使用 python2，你可以使用 `reset` 命令来快速切换版本：

```powershell
scoop reset python2
```

##### 使用 `hold` 命令锁定版本

部分情况下可能需要锁定版本，不再更新，你可以使用 `hold` 命令来锁定版本：

```powershell
scoop hold python2
```

##### 其余常用命令

```powershell
scoop help                         # 查看帮助
scoop info <app>                   # 查看APP信息
scoop install <app>                # 安装APP
scoop uninstall <app>              # 卸载APP
scoop list                         # 列出已安装的APP
scoop status                       # 检查软件更新
scoop update                       # 更新Scoop自身
scoop update <appName1> <appName2> # 更新指定应用
scoop update *                     # 更新所有应用（需在apps目录下操作）
scoop bucket known                 # 列出所有已知bucket
scoop bucket add <bucketName>      # 添加bucket
scoop cache rm <app>               # 移除应用缓存
scoop cache rm -a                  # 移除所有缓存
scoop cleanup <app>                # 删除旧版本
```

## Scoop 的缺点

### 极慢的搜索速度

因为 Scoop 是通过搜索本地 json 文件的形式去搜索软件的，但是因为 Scoop 软件个数的急速增长，这种搜索方式已经是非常慢的了，在某些条件下，搜索一个软件需要大约半分钟，这对于一个搜索功能来说是非常慢的，不过 Scoop 社区也在努力改善这部分的体验：

#### Scoop-search

[Scoop-search](https://github.com/shilangyu/scoop-search)，是一个 `scoop search` 命令的代替产品，它使用了更快的搜索引擎，可以大大提高搜索速度，你可以通过以下命令来安装：

```powershell
scoop install scoop-search
```

通过对比原命令和 scoop-search 的速度，可以看出 scoop-search 的速度要快很多：

```sh
❯ hyperfine --warmup 1 'scoop-search google' 'scoop search google'
Benchmark 1: scoop-search google
  Time (mean ± σ):      60.3 ms ±   3.5 ms    [User: 91.2 ms, System: 394.2 ms]
  Range (min … max):    55.1 ms …  73.8 ms    49 runs

Benchmark 2: scoop search google
  Time (mean ± σ):     21.275 s ±  2.657 s    [User: 9.604 s, System: 11.789 s]
  Range (min … max):   19.143 s … 27.035 s    10 runs

Summary
  scoop-search google ran
  352.74 ± 48.49 times faster than scoop search google
```

同时，在 Windows 上为众多软件提供 GUI 的 [UniGetUI](https://github.com/marticliment/UnigetUI)，也默认要求安装 scoop-search 来提升搜索速度。

#### 使用 SQLite 的本地搜索

在 Scoop [v0.5.0](https://github.com/ScoopInstaller/Scoop/releases/tag/v0.5.0) 中，Scoop 引入了 SQLite 数据库，用于加速搜索，你可以通过以下命令来初始化 SQLite 数据库：

```powershell
scoop config use_sqlite_cache true
```

等待数据库初始化完成之后，你便可以享受飞快的搜索速度了。

但是，当前的 SQLite 数据库并不会删除已经弃用的 json 数据，比如曾经安装过却卸载了的 bucket 或是已经被弃用的 manifest 文件，当前并没有一个很好的解决办法，你可以通过手动删除 Scoop 目录下的 `scoop.db` 文件，再重新初始化数据库来暂时解决这个问题。

### 社区活跃度不高

Scoop 的社区活跃度很差，我开始使用 Scoop 大概是 22 年 12 月，当时 11 月刚刚发布完 v0.3.1，之后每次运行 `scoop update` 时，我都没有看到 `Updating scoop` 下有任何 scoop 的更新，直到 24 年 4 月，中间隔了整整 17 月才迎来了 v0.4.0 的更新。

[Scoop Installer](https://github.com/ScoopInstaller) 的 GitHub 组织成员也大多不再参与管理 Scoop 的相关事务，最开始我给 Scoop 贡献包的时候，经常需要一个 PR 等好多天才会被合并，后来我便慢慢开始自行维护属于自己的库，这也是我创建了 [cetacea](https://github.com/cscnk52/cetacea) 这个 bucket 的原因。而我也是在刚刚才正式合并了我在六个月前提交的 [PR](https://github.com/ScoopInstaller/Versions/pull/1918)，以后也应该不会再为 Scoop 贡献包了，转而维护自己的 bucket。

## Reference

写作过程中参考了如下文章，在此表示感谢：

- <https://zhuanlan.zhihu.com/p/463284082>
- <https://sspai.com/post/52496>
- <https://blog.dejavu.moe/posts/windows-scoop/>
