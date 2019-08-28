---
description: 以下信息可帮助您解决客户获取测试问题。
keywords: android；客户赢取；testing
seo-description: 以下信息可帮助您解决客户获取测试问题。
seo-title: 获取测试疑难解答
solution: Marketing Cloud，Analytics
title: 获取测试疑难解答
translation-type: tm+mt
source-git-commit: da8798d7ee1f05dcade31cced5404d78c9cf360a

---


# 获取测试疑难解答 {#aquistion-testing-troubleshooting}

以下是测试获取时可能遇到的一些问题以及可能的解决方案：

* 如果未指定，则应将AdbMobileConfig. json文件放入assets文件夹中。

* 该名称区分大小写，因此不提供小写字母的名称。

   您需要确保 `Config.setContext(this.getApplicationContext())` 从主要活动调用。有关详细信息，请参阅 [配置方法](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)。

* 提供的AndroidManifest.xml文件中缺少一些用户权限，因此必须发送数据并记录脱机跟踪调用：

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 在您的配置中，如果将引用超时设置为 `referrerTimeout: 5`，这意味着您需要在安装应用程序后在秒钟时间内发送安装意向，以查看安装点击附加的引介信息。

   对于手动测试，请增加 `referrerTimeout` 到10-15秒，以便在处理安装点击之前有足够的时间发送引用信息。

* 务必按照顺序运行 [Testing Marketing Link获取中的](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) 所有步骤，并确保执行 `adb` Shell，然后执行以下操作：

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>必须单独运行这两个命令，才能正确处理引介用途。否则， `adb` 引用的信息会加倍，广播接收方接收的数据将不完整。
