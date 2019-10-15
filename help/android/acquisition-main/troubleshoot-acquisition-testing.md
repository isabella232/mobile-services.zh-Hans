---
description: 本主题提供了有关如何解决客户获取测试过程中可能遇到的问题的信息。
keywords: android；库；移动；sdk
seo-description: 本主题提供了有关如何解决客户获取测试过程中可能遇到的问题的信息。
seo-title: 客户获取测试疑难解答
solution: Marketing Cloud,Analytics
title: 客户获取测试疑难解答
topic: 开发人员和实施
translation-type: tm+mt
source-git-commit: 1c387b063eedb41a52e044dc824df6a51f173ad2

---


# 客户获取测试疑难解答 {#troubleshoot-acquisition-testing}

本主题提供了有关如何解决客户获取测试过程中可能遇到的问题的信息。

* 如果未指定，则应将ADBMobileConfig.json文件放在文件夹 `assets` 中。

   名称区分大小写，因此请勿使用大写或小写字母。

* 确保从 `Config.setContext(this.getApplicationContext())` 主活动中调用该选项。

   有关详细信息，请参阅 [配置方法](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html)。

* 确保文件中存在Mobile SDK所需的权 `AndroidManifest.xml` 限：

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* 如果 `referrerTimeout` 在ADMobileConfig.json文件中设置为5，则必须在应用程序第一次安装并启动后的5秒时间范围内发送安装意图，以查看附加到安装点击的引用信息。

   对于手动测试，我们建议您将访问时间增加 `referrerTimeout` 到10-15秒，这样您就有足够的时间在处理安装点击之前发送引用信息。

* 运行Testing Marketing link客户获取 [中的所有步骤](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) ，确保先执行命 `adb shell` 令，然后执行以下操作：

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>要正确处理引用意图，必须独立运行这两个命令。 否则， `adb` 将双重逃出引用信息，广播接收机接收的数据将不完整。

