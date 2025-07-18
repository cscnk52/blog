+++
title = "与 DIYgod 的相遇"
description = "和最爱的 DIYgod 交流过了，很感动"
date = 2025-06-22T02:17:52Z
taxonomies.categories = ["Life"]
taxonomies.tags = [ "Folo", "Connection", "Open Source"]
+++

{% quote(cite="DIYgod") %}
写代码是热爱，写到世界充满爱。
{% end %}

正如我在上一篇[《一些冥冥的际遇》](../some-magic-connections) 引用的乔布斯名言："Connect the dots"一般。人生就是由不同的点串联成线，而这些线又交织成一幅幅美好的画面。

而作为上一篇的续集，这理所当然是一个线交织成面的故事————其实我也没想到这么快就能写续集，感谢我最爱的 @DIYgod.

---

2020 年，彼时的我还是一个高中生。众所周知的原因，我们开始了上网课。我也有了更多的时间接触电子设备，也正如那篇[《写在 RSSHub 贡献之后》](../rsshub)中提到的：

> 再回到四年前，那时的我会在网上搜索很多文章来看，久而久之，便对红底白字的“π”有了印象，这便是[少数派](https://sspai.com)，翻到少数派旗下“一派”播客中提到了 RSS 订阅，然后看到了那篇大名鼎鼎的[《高效获取信息，你需要这份 RSS 入门指南》](https://sspai.com/post/56391)，便迷上了这种开放，自行定制的信息获取方式。使用 RSS 的过程中，自然而然，我也发现了很多的优质内容与创作者，其中就包含 RSSHub 项目，用久之后，看着 README 里面众多贡献者，我想着——我——是否也能出现在这里？

我很想去为 RSSHub 这个项目去贡献属于我自己的力量，看到每天刷新的订阅源，背后的代码是我写的，一种成就感油然而生。

可事与愿违，当时作为一个高中生的我，硬件上来说没有电脑，时间上来说学业压力大，自然是做不了贡献。我只能把这个理想深埋在心底，等待某一天再挖出来……

2022 年，和很多普通高中生一样，我毕业了，考上了一个即不高、也不低的学校，进入了计算机专业，也理所当然地获得了一台电脑，打下第一次 Hello World，敲下第一次 Git commit……[^1]

我还记得大一晚自习时，我想起我这个小小愿望，第一次 clone 下 RSSHub 的源码、第一次把开发版跑起来的感觉，可当时的我，看着从来没有学过的 JavaScript，无奈，又一次埋藏在心底。

几年间，我也一直关注着 @DIYgod 和 RSSHub 的发展：维护 Twitter 路由的正常运行、xLog 与 RSS3 的问世、RSSHub Radar 的各平台发布、RSSHub 的贡献者在 Starknet 的空投范围内，RSSHub 的重构，RSSHub 贡献者可以提前拿到 Folo 的邀请码……

可————我感觉有心无力：我也想领领空投，我也想在那贡献者的头像墙里看见我的名字，我也想第一批拿到 Folo 的邀请码，我也想……可……我看不懂，很长一段时间里，我都失望了，我不知道我的这个梦想该怎么实现。我想，可我……看不懂

正如每个烂套的故事一般：低谷之后便是光明，可既然看到这篇文章了，那说明我成功了。但还有很多没有资格写出一篇文章来纪念的理想，我想：这些，才是常态。

去年七月底，我看到了 Folo 公测的消息。我不是 RSSHub 的贡献者，可我还是腆着脸去私信了 @DIYgod，答案当然是没有回复，很正常。后来，我在 Twitter 上关注了很多抽奖 Folo 邀请码的信息，无一例外，对我这个中奖绝缘体来说，一个都抽不到。后来关注了一个博主，（很抱歉，我忘记是哪个博主了，我翻了半天 Telegram 也没找到），去 Telegram 群里，还是抽奖，继续绝缘体。不过我很热心，去群里解答别人问题，然后群主发现我没邀请码，给了我一个码，这才开始使用 Folo。

11 月，学校里的 Python 课程需要完成一个大作业，要求主题是爬虫，我突然想起了 RSSHub：RSSHub 不就是爬虫嘛，我于是就想以这个主题来写，然后在 AI 的帮助下，我慢慢 Debug，终于算是把整个流程跑通了。那次报告本来是定在星期三，但老师记错了，应该在星期五。然后在那个本来星期三汇报的下午，我在 AI 帮助下摸索清楚了 RSSHub 的一些规范，也终于提交了第一个路由类的 PR（之前提过一个修 Radar 的 PR），然后我本来想的是如果星期五上课之前这个 PR 被合并了，我就糅杂在里面讲了，可，并没有。因为我本身的 I 人特质，我上去了很紧张，结结巴巴地，本来脑子里想了很多词都忘光了，开着提前用 [Slidev](https://cn.sli.dev/) 制作的 [PPT](https://github.com/cscnk52/hrbustnews2rss/blob/main/slides/slides-export.pdf)，快速讲了几下代码就说完了，在最后的 Reference 部分，我放进去了那篇[《一个六岁开源项目的新生》](https://diygod.cc/6-year-of-rsshub)，我讲解完了，老师看了看屏幕上的东西，没有像其他组那样多问什么。据同学说，老师说这是近几年学生里做的最好的，可我当时太紧张了，什么也没听清，便草草下台了。

在有了第一次 PR 后，我便一发不可收拾，期末考试的间隙也在提 PR。回家后，上午去驾校，回家就继续处理 Issue，断断续续提交了很多个 PR，现在也在贡献者头像里处在第一排的位置。

---

再回到二月，面对着我一点儿都没学过的 React，我一次次在 Folo 的代码下敲出 `pnpm dev`，却一点也看不懂代码。后来，看到一个图片类的 RSS enclosure 被渲染整了音频封面的样子，我察觉到这肯定是某个 if 条件写错了，于是我打开浏览器开发者工具，慢慢定位，然后再通过 AI 去找，不过这个问题最后定位到还是很简单的，就改动了一行代码，这是我在 Folo 的[第一个 PR](https://github.com/RSSNext/Folo/pull/2813)。后来，还有几个问题，慢慢研究代码，慢慢学习 React，慢慢去看一个个的 Issue，也提了好多个 PR 了，现在你可以在 Folo 的 GitHub 主页就看到我的头像在 contributor 下。

---

前几天，在 B 站看到了 Litomore 在直播，注意到他在维护 simple-icons，然后想到 Folo 的图标好像也能提交到 simple-icons，就在直播间问了下 Litomore 是用什么软件做图标的。之后边问 AI 边学，然后遇到 Folo 原来的图标做的很乱，和 reviewer 好几个来回才发现图标需要重绘，借着重绘的契机，需要问一下 DIYgod 关于图标重绘的意见，然后顺便加一下大佬的微信，算是给自己圆个梦。

通过微信后，DIYgod 第一句就发了个仰望大佬的表情包，我不知道为什么，看到这里我眼眶里泪水打转了：

> 我：大佬你好
>
> 我：😭😭😭
>
> 我：追星成功了
>
> DIYgod：大佬好
>
> DIYgod：谢谢你那么多 pr
>
> DIYgod：好人一生平安

看到这里，我真的止不住哭出来了，想想五年前的我自己，好像还只是一个普普通通的高中生，可是现在却成了我所梦想的开源项目的 contributor。我后面实在哭不住了，yy 安慰我说：

> 写代码最开心了

是啊，写代码最开心了。

可我不知道怎么去写下这篇文章的结尾，正如我听了很多遍的那期[《S1E10 冬天好》](../bon-iver)一般：Bon Iver 在那个小木屋里离群索居三个月，创作出了那张堪称经典的[《For Emma, Forever ago》](https://en.wikipedia.org/wiki/For_Emma,_Forever_Ago)。在那篇播客的最后，重轻老师引用了 Bon Iver 纹身征稿启事中的一段话：

> 这是一件对我非常重要的事，我不知如何准确地解释。它只是一个电视剧，但是它诡异的向我解释了我的生命，Cicely 就是这个隐喻。

我也不知如何准确地解释，所以我引用 @DIYgod 个人简介作为这篇文章的结尾：

> 写代码是热爱，写到世界充满爱。

[^1]: 这里的经历很多，还是想挖个坑（突然发现我怎么这么爱挖坑
