# 常用 GUI 应用

## [Rescue Time](https://www.rescuetime.com/)

记录你一周内的软件使用时间分配情况，以周为单位返回效率报告。

![](https://www.rescuetime.com/images/imac.png)

    brew cask install rescuetime


## FlashLight

![](https://camo.githubusercontent.com/3518833268d47c54081beec1f6aac6e834113676/68747470733a2f2f7261772e6769746875622e636f6d2f6e6174652d706172726f74742f666c6173686c696768742f6d61737465722f496d6167652e706e67)

[Flashlight](http://flashlight.nateparrott.com/plugin/quicksearch) 是 Spotlight
的扩展工具，是 Alfred 的免费 clone。

源代码：[w0lfschild/Flashlight](https://github.com/nate-parrott/Flashlight/wiki/Creating-a-Plugin)

安装：``brew cask install mysimbl flashlight``。


## Wireshark
![](https://www.wireshark.org/docs/wsug_html_chunked/wsug_graphics/ws-main.png)

网络请求查询工具

    brew cask install wireshark


## Go2Shell

Finder 中快速打开 Shell 的工具，支持多个 Shell 程序。

    brew cask install go2shell


## Sublime Text 3

简单、好用的 GUI 编辑器。

    brew cask install sublime-text3


## DrRacket

提供 Scheme 的运行环境，严格说起来 DrRacket 实现的也只是 Scheme 的方言。

    brew cask install racket


## SourceTree

支持 git 和 hg 版本控制的 GUI 应用，并且支持 Git Flow。

    brew cask install sourcetree


## Postman - REST client

提供强大的 web 请求模拟功能，非常适合 RESTful API 应用测试。


## Music Converter

音频转换工具。


## Gas Mask

用于多个 hosts 之间快速切换。

    brew cask install gas-mask


## ClipMenu

![](http://www.clipmenu.com/images/screenshot/home/screenshot.jpg)

剪贴板纪录工具。

    brew cask install clipmenu


## DynamicLyrics

在任务栏或者工作区中动态显示歌词的应用。

    brew cask install dynamiclyrics


## CrossShare

CrossShare 提供了快捷 AirDrop 共享支持，安装后可以使用 AirDrop 打开
``crossshare://airdrop?url=http://google.com`` 这样的链接，通常[配合 Chrome
插件](/pages/chrome-plugin.html#cross-share-airdrop)或者
Alfred 工作流使用。


## 微信 debugger

国内做微信相关开发还是很需要的。

    brew cask install wxdebugger


## Rime 输入法

又名鼠须管输入法。官网：http://rime.im/

配置文档：https://github.com/rime/home/wiki/CustomizationGuide

配置教程：https://medium.com/@scomper/鼠須管-的调教笔记-3fdeb0e78814
http://www.jianshu.com/p/cffc0ea094a7

配置文件下载地址（Mac 版）：https://dl.dropboxusercontent.com/u/6790544/squirrel-patch.zip

仍在调教中……


## [MplayerX 播放器](http://mplayerx.org/)

稳定、美观的全格式视频播放器，播放 SMB 视频非常流畅。

    brew cask install mplayerx


## QuickLook 插件

系统性地增强 Mac 预览程序的功能，大部分可以通过 HomeBrew Cask 进行安装：

```sh
brew cask install qlcolorcode # 代码高亮
brew cask install qlstephen # 纯文本格式增强
brew cask install qlmarkdown # Markdown 预览
brew cask install quicklook-json # JSON 预览
brew cask install qlprettypatch # patch 格式预览
brew cask install quicklook-csv # csv 格式预览
brew cask install betterzipql # 压缩格式预览
brew cask install qlimagesize # 标题栏显示图片大小信息
brew cask install webpquicklook # webp 格式支持
brew cask install suspicious-package # pkg 格式支持
brew cask install qlvideo # 视频缩略图预览
```

插件列表可以在 [quick-look-plugins](https://github.com/sindresorhus/quick-look-plugins)
上找到。


## Synergy 键鼠同步

[Synergy](https://symless.com/synergy/) 是一款[开源](https://github.com/symless/synergy)的跨平台的多设备间键鼠同步软件。在所有设备上都安装完 Synergy 并运行之后，将其中连结了键鼠的设备设置为服务端，其它为客户端即可根据提示自动完成配对，并自由地切换想要控制的设备。（当然，需要保证在同一网络环境下。）

目前在无线环境中使用中遇到了卡顿和轻微漂移的问题，也存在断线不能重连的问题，可能跟网络质量有关。

亮点：

- 支持剪贴板同步
- 支持拖拽复制文件

缺点：

- 不够稳定；
- 存在内存泄漏问题，需要定时重启。


## Tunnelblick

Mac 下的 OpenVPN 客户端。

源代码：[Tunnelblick/Tunnelblick](https://github.com/Tunnelblick/Tunnelblick/)

    brew cask install tunnelblick


## 日历增强软件 [Itsycal](https://www.mowglii.com/itsycal/)

macOS 自带的时间软件一直为人所诟病，Itsycal 则提供了一个简单的替代方案，支持日历和近期事项管理。

![](https://www.mowglii.com/itsycal/itsycalbanner2.png)
