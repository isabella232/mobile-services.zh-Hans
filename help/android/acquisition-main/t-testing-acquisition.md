---
description: 以下信息可帮助您对 Android 设备上的旧版客户获取促销活动链接进行往返测试。
keywords: android;library;mobile;sdk
seo-description: 以下信息可帮助您对 Android 设备上的旧版客户获取促销活动链接进行往返测试。
seo-title: 测试旧版客户获取
solution: Experience Cloud,Analytics
title: 测试旧版客户获取
topic: Developer and implementation
uuid: bb7ace96-68eb-4f43-b3cf-af80730b9cee
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 74%

---


# 测试旧版客户获取 {#testing-legacy-acquisition}

以下信息可帮助您对 Android 设备上的旧版客户获取促销活动链接进行往返测试。

如果移动应用程序尚未在Google Play中，则可在创建活动链接时选择任何移动应用程序作为目标。 这仅会影响在您单击客户获取链接后，客户获取服务器将您重定向到的应用程序，而不会影响测试客户获取链接的功能。查询字符串参数将传递到 Google Play 应用商店，并作为促销活动广播的一部分传递到正在安装的应用程序。往返移动设备应用程序客户获取测试需要模拟此类广播。

每次运行测试时，必须全新安装应用程序，或清除&#x200B;**[!UICONTROL 设置]**&#x200B;中的数据。这可以确保在首次启动应用程序时发送与促销活动查询字符串参数关联的初始生命周期量度。

1. 在 Mobile Services 用户界面中，生成旧版客户获取促销活动 URL。

   有关更多信息，请参阅[使用旧版客户获取链接](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md)。
1. 将设备连接到计算机，启动 ADB Shell，然后在设备上启动应用程序。
1. 使用以下格式发送广播：

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. 完成以下步骤：
   1. 将 `com.example.adobetesttapp.com` 替换为您的应用程序的反向 DNS 条目。
   1. 使用您的应用程序中的促销活动跟踪接收器位置引用更新接收器引用。
   1. 将与 `utm_source`、`utm_medium`、`utm_term`、`utm_content`、`utm_campaign` 等关联的值替换为相应的值。

如果广播成功，则显示与下面类似的响应：

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

您还将看到一个图像请求发送到Adobe的数据收集服务器。 如果SDK等待推荐人超时（您在第1步中设置）的完整持续时间，并且图像请求不包含活动参数，则广播失败。
