---
description: 以下是关于默认 Mobile 量度和维度的参考信息。
keywords: mobile
solution: Experience Cloud,Analytics
title: 移动量度和维度参考
topic-fix: Metrics
uuid: 96170ae7-8553-4f3e-ae01-65e5b664adf4
exl-id: ddfbf11e-a4c3-4d59-92b3-1d192dc3e7cd
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 100%

---

# 移动量度和维度参考 {#mobile-metrics-and-dimensions-reference}

此信息可帮助您进一步了解默认移动量度和维度。

>[!TIP]
>
>在 Adobe Analytics 中设置的维度和量度权限同样适用于 Mobile Services。当您尝试运行没有相应权限的报表时，会发生错误。

## 量度 {#section_6704C815147D44AF96151D626BEB813C}

以下是默认移动量度列表：

* **首次启动次数**

   安装后或重新安装后首次运行时触发。

* **升级**

   升级后或版本号变更后首次运行时触发。

* **每日参与的用户数**

   当特定的某天使用应用程序时触发。

   >[!TIP]
   >
   >“每日参与的用户数”事件不会自动存储到 Analytics 量度中。您必须创建一个处理规则，以设置一个自定义事件用来捕获此量度。

* **每月参与的用户数**

   在每月使用应用程序时触发。

   >[!TIP]
   >“每月参与的用户数”事件不会自动存储到 Analytics 量度中。您必须创建一个处理规则，以设置一个自定义事件用来捕获此量度。

* **启动次数**

   在除安装或升级以外的任何情况下运行时触发。当应用程序移出后台时也会触发该事件。默认情况下，如果应用程序在后台的时间达到或超过五分钟，则会触发一个新的启动。可以在“管理应用程序设置”页面的 **[!UICONTROL SDK Analytics 选项]**&#x200B;中，配置触发新的启动之前应用程序在后台的时长。有关更多信息，请参阅[配置 SDK Analytics 选项](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md)中的“会话超时（秒）”**&#x200B;行。

   >[!IMPORTANT]
   >由于计算 [!UICONTROL Adobe Analytics] 中访问次数和 [!UICONTROL Adobe Mobile Services] 中移动设备应用程序启动次数的方式，您可能会在报表中看到不同的结果。有关更多信息，请参阅[比较查看次数和移动设备应用程序启动次数](https://helpx.adobe.com/cn/analytics/kb/compare-visits-and-mobile-app-launches.html)。

* **崩溃**

   当应用程序无法正确退出时触发。应用程序在崩溃后启动时会发送此事件。

   >[!TIP]
   >如果未调用退出，则视为应用程序发生崩溃。

* **会话总时长**

   会话合计总时长。

## 维度 {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

以下是默认移动维度列表：

* **安装日期**

   安装后首次启动的日期。日期采用 *YYYY/MM/DD* 格式。

* **应用程序 ID**

   采用以下格式存储应用程序名称和版本：`[AppName] [BundleVersion]`。例如：`myapp 1.1`。

* **启动次数**

   应用程序启动或移出后台的次数。

* **首次使用后间隔天数**

   首次运行后间隔的天数。

* **上次使用后间隔天数**

   自上次使用以来经过的天数。

* **每天时间**

   测量应用程序启动的时间，采用 24 小时数字格式。此维度还用于时间分片以确定峰值使用时间。

* **每周时间**

   应用程序星期几启动。

* **操作系统**

   设备的操作系统。

* **操作系统版本**

   操作系统版本。

* **上次升级后间隔天数**

   自应用程序版本号发生更改后间隔的天数。

   >[!TIP]
   >
   >自上次升级后的天数不会自动存储在 Analytics 变量中。您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

* **上次升级后启动次数**

   自应用程序版本号发生更改后的启动次数。

   >[!TIP]
   >
   >自上次升级后的启动次数不会自动存储在 Analytics 变量中。您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

* **设备名称**

   存储设备名称。在 iOS 中，使用以逗号分隔的两位字符串来标识 iOS 设备。第一个数字代表第几代设备，第二个数字表示设备系列的不同成员。要获取常见设备名称的完整列表，请参阅 [iOS 设备版本](/help/ios/reference/device-versions.md)。

* **运营商名称**

   存储移动服务提供商的名称。

* **分辨率**

   宽度和高度的实际像素。
