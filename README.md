# Termux APP

[![构建状态](https://github.com/termux/termux-app/workflows/Build/badge.svg)](https://github.com/termnex/termux-app/actions)
[![测试状态](https://github.com/termux/termux-app/workflows/Unit%20tests/badge.svg)](https://github.com/termnex/termux-app/actions)
[![加入聊天在 https://gitter.im/termux/termux](https://badges.gitter.im/termux/termux.svg)](https://gitter.im/termux/termux)
[![加入 Termux Discord 服务器](https://img.shields.io/discord/641256914684084234.svg?label=&logo=discord&logoColor=ffffff&color=5865F2)](https://discord.gg/HXpF69X)
[![Termux 库在 Jitpack 上发布](https://jitpack.io/v/termux/termux-app.svg)](https://jitpack.io/#termux/termux-app)


[Termux](https://termux.com) 是一个Android终端应用程序和Linux环境.

请注意，此存储库用于应用程序本身（用户界面和终端仿真). 有关可在应用程序内安装的软件包，请参阅 [termnex/termux-packages](https://github.com/termnex/termux-packages).

有关 Termux 包管理的快速指南，请访问 [包管理](https://github.com/termnex/termux-packages/wiki/Package-Management). 它还包含有关如何在运行 `apt` 或 `pkg` 命令时修复 **`repository is under maintenance or down`** 错误的信息.
***

**@termux 正在寻找 Termux 应用程序维护人员来实现新功能、修复错误和审查拉取请求，因为当前 (@fornwall) 处于非活动状态. **

问题 https://github.com/termnex/termux-app/issues/ 需要特别注意.

***

### 内容
- [Termux应用和插件](#Termux-应用-和-插件)
- [安装](#安装)
- [卸载](#卸载)
- [重要链接](#重要链接)
- [对于维护者和贡献者](#对于维护者和贡献者)
- [分叉](#分叉)
##



## Termux 应用 和 插件

核心 [Termux](https://github.com/termnex/termux-app) 应用程序附带以下可选插件应用程序

- [Termux:API](https://github.com/termnex/termux-api)
- [Termux:Boot](https://github.com/termnex/termux-boot)
- [Termux:Float](https://github.com/termnex/termux-float)
- [Termux:Styling](https://github.com/termnex/termux-styling)
- [Termux:Tasker](https://github.com/termnex/termux-tasker)
- [Termux:Widget](https://github.com/termnex/termux-widget)
##



## 安装

Termux 可以通过下面列出的各种来源获得，**仅限** Android `>= 7`。不再支持 Android `5` 和 `6` [2020-01-01](https://www.reddit.com/r/termux/comments/dnzdbs/end_of_android56_support_on_20200101/) 在 `v0.83` 上，旧版本可以在 [archive.org](https://archive.org/details/termux-repositories-legacy).

不同来源的 APK 文件使用不同的签名密钥进行签名。 `Termux` 应用程序及其所有插件使用相同的 [`sharedUserId`](https://developer.android.com/guide/topics/manifest/manifest-element) `com.termux` 等所有安装在设备上的 APK 必须使用相同的签名密钥进行签名才能协同工作，因此它们都必须从同一来源安装. 不要尝试将它们混合在一起，即不要尝试安装来自“F-Droid”的应用程序或插件以及来自不同来源（如“Github”）的应用程序或插件. Android 包管理器通常也不允许安装具有不同签名的 APK，并且您会在安装时遇到诸如“未安装应用程序”、“由于未知错误而无法安装”等错误消息，`INSTALL_FAILED_UPDATE_INCOMPATIBLE`, `INSTALL_FAILED_SHARED_USER_INCOMPATIBLE`, `签名与以前安装的版本不匹配，等等。这个限制可以通过 root 或自定义 rom 绕过.

如果您希望从不同的来源安装，那么您必须先从您的设备 **卸载所有现有的 Termux 或其插件应用 APK**，然后安装来自同一新来源的所有新 APK. 查看 [卸载](#卸载) 部分了解详情. 您可能还想考虑 [备份Termux](https://wiki.termux.com/wiki/Backing_up_Termux) 卸载之前，以便您可以在从 Termux 不同来源重新安装后恢复它.

在下面的段落中，*"bootstrap"* 是指与`termux-app` 本身一起提供的用于启动工作 shell 环境的最小包. 它的拉链被构建和发布 [here](https://github.com/termnex/termux-packages/releases).

### Github

可以从`Github` 上获得 Termux 应用程序 [`Github Releases`](https://github.com/termux/termux-app/releases) for `>= v0.118` 或者在 [`Github 构件`](https://github.com/termux/termux-app/actions/workflows/debug_build.yml) action workflows.

`Github Releases` 的 APK 将列在一个版本的 `Assets` 下拉列表中. 当新版本发布时，这些会自动附加。 `Github Build` 操作工作流的 APK 将列在工作流运行的 `Artifacts` 部分下. 这些是为每次提交/推送到存储库而创建的，可供不想等待发布并想要立即试用最新功能或想要测试其拉取请求的用户使用. 
 这两个的 APK 是 [`debuggable`](https://developer.android.com/studio/debug) 并且彼此兼容，但它们与其他来源不兼容.
 
发布了通用和特定于架构的 APK. 如果使用通用，APK 和引导程序安装大小将为“~180MB”，如果使用特定架构，则为“~120MB”. 查看 [here](https://github.com/termux/termux-app/issues/2153) 详情.


## 卸载

如果用户不想再在他们的设备中安装 Termux 或正在切换到不同的设备，则可能需要卸载 [安装源码](#安装). 您可能还想考虑 [备份Termux](https://wiki.termux.com/wiki/备份_Termux) 在卸载之前.

要完全卸载 Termux，您必须卸载 **任何和所有现有的 Termux 或其插件应用程序 APK** [Termux 或其插件应用程序](#Termux-或其插件应用程序).

转到“Android 设置”->“应用程序”，然后查找这些应用程序. 您还可以使用搜索功能（如果它在您的设备上可用）并在应用程序列表中搜索“termux”.

即使您认为自己没有安装任何插件，强烈建议您浏览 Android 设置中的应用程序列表并仔细检查.
##



