---
layout: post
title:  "IFTTT 和 Instapaper 来收集和整理资讯"
date:   2018-04-16
categories: 教程
---

上篇文章提到了资讯过多的困扰。这篇文章就基于上篇文章提到的“对资讯源的管理”来谈谈「如何来管理你的资讯源」。

看了这篇文章你可以学到：
* 让想要的资讯主动的来找你
* 让资讯的收集和存储自动化

1984 中有一句话是：__谁控制了过去就控制了未来；谁控制了现在就控制了过去。__
而现在的时代更像是：__谁控制了媒体，谁就控制了舆论，谁就控制了思想。__

当你的资讯来源比较单一的时候，就容易被错误的信息误导。丰富自己的资讯源会有利于自己从众多杂乱，甚至从掩人耳目的讯息中找到有价值的那些。

## 概念介绍（可以跳过）
##### RSS 是什么？
[RSS][RSS]（简易信息聚合）是一种消息来源格式规范，用以聚合经常发布更新数据的网站。英文全名是 Really Simple Syndication“简易信息聚合”。想要了解更多的同学可以看[这里][RSS]。

简而言之 RSS 就是一种定制个性化推送信息的服务，把你需要的一些信息送到你的口袋。而且基本上现在所有的资讯类网站都支持了 RSS。

总结一下，RSS 的好处有
* 收集资讯主动推送给你
* 不受“墙”的限制

##### 什么是 IFTTT？
[IFTTT][IFTTT]，是一个新生的网络服务平台，通过其他不同平台的条件来决定是否执行下一条命令。即对网络服务通过其他网络服务作出反应。IFTTT得名为其口号“if this then that”。
IFTTT 可以玩的东西有很多，但是这里只谈论通过 IFTTT 来触发 RSS 并推送至 Instapaper。

##### 什么是 Instapaper?
[Instapaper][Instapaper] 一款 "之后再读" 的应用。最近也是刚好走过了十年，一直是个人非常喜欢的一个小而美的应用。虽然在 [17 年被 Pinterest 收购了][instapaper_pinterest]，但幸运的是感觉产品还是没有被他们带错方向，近期的一些优化都是往用户体验好的方向走。

## 步骤

##### 寻找网站的 RSS 链接
以我的网站为例，打开右上角的“汉堡”按钮后，点击 RSS。接着就打开了 feed.xml 的文件。你会发现里面有很多的代码，不用管文件里面的内容，之后只要复制浏览器上面的 https://sayidhe.me/feed.xml 网址即可。

##### 注册 Instapaper
![Instapaper][image1]

##### 注册 IFTTT
注册完成之后，选择 My Applets > New Applet
![New Applet][image2]

##### Choose a service
这里选择 RSS
![Choose a Service][image3]

##### Choose trigger
这里选择 New feed item
![New feed item][image4]

##### Complete trigger fields
这里填入前面复制的 RSS 地址
![RSS][image5]

接下来可以看到之前 this 部分已经变成 RSS 的图标了。接着，点击 That。
![If This Than That][image6]

##### Choose action service
这里选择 Instapaper（这里需要获取 Instapaper 的权限，用前面注册完成的 Instapaper 来登陆）。
![Choose action service][image7]

##### Choose action
点击 Save item
![Save item][image8]

##### Complete action fields
接下来，可以默认点击 Create action。如果你在 Instapaper 中有新建了不同的文件夹，则可以在此步骤 Which folder 的下拉菜单中选择，该资讯源在 Instapaper 中存放的文件夹。
![Complete action fields][image9]

##### Review and finish
点击 Finish 就完成了。
![Review and finish][image10]

这样，之后博客一有更新，你就能第一时间在 Instapaper 中收到了。

下面推荐一些资讯源：

__Design__
* UI/UX Design: https://medium.com/feed/ux-ui-design
* User Experience Design: https://medium.com/feed/user-experience-design-1
* 设计师 Julie Zhou: https://medium.com/feed/@joulee
* 设计师 Van Schneider: https://medium.com/feed/desk-of-van-schneider
* Type Is Beautiful: http://www.typeisbeautiful.com/feed/

__技术/思维__
* Smashingmagazine: http://www.smashingmagazine.com/feed/
* 编程随想：http://feeds2.feedburner.com/programthink

__新闻__
* 端传媒：http://feeds.initium.news/theinitium
* 纽约时报：https://cn.nytimes.com/rss.html

__知乎__
* 知乎精选：https://www.zhihu.com/rss
* 知乎日报：http://zhihurss.miantiao.me/dailyrss

## 最后
会了上面的之后，就可以自己研究一下进阶玩法，如
* Instapaper 支持推送至 Kindle 的服务
* 用 IFTTT 保存 Instapaper 中喜欢的文章和 Highlight 至 Evernote

有兴趣的继续摸索吧。

[RSS]: https://zh.wikipedia.org/wiki/RSS
[IFTTT]: https://ifttt.com/
[instapaper]: https://instapaper.com/
[instapaper_pinterest]: https://blog.instapaper.com/post/149374303661
[image1]: /assets/img/ifttt_instapaper/instapaper.png
[image2]: /assets/img/ifttt_instapaper/if_this_than_that.png
[image3]: /assets/img/ifttt_instapaper/if_this_than_that_step1.png
[image4]: /assets/img/ifttt_instapaper/if_this_than_that_step2.png
[image5]: /assets/img/ifttt_instapaper/if_this_than_that_step2_1.png
[image6]: /assets/img/ifttt_instapaper/this_this_than_that_2.png
[image7]: /assets/img/ifttt_instapaper/if_this_than_that_step3.png
[image8]: /assets/img/ifttt_instapaper/if_this_than_that_step4.png
[image9]: /assets/img/ifttt_instapaper/if_this_than_that_step5.png
[image10]: /assets/img/ifttt_instapaper/if_this_than_that_step6.png
