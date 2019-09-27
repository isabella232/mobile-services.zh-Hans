---
description: 以下是关于默认 Mobile 量度和维度的参考信息。
keywords: mobile
seo-description: 以下是关于默认 Mobile 量度和维度的参考信息。
seo-title: 移动量度和维度参考
solution: Marketing Cloud,Analytics
title: 移动量度和维度参考
topic: 量度
uuid: 96170ae7-8553-4f3e-ae01-65e5b664adf4
translation-type: tm+mt
source-git-commit: 056bb3edb94c2ceb2961bbe8e4851c20429e1ea2

---


# Mobile metrics and dimensions reference {#mobile-metrics-and-dimensions-reference}

This information helps you understand more about the default mobile metrics and dimensions.

>[!TIP]
>
>在Adobe Analytics中设置的维度和度量权限适用于Mobile Services。 When you try to run a report without the proper permissions, an error occurs.

## 量度 {#section_6704C815147D44AF96151D626BEB813C}

以下是默认移动量度列表：

* **首次启动次数**

   安装后或重新安装后首次运行时触发。

* **升级**

   升级后或版本号变更后首次运行时触发。

* **每日参与的用户数**

   当特定的某天使用应用程序时触发。

   >[!TIP]
   >“每日参与的用户”事件不会自动存储在Analytics量度中。 您必须创建一个处理规则，以设置一个自定义事件用来捕获此量度。

* **每月参与的用户**

   在每月使用应用程序时触发。

   >[!TIP]
   >The Monthly Engaged Users event is not automatically stored in an Analytics metric. 您必须创建一个处理规则，以设置一个自定义事件用来捕获此量度。

* **启动次数**

   在除安装或升级以外的任何情况下运行时触发。当应用程序移出后台时也会触发该事件。默认情况下，如果应用程序在后台的时间达到或超过五分钟，则会触发一个新的启动。The amount of background time before triggering a new launch can be configured in **[!UICONTROL SDK Analytics Options]** on the Manage App Settings page. For more information, see the Session Timeout (Seconds) row in Configure SDK Analytics Options.**[](/help/using/c-manage-app-settings/c-mob-confg-app/t-config-analytics/t-config-analytics.md)

   >[!IMPORTANT]
   >Because how visits in [!UICONTROL Adobe Analytics] and mobile app launches in [!UICONTROL Adobe Mobile Services] are calculated, you might see different results in reporting. 有关更多信息，请参阅[比较查看次数和移动设备应用程序启动次数](https://helpx.adobe.com/analytics/kb/compare-visits-and-mobile-app-launches.html)。

* **崩溃**

   在应用程序未正常退出时触发。该事件在应用程序崩溃后又重新启动时发送。

   >[!TIP]
   >The application is considered to crash if quit is not called.

* **会话总时长**

   会话合计总时长。

## 维度 {#section_1784C7E859F64CCEB95C5DD1DCF5C98D}

Here is the list of default mobile dimensions:

* **安装日期**

   安装后首次启动的日期。日期采用 *YYYY/MM/DD* 格式。

* **应用程序 ID**

   Stores the Application name and version in the following format: `[AppName] [BundleVersion]`. 例如：`myapp 1.1`。

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

* **Operating System**

   设备的操作系统。

* **操作系统版本**

   操作系统版本。

* **上次升级后间隔天数**

   自应用程序版本号发生更改后间隔的天数。

   >[!TIP]
   >
   >上次升级后的天数不会自动存储在Analytics变量中。 您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

* **上次升级后启动次数**

   自应用程序版本号发生更改后的启动次数。

   >[!TIP]
   >
   >自上次升级以来的启动项不会自动存储在Analytics变量中。 您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

* **设备名称**

   存储设备名称。In iOS, a comma-separated, two-digit string identifies the iOS device. 第一数字表示设备生成，第二数字表示设备系列的不同成员。 要获取常见设备名称的完整列表，请参阅 [iOS 设备版本](/help/ios/reference/device-versions.md)。

* **运营商名称**

   存储移动服务提供商的名称。

* **分辨率**

   宽度和高度的实际像素。
