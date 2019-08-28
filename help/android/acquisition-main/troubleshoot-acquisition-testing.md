---
description: 本主题提供了有关在客户获取测试过程中可能遇到的问题故障诊断的信息。
keywords: android；库；移动；sdk
seo-description: 本主题提供了有关在客户获取测试过程中可能遇到的问题故障诊断的信息。
seo-title: 客户赢取测试疑难解答
solution: Marketing Cloud，Analytics
title: 客户赢取测试疑难解答
topic: 开发人员和实施
translation-type: tm+mt
source-git-commit: 97202c672d7349496f83b9ac0c365dd8b3e13eda

---


# 客户赢取测试疑难解答 {#troubleshoot-acquisition-testing}

本主题提供了有关在客户获取测试过程中可能遇到的问题故障诊断的信息。

* 如果未指定，则应将AdbMobileConfig. json文件放入 `assets` 文件夹中。

   该名称区分大小写，因此请勿使用大写字母或小写字母。

* 确保 `Config.setContext(this.getApplicationContext())` 从主活动调用。

   有关详细信息，请参阅 [配置方法](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)。

* 确保 `AndroidManifest.xml` 文件中存在Mobile SDK所需的权限：

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 如果在AdMobileConfig. json文件中设置 `referrerTimeout` 为5，您必须在安装应用程序并首次启动之后在秒钟时间内发送安装意向，以查看安装点击附加的引介信息。

   对于手动测试，建议您将到15秒的时间增加 `referrerTimeout` 到10-15秒，以便在处理安装点击之前有足够的时间发送引用信息。

* 运行 [Testing Marketing Link获取中的所有步骤](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) ，并确保您首先执行 `adb shell` 该命令，然后执行以下操作：

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>要正确处理引介意图，您必须独立运行这两个命令。否则 `adb` 将双向转义，广播接收方收到的数据将不完整。

