---
description: 以下信息可帮助您解决客户获取测试问题。
keywords: android；获取；测试
seo-description: 以下信息可帮助您解决客户获取测试问题。
seo-title: 客户获取测试疑难解答
solution: Marketing Cloud,Analytics
title: 客户获取测试疑难解答
translation-type: tm+mt
source-git-commit: da8798d7ee1f05dcade31cced5404d78c9cf360a

---


# 客户获取测试疑难解答 {#aquistion-testing-troubleshooting}

以下是测试客户获取和一些可能的解决方案时可能遇到的一些问题：

* 如果未指定，则应将ADBMobileConfig.json文件放在assets文件夹中。

* 该名称区分大小写，因此请勿在小写字母中提供名称。

   您需要确保从主 `Config.setContext(this.getApplicationContext())` 活动中调用该选项。 For more information, see Configuration methods.[](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)

* 提供的AndroidManifest.xml文件中缺少一些用户权限，发送数据和记录脱机跟踪调用时需要这些权限：

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 在您的配置中，如果引用超时设置为 `referrerTimeout: 5`，这意味着您需要在应用程序第一次安装并启动后的5秒钟内发送安装意向，以查看附加到安装点击的引用信息。

   For manual testing, increase the  to 10-15 seconds, so that there is enough time to send the referrer information before the install hit is processed.`referrerTimeout`

* It is important to run all the steps in Testing Marketing Link acquisition in order and make sure you execute  shell and then the following:[](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html)`adb`

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>You must run these two commands independently to process the referrer intent correctly.  否则， `adb` 双重转义参照信息，广播接收机接收的数据将不完整。
