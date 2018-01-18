---
layout: post
title: Android Studio Run 错误
permalink: 20171228_1.html
description: Android
date: 2017-12-28 12:40:00 +08:00
tags: [Android]
---
### 错误：

使用 Android Studio 运行一个APK时，提示已经安装是否要卸载重新安装时，点“是”后，有以下错误：


>Installation failed with message Failed to finalize session : INSTALL_FAILED_INVALID_APK: /data/app/vmdl1241319322.tmp/11_android______-debug version code 20500000 inconsistent with 0.
It is possible that this issue is resolved by uninstalling an existing version of the apk if it is present, and then re-installing.

> Unknown failure (at android.os.Binder.execTransact(Binder.java:674))

### 原因：

这是因为 Android Studio 有一个Instant Run 运行机制。报错原因不明。

[官方文档](https://developer.android.com/studio/run/index.html#instant-run
)说明
> Android Studio 2.0 中引入的 Instant Run 是 Run  和 Debug  命令的行为，可以大幅缩短应用更新的时间。尽管首次构建可能需要花费较长的时间，Instant Run 在向应用推送后续更新时则无需构建新的 APK，因此，这样可以更快地看到更改。

> 仅在您部署调试构建变体、使用 Android Plugin for Gradle 版本 2.0.0 或更高版本，以及在应用的模块级别 build.gradle 文件中将 minSdkVersion 设置为 15 或以上时，Instant Run 才受支持。为获得最佳性能，可以将 minSdkVersion 设置为 21 或更高。

### 解决：

停用 Instant Run 机制即可解决问题。

1. File -> Settings -> Build, Execution, Deployment.
2. Instant Run -> disable "Enable Instant Run to hot swap code/resource changes on deploy".
3. Apply -> OK


