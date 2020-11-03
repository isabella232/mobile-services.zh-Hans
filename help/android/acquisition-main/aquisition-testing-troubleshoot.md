---
description: 以下信息可帮助您排查客户获取测试问题。
keywords: android;Acquisition;testing
seo-description: 以下信息可帮助您排查客户获取测试问题。
seo-title: 排查客户获取测试问题
solution: Experience Cloud,Analytics
title: 排查客户获取测试问题
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '251'
ht-degree: 100%

---


# 排查客户获取测试问题 {#aquistion-testing-troubleshooting}

以下是测试客户获取时可能遇到的一些问题以及一些可能的解决方案：

* 如果没有另外指定，则应将 ADBMobileConfig.json 文件放置在 assets 文件夹中。

* 名称区分大小写，因此不要使用小写字母提供名称。

   您需要确保从主活动中调用 `Config.setContext(this.getApplicationContext())`。有关更多信息，请参阅[配置方法](https://docs.adobe.com/content/help/zh-Hans/mobile-services/android/configuration-android/methods.html)。

* 提供的 AndroidManifest.xml 文件中缺少一些用户权限，发送数据和记录离线跟踪调用时需要使用这些权限：

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 在您的配置中，如果将反向链接超时设置为 `referrerTimeout: 5`，这意味着您需要在安装应用程序并首次启动该应用程序后的 5 秒内发送安装意图，才能查看附加到安装点击的反向链接信息。

   对于手动测试，请将 `referrerTimeout` 增加到 10-15 秒，以便在处理安装点击之前有足够的时间发送反向链接信息。

* 务必按顺序运行[测试营销链接客户获取](https://docs.adobe.com/content/help/zh-Hans/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html)中的所有步骤，并确保执行 `adb` Shell，然后完成以下步骤：

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>要正确处理反向链接意图，必须独立运行这两个命令。否则，`adb` 将双重转义反向链接信息，而且广播接收器收到的数据将不完整。
