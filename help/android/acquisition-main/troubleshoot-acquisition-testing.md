---
description: 本主题提供了有关如何排查客户获取测试过程中可能遇到的问题的信息。
keywords: android;library;mobile;sdk
seo-description: 本主题提供了有关如何排查客户获取测试过程中可能遇到的问题的信息。
seo-title: 排查客户获取测试问题
solution: Experience Cloud,Analytics
title: 排查客户获取测试问题
topic: Developer and implementation
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 100%

---


# 排查客户获取测试问题 {#troubleshoot-acquisition-testing}

本主题提供了有关如何排查客户获取测试过程中可能遇到的问题的信息。

* 如果没有另外指定，则应将 ADBMobileConfig.json 文件放置在 `assets` 文件夹中。

   名称区分大小写，因此不要使用大写或小写字母。

* 确保从主活动中调用 `Config.setContext(this.getApplicationContext())`。

   有关更多信息，请参阅[配置方法](https://docs.adobe.com/content/help/zh-Hans/mobile-services/android/configuration-android/methods.html)。

* 确保 `AndroidManifest.xml` 文件中存在 Mobile SDK 所需的权限：

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 如果在 ADBMobileConfig.json 文件中将 `referrerTimeout` 设置为 5，则您必须在安装应用程序并首次启动该应用程序后的 5 秒内发送安装意图，才能查看附加到安装点击的反向链接信息。

   对于手动测试，我们建议您将 `referrerTimeout` 增加到 10-15 秒，以便在处理安装点击之前有足够的时间发送反向链接信息。

* 运行[测试营销链接客户获取](https://docs.adobe.com/content/help/zh-Hans/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html)中的所有步骤，并确保首先执行 `adb shell` 命令，然后完成以下步骤：

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>要正确处理反向链接意图，必须独立运行这两个命令。否则，`adb` 将双重转义反向链接信息，并且广播接收器收到的数据将不完整。

