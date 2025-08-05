---
id: 7214
title: 'Lean 大神 OpenWRT 固件精简版编译教程'
date: '2022-03-22T21:13:27+08:00'
author: jichanghui
layout: post
guid: 'https://affvps.com/?p=7214'
permalink: /lean-%e5%a4%a7%e7%a5%9e-openwrt-%e5%9b%ba%e4%bb%b6%e7%b2%be%e7%ae%80%e7%89%88%e7%bc%96%e8%af%91%e6%95%99%e7%a8%8b/
classic-editor-remember:
    - classic-editor
wb_bsl_daily_push:
    - '0'
wb_sst_seo:
    - 'a:3:{i:0;s:0:"";i:1;s:0:"";i:2;s:0:"";}'
baidutui:
    - ''
url_in_baidu_ymd:
    - '2022-09-22 00:05:31'
fromname_value:
    - 佐志
fromurl_value:
    - jinbo123.com
url_in_baidu:
    - '2'
views:
    - '12173'
categories:
    - 机场推荐
---

网上有很多编译 OpenWrt 固件的教程，我自己整理一下方便自已往后使用，并且提供给想自已编译 OpenWRT 固件的朋友。OpenWrt 源码来自 Lean 大神。 自已编译软路由 OpenWrt 固件可以满足自己需求，一个符合自己需求，简洁及稳定的固件。有很多插件对于我们有时候没什么用。

## [高速稳定便宜机场服务推荐](https://affvps.com/2931.html)[老牌机场](https://affvps.com/2931.html)

\[table id=45 /\] ## 编译 OpenWrt 固件环境

