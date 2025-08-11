+++
title = "第 128 个 Pull request"
date = 2025-08-11T13:10:21Z
taxonomies.categories = ["life"]
taxonomies.tags = ["GitHub", "Open source"]
+++

我的 GitHub Pull request 总数来到了第 128 个，看到这个数字，总想写点什么。

# 为什么参与开源

首先，先说一下为什么想参与开源贡献吧：在大学之前，我都是在用一个已经非常跟不上时代的手机，所以对我来说，选择一个软件时，轻量、简洁甚至排在了实用性之前，因此我经常会去探索一些软件精简版本或替代品。探索的过程中，经常会遇到别人推荐开源软件，下载之后确实体验很好，~~也能白嫖~~，自那时起，开源软件，在我心里，就是安全、优雅软件的代名词。并且也会去看看下面的 README，每次看到下面的欢迎参与贡献与头像墙，就会想着去做点什么开源贡献，于是这颗种子就这么种下了。

# 第一个 PR

大一的时候，我电脑上的很多软件都是我自己从开源社区挑选手动下载来的，而我自己又是个更新强迫症，所有软件系统都想用最新的稳定版，所以当时的解决办法是手动 watch 我需要的软件 release，有更新的时候手动装一下，前期软件还少，后来越来越多，也看不过来了。然后在此期间也折腾了 Linux，就想为什么 Linux 下就能一行 install 装了，Windows 就不行呢？看到了网上推荐 [Chocolatey](https://chocolatey.org)，我就下载安装了，可我也忘了是什么原因，反正感觉 Chocolatey 并不是那么优雅，就卸载了。后来看到了 [CS 自学指南](https://csdiy.wiki)[^1]，看到里面推荐了 [Scoop](https://scoop.sh)，下载安装看了 Scoop 的目录结构和命令设计后，感觉这就是我想要的 Windows 包管理器。但当时的我还是对这种纯命令行管理软件的方式有点不顺手，所以只是慢慢迁移了部分软件到 Scoop 去。

之后想在电脑上用买了高级版的[纯纯写作](https://writer.drakeet.com)（也是我现在写这篇文章的工具），尝试下电脑写作，却发现 [dorado](https://github.com/chawyehsu/dorado) 库里对纯纯写作的更新不及时，就去看了看 scoop 的包设计，没完全看懂，但好像把链接改成最新版应该就可以了，然后提起了第一个[PR](https://github.com/chawyehsu/dorado/pull/674)，记不得是什么原因了，好像是 CI 没过，还是等不住 chawyehsu 合并，最后我把那个 PR 给关了。是的，我的第一个 PR 没被合并进去。

现在看来，当时的我真的有很多细节纰漏：直接拿主分支去提 PR，不好好写 commit message 等等，然后我印象最深的是前几个 PR，那时候听别人推荐，安装了那个 pull[bot]，然后我还是用主分支提的 PR，所以前几个 PR 每次都是第二天 pull bot 就自动 force push，把我的更改给覆盖了，我当时还不明白这些，~~还以为 bot 阻止我做开源贡献~~,于是这些事情就搁置起来，继续还是老实上课了。

# 第一个成功的 PR

和很多人一样，我的第一个被合并的 PR 也是 typo，是在一个[开源安卓软件列表](https://github.com/xlucn/oh-my-foss-android)。看时发现部分链接和名词没对上号，然后花了一点时间校对了所有的链接，就提起了 [PR](https://github.com/xlucn/oh-my-foss-android/pull/5), 当了次 Markdown Engineer。xlucn 人很好，不到两个小时就回复、合并、发版了，那是我第一次看到自己的 ID 被标黄[^2]放在 release note 里，"light my day"[^3].

# 第 128 个 PR

[第 128 个 PR](https://github.com/simple-icons/simple-icons/pull/13684) 则看起来轻车熟路多了，是给 [Simple Icons](https://simpleicons.org) 做了个新的 [Rust crate](https://crates.io/crates/simpleicons-rs)。做这个最初原因是看到某些简历上每个技术前面都有个对应的小图标，正好前一阵为 Folo 把图标提交到 Simple Icons，对 Simple Icons 这个库有一定了解。因为我的简历是使用 typst 写的，typst 支持以文件形式引入 SVG，可这也太不优雅了，就想着给 Typst 做个 Simple Icons 插件，最初版本是直接把 Simple Icons 仓库作为 Git 子模块引入，其实还是不优雅，但 typst 插件还是限制太多了，于是做到这个版本先放着了。

后来偶尔搜 typst plugin 看到 [based](https://github.com/EpicEricEE/typst-based) 这个库竟然是用 Rust WebAssembly 写的，想到去年暑假抽时间学了一点点的 Rust，还跟着敲了 [hecto](https://github.com/cscnk52/hecto) 这个项目，做点简单的 Rust 项目应该不成问题。在 crates.io 上搜了下，发现 Rust 生态里的 Simple Icons 要么年久失修，要么功能不完善。想着既然不行那就我整一个，参照这个包的 Python 脚本，写了个 Rust 版本，正好练练 Rust，然后用了几天写了点 Rust 代码，把基本的包生成写完了，就提了这第 128 个 PR，本来想等下 Simple Icons 那边维护者是什么反应我再发个版，暂时没回复，我想着还是先发了，于是今天下午，所有都准备好之后，我敲下了那句 `cargo publish`，发现 Rust 的工具链真的太棒了，一个 cargo 基本完成所有东西，也非常期待 VoidZero 在做的 Vite+,给 JavaScript 生态带来 cargo 的体验。

# 回望

回望我这 128 个 PR，整体来说，做的东西都很简单，没什么难度，更多情况下，只是我需要某个功能或者发现了某个 bug，去提了个 PR。这几天，脑海里也一直飘着几个想法，所以下一步，我应该去尝试去实现这几个想法，做些更难的，属于自己的事情。

感谢在这 128 个 PR 里面遇到的很多人，他们都给了我很多建议或力量，让我去做我自己想做的事情。

[^1]: 里面也看到了推荐我很熟悉的 RSSHub，Cubox，Obsidian，简悦等软件

[^2]: GitHub 会对自己的名字标黄

[^3]: 写到这里突然想起了《LaLaLand》里的歌词，乱入下
