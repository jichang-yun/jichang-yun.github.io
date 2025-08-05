---
id: 104689
title: '2024 最新苹果 iOS 小火箭 Shadowrocket 配置规则'
date: '2024-12-20T21:23:40+08:00'
author: jichanghui
layout: revision
guid: 'https://jichanghui.com/?p=104689'
permalink: '/?p=104689'
---

Shadowrocket 俗称小火箭，是相当好用的苹果 iOS 手机平板科学上网工具，我分享下我自己常用的小火箭规则，Shadowrocket-ADBlock-Rules。原作者已停止维护 我看到 Github 上有其他童鞋根据原有项目来更新规则，使用 Python 按照一定的规则和模板定期自动生成，所有规则都会在每天北京时间 8:00 更新发布。本规则只提供给大家用于学习、工作和娱乐。如果你是极端政治人士或已被洗脑，请立即离开。

## 高速稳定高性价比的老牌机场推荐

\[table id=45 /\] ## 规则使用方法

- 在小火箭应用中，进入配置页面，点击右上角加号，将规则文件地址粘贴到 url 处，点击“下载”即可。
- 最好让小火箭断开并重新连接一次，以确保新的规则文件生效。

项目仓库：[小火箭规则Github仓库](https://github.com/Johnshall/Shadowrocket-ADBlock-Rules-Forever)

项目仓库经常打不开，可以直接复制下面的对应规则到小火箭中即可，按照上面的使用方法。

## [黑名单过滤 + 广告](https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_top500_banlist_ad.conf)

黑名单中包含了境外网站中无法访问的那些，对不确定的网站则默认直连。

- 代理：被墙的网站（GFWList）
- 直连：正常的网站
- 包含广告过滤
- 规则地址：https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr\_top500\_banlist\_ad.conf

## [白名单过滤 + 广告](https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_top500_whitelist_ad.conf)

白名单中包含了境外网站中可以访问的那些，对不确定的网站则默认代理。

- 直连：top500 网站中可直连的境外网站、中国网站
- 代理：默认代理其余的所有境外网站
- 包含广告过滤
- 规则地址：https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr\_top500\_whitelist\_ad.conf

## [黑名单过滤](https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_top500_banlist.conf)

现在很多浏览器都自带了广告过滤功能，而广告过滤的规则其实较为臃肿，如果你不需要全局地过滤 App 内置广告和视频广告，可以选择这个不带广告过滤的版本。

- 代理：被墙的网站（GFWList）
- 直连：正常的网站
- 不包含广告过滤
- 规则地址：https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr\_top500\_banlist.conf

## [白名单过滤](https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_top500_whitelist.conf)

现在很多浏览器都自带了广告过滤功能，而广告过滤的规则其实较为臃肿，如果你不需要全局地过滤 App 内置广告和视频广告，可以选择这个不带广告过滤的版本。

- 直连：top500 网站中可直连的境外网站、中国网站
- 代理：默认代理其余的所有境外网站
- 不包含广告过滤

## [国内外划分 + 广告](https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_cnip_ad.conf)

国内外划分，对中国网站直连，外国网站代理。包含广告过滤。国外网站总是走代理，对于某些港澳台网站，速度反而会比直连更快。

规则地址：https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr\_cnip\_ad.conf

## [国内外划分](https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_cnip.conf)

国内外划分，对中国网站直连，外国网站代理。不包含广告过滤。国外网站总是走代理，对于某些港澳台网站，速度反而会比直连更快。

规则地址：https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr\_cnip.conf

## [直连去广告](https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_direct_banad.conf)

如果你想将 SR 作为 iOS 全局去广告工具，这个规则会对你有所帮助。

- 直连：所有请求
- 包含广告过滤
- 规则地址：https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr\_direct\_banad.conf

## [代理去广告](https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_proxy_banad.conf)

如果你想将 SR 作为 iOS 全局去广告 + 全局翻墙工具，这个规则会对你有所帮助。

- 直连：局域网请求
- 代理：其余所有请求
- 包含广告过滤
- 规则地址：https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr\_proxy\_banad.conf

## [回国规则](https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_backcn.conf)

提供给海外华侨使用，可以回到墙内，享受国内的一些互联网服务。

- 直连：国外网站
- 代理：中国网站
- 不包含广告过滤
- 规则地址：https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr\_backcn.conf

## [回国规则 + 广告](https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_backcn_ad.conf)

提供给海外华侨使用，可以回到墙内，享受国内的一些互联网服务。

- 直连：国外网站
- 代理：中国网站
- 包含广告过滤
- 规则地址：https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr\_backcn\_ad.conf

## [仅去广告规则](https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr_ad_only.conf)

仅包含去广告规则，不包含代理/直连规则。用于与其他规则联用。

- 仅包含去广告规则，不包含代理/直连规则。无任何其他配置。
- 规则地址：https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/sr\_ad\_only.conf

## [懒人配置](https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/lazy.conf)

不折腾，开箱即用。

- 配置简洁
- 规则覆盖范围广
- 国内外常用app单独分流
- 规则地址：https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/lazy.conf

## [懒人配置-含策略组](https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/lazy_group.conf)

不折腾，开箱即用。下载规则后可在 i -&gt; 代理分组 中自行配置。

- 配置简洁
- 规则覆盖范围广
- 国内外常用app单独分流
- 添加自动切换延迟最低节点类型
- 通过「代理分组」灵活调整流媒体分流策略
- 规则地址：https://johnshall.github.io/Shadowrocket-ADBlock-Rules-Forever/lazy\_group.conf