事先需要一台安装好 Ubuntu 64 位操作系统的 VPS。 需要注意以下三点： 1. 不要用 root 用户 git 和编译，安装好操作系统后。先新建一个用户
2. 使用 SSH 连接服务器后进入非Root用户帐号进行代码操作
3. 国内用户编译前最好准备好梯子：[高性价比的SS/SSR/V2ray/Trojan等老牌高速低价稳定便宜机场服务推荐](https://affvps.com/2931.html)
4. 默认登陆IP 192.168.1.1, 密码 password

## OpenWrt 固件精简版

本固件只保留以下常用插件，无广告： > LuCI —&gt; Applications —&gt; luci-app-accesscontrol #访问时间控制 LuCI —&gt; Applications —&gt; luci-app-arpbind #IP/MAC绑定 LuCI —&gt; Applications —&gt; luci-app-autoreboot #定时重启 LuCI —&gt; Applications —&gt; luci-app-filetransfer #文件传输（可web安装ipk包） LuCI —&gt; Applications —&gt; luci-app-firewall #添加防火墙 LuCI —&gt; Applications —&gt; luci-app-sfc #最新版 Turbo ACC网络加速 LuCI —&gt; Applications —&gt; luci-app-nlbwmon #网络带宽监视器 LuCI —&gt; Applications —&gt; luci-app-ramfree #释放内存 LuCI —&gt; Applications —&gt; luci-app-sqm #流量智能队列管理（QOS） LuCI —&gt; Applications —&gt; luci-app-55R饮料 #不忘初心 LuCI —&gt; Applications —&gt; luci-app-upnp #通用即插即用UPnP（端口自动转发） LuCI —&gt; Applications —&gt;luci-app-wol 网络唤醒 Extra packages —&gt; ipv6helper #支持 ipv6

固件的初始访问地址：192.168.1.1；用户名：root 登陆密码：password img格式下载地址：<https://drive.google.com/file/d/16BuXadbBfM3lpcauUFR7GJ1B9O2LiLn7/view?usp=sharing>vmdk格式载地址：<https://drive.google.com/file/d/1CDSgZ5pp9fVPrJ7OdF0LeUBte-zXJZk2/view?usp=sharing>## 一、升级及安装必要组件

命令行输入 `sudo apt-get update` 后回车，然后输入: ```
sudo apt-get -y install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf automake libtool autopoint
```

## 二、克隆lean的源代码到本地

```
git clone https://github.com/coolsnowwolf/lede
```

## 三、开始定制与编译

进入克隆下来的目录后执行下面的命令 ```
1. cd lede/
2. ./scripts/feeds update -a
3. ./scripts/feeds install -a
4. make menuconfig
```

敲下回车键后，稍等片刻进入如下菜单 ![fe7201607462b61](https://affvps.com/wp-content/uploads/2022/03/fe7201607462b61.jpg "fe7201607462b61")进入Target System和Subtarget勾选你需要编译的平台，默认的是X86，并且是64位的，所以你需要选择自助选择。 ![4b581f8ae7a783f](https://affvps.com/wp-content/uploads/2022/03/4b581f8ae7a783f.jpg "4b581f8ae7a783f")进入 Target Images 勾选你需要的固件格式等，img、vmdk等保持默认 接下来是最重要也是最核心部份，选择编译的插件。进入LuCI–&gt;Applications内选中你需要的插件。 ![58a8edfac2bafaf](https://affvps.com/wp-content/uploads/2022/03/58a8edfac2bafaf.jpg "58a8edfac2bafaf")![0b79434d6ab012b](https://affvps.com/wp-content/uploads/2022/03/0b79434d6ab012b.jpg "0b79434d6ab012b")![72367995857284f](https://affvps.com/wp-content/uploads/2022/03/72367995857284f.jpg "72367995857284f")这里按Y勾选，N取消勾选，M编译而不安装。连按两次`Esc键`返回上一界面。( ‘\*’ 代表编入固件，‘M’ 表示编译成模块或者IPK包， ‘空’不编译 )。 关于 Applications 添加插件应用说明，请看这一篇文章：[OpenWrt 编译 LuCI -&gt; Applications 添加插件应用说明【2019.09.22】](https://www.right.com.cn/forum/thread-344825-1-1.html)。 勾选完需要的插件后就可以退回第一个界面按`Y`保存退出，保存按默认的文件名称(.config）保存即可，不需要修改。编译会根据.config的内容编译，想要恢复到初始配置删掉.config文件即可。 最后选好你要的路由，输入： `make -j1 V=s`注意：-j1 后面是线程数。第一次编译推荐用单线程，国内请尽量全局科学上网。 即可开始编译你要的固件了。首次编译大概需要两三个小时，之后基本上只需要十多分钟既可。编译过程中不要断开SSH。若断开，请清除整个lede 文件夹重新开始。 编译完成后，前往：/home/lede/bin/targets/x86/64这个目录获取编译成功的固件。 ![7a0fb5fdb92d062](https://affvps.com/wp-content/uploads/2022/03/7a0fb5fdb92d062.jpg "7a0fb5fdb92d062")## 编外：给openwrt固件添加Passwall插件的方法

有人喜欢Lienol的Passwall的插件，那以下是给openwrt固件添加Passwall插件的方法。 1、克隆lean的源代码到本地； ```
git clone https://github.com/coolsnowwolf/lede
```

2、然后 cd lede 进入目录； 3、添加 src-git lienol https://github.com/Lienol/openwrt-package 到 OpenWRT源码根目录feeds.conf.default文件。feeds.conf.default 文件在lede根目录中，使用文本编辑器打开既可。 4、执行下面的命令 ```
./scripts/feeds clean
./scripts/feeds update -a
rm -rf feeds/lienol/lienol/ipt2socks
rm -rf feeds/lienol/lienol/shadowsocksr-libev
rm -rf feeds/lienol/lienol/pdnsd-alt
rm -rf feeds/lienol/package/verysync
rm -rf feeds/lienol/lienol/luci-app-verysync
rm -rf package/lean/kcptun
rm -rf package/lean/trojan
rm -rf package/lean/v2ray
rm -rf package/lean/luci-app-kodexplorer
rm -rf package/lean/luci-app-pppoe-relay
rm -rf package/lean/luci-app-pptp-server
rm -rf package/lean/luci-app-v2ray-server
./scripts/feeds install -a
```

然后make menuconfig 进入编译菜单。 最后按以上教程选择所需的插件后。退出编译菜单运行命令：make -j1 V=s 进行编译。#n=线程数+1，例如4线程的I5填-j5，开始编译 给openwrt固件添加Passwall插件的方法结束，建议plus+与passwall二选一吧，如果选择passwall的话，那建议把plus+以下的其它组件都取消掉。 ## 四、再次编译

完成首次编译 再编译可大大缩短时间，只输入以下代码，十几分钟的事情。 ```
OpenWrt编译方式：
cd lede      #进入LEDE目录
git pull      #同步更新大雕源码
./scripts/feeds update -a && ./scripts/feeds install -a       #更新FEEDS
rm -rf ./tmp && rm -rf .config        #清除编译配置和缓存
make menuconfig     #进入编译配置菜单
make -j1 V=s      #n=线程数+1，例如4线程的I5填-j5，开始编译
```

以上代码一行一行操作。 注意：编译丰富插件时，建议修改下面两项默认大小，留足插件空间。（ x86/64 ）！！！ Target Images —&gt; (16) Kernel partition size (in MB) #默认是 (16) 建议修改 (256) Target Images —&gt; (160) Root filesystem partition size (in MB) #默认是 (160) 建议修改 (512) ## 五、刷写 OpenWrt 软件由固件方法

如何把固件刷到软路由上面，建议使用以下两个方案。 **1. DiskImage直接刷写（最直接方便）**![c4ea5c0b0a8fd06](https://affvps.com/wp-content/uploads/2022/03/c4ea5c0b0a8fd06.jpg "c4ea5c0b0a8fd06")刷写方法：制作一个PE盘，把DiskImage和LEDE固件拷贝到PE盘，插到路由上，启动PE，然后和方法一差不多，打开DiskImage，选择软路由上的那块硬盘，选 OpenWrt.img，点开始，等进度条结束，然后关机，拔掉U盘，再开机就可以了 **2. 用physdiskwrite刷写**刷写方法：制作一个PE盘，把physdiskwrite和LEDE固件拷贝到PE盘（同一个目录下，建议放在根目录，就是打开U盘就能看到的那个目录），插到路由上，启动PE，然后查看下存放固件的盘符（这里举例为U:盘），打开cmd（不懂的就按Win建+r键，输入cmd回车，Win键就是键盘左下方是Windows图标的那个按键） ```
　　输入U: （回车确定，切换到U盘的目录）
　　输入physdiskwrite -u OpenWrt.img（回车确定）
```

然后会显示目前检测到的硬盘，输入0或者1选择要刷写到哪个盘（看容量，选择硬盘的那个编号），按Y确定，之后等待刷写结束就可以了，然后关机，拔掉U盘，再开机就可以了. **常用插件列表**一般来说只要选对你的机器型号其他按默认就行了，有特殊需要可以勾选需要的插件即可 > luci-app-accesscontrol 上网时间控制 luci-app-adbyby-plus 广告屏蔽大师Plus + luci-app-amule 电驴下载–我一般精简掉 luci-app-aria2 Aria2下载–我一般精简掉 luci-app-arpbind IP/MAC绑定 luci-app-ddns 动态域名解析 luci-app-flowoffload Turbo ACC FLOW转发加速 luci-app-frpc 内网穿透 Frp–我一般精简掉，因为我的是公网IP luci-app-hd-idle 硬盘休眠 luci-app-ipsec-vpnd IPSec服务端 luci-app-mwan3 MWAN负载均衡 luci-app-nlbwmon 网络带宽监视器 luci-app-openvpn OpenVPN客户端 luci-app-openvpn-server OpenVPN服务端 luci-app-pptp-server PPTP服务端 luci-app-ramfree 释放内存 luci-app-samba 网络共享(samba) luci-app-sfe Turbo ACC网络加速(开启Fast Path转发加速) luci-app-sqm 流量智能队列管理(QOS) luci-app-ssr-plus 介绍 `神秘代码：echo 0xDEADBEEF > /etc/config/google_fu_mode`luci-app-transmission BT下载–我一般精简掉 luci-app-upnp 通用即插即用UPnP(端口自动转发) luci-app-usb-printer USB 打印服务器–我一般精简掉 luci-app-vlmcsd KMS服务器（WIN激活工具）–我一般精简掉 luci-app-vsftpd FTP服务器–我一般精简掉 luci-app-webadmin Web管理 luci-app-wireguard VPN服务器 WireGuard状态 luci-app-wol 网络唤醒 luci-app-wrtbwmon 实时流量监测 支持 iPv6： Extra packages —&gt; ipv6helper （选定这个后下面几项自动选择了） Network —&gt; odhcp6c Network —&gt; odhcpd-ipv6only LuCI —&gt; Protocols —&gt; luci-proto-ipv6 LuCI —&gt; Protocols —&gt; luci-proto-ppp