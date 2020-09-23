---
description: 以下是在实施生命周期后可由移动设备库自动测量的量度和维度，以及生命周期数据疑难解答链接。
keywords: android;library;mobile;sdk
seo-description: 以下是在实施生命周期后可由移动设备库自动测量的量度和维度，以及生命周期数据疑难解答链接。
seo-title: 生命周期量度
solution: Experience Cloud,Analytics
title: 生命周期量度
topic: Developer and implementation
uuid: 5a371f11-6521-410f-a01f-fc3b285b050f
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 70%

---


# 生命周期量度 {#lifecycle-metrics}

以下是在实施生命周期后可由移动设备库自动测量的量度和维度，以及生命周期数据疑难解答链接。

有关详细信息，请访问生命周期数据疑 [难解答知识库](https://helpx.adobe.com/cn/analytics/kb/troubleshoot-lifecycle-data.html)。

## 生命周期量度和维度 {#section_78F036C4296F4BA3A47C2044F79C86C1}

配置后，生命周期指标将以上下文数据参数的形式发送到Analytics，以参数形式发送到每个mbox调用的目标，并作为受众管理的信号。 分析和目标使用相同的格式，而受众管理对每个指标使用不同的前缀。

对于Analytics，每次生命周期跟踪调用时发送的上下文数据都会使用度量或维度自动捕获并报告。

### 量度

* **a.media.name**

   安装或重新安装后，在首次运行时触发。

   * Analytics context data/Target parameter: `a.InstallEvent`
   * Audience Manager 信号：`c_a_InstallEvent`

* **升级**

   升级后或版本号变更后，在首次运行时触发。

   * Analytics context data/Target parameter: `a.UpgradeEvent`
   * Audience Manager 信号：`c_a_UpgradeEvent`

* **每日参与的用户数**

   当特定的某天使用应用程序时触发。

   >[!IMPORTANT]
   >
   >此量度不会自动存储到某个 Analytics 量度中。您必须创建一个处理规则，以设置一个自定义事件用来捕获此量度。

   * Analytics context data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager 信号：`c_a_DailyEngUserEvent`

* **每月参与的用户数**

   当特定的某月使用应用程序时触发。>>>>

   >[!IMPORTANT]
   >
   >此量度不会自动存储到某个 Analytics 量度中。您必须创建一个处理规则，以设置一个自定义事件用来捕获此量度。

   * Analytics context data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager 信号：`c_a_MonthlyEngUserEvent`

* **启动次数**

   每次运行时触发，包括崩溃和安装。 当超出生命周期会话超时时，从后台在恢复上触发。

   * Analytics context data/Target parameter: `a.LaunchEvent`
   * Audience Manager 信号：`c_a_LaunchEvent`

* **崩溃**

   当应用程序在关闭前未转入后台时触发。当应用程序在崩溃后启动时会发送该事件。Adobe Mobile 崩溃报告不实施全局未捕获异常处理程序。

   * Analytics context data/Target parameter: `a.CrashEvent`
   * Audience Manager 信号：`c_a_CrashEvent`

* **上一会话时长**

   根据应用程序在前台打开时间的长短，报告应用程序上一次会话持续的秒数。

   * Analytics context data/Target parameter: `a.PrevSessionLength`
   * Audience Manager 信号：`c_a_PrevSessionLength`

### 维度

* **安装日期**

   安装后首次启动的日期。日期格式为 `MM/DD/YYYY`。

   * Analytics context data/Target parameter: `a.InstallDate`
   * Audience Manager 信号：`c_a_InstallDate`

* **应用程序 ID**

   按以下格式存储应用程序名称和版本：
   `[AppName] [BundleVersion]`。

   例如，`myapp 1.1` 便采用了上述格式。

   * Analytics context data/Target parameter: `a.AppID`
   * Audience Manager 信号：`c_a_AppID`

* **启动次数**

   应用程序启动或移出后台的次数。

   * Analytics context data/Target parameter: `a.Launches`
   * Audience Manager 信号：`c_a_Launches`

* **首次使用后间隔天数**

   首次运行后间隔的天数。

   * Analytics context data/Target parameter: `a.DaysSinceFirstUse`
   * Audience Manager 信号：`c_a_DaysSinceFirstUse`

* **上次使用后间隔天数**

   自上次使用以来经过的天数。

   * Analytics context data/Target parameter: `a.DaysSinceLastUse`
   * Audience Manager 信号：`c_a_DaysSinceLastUse`

* **每天时间**

   测量应用程序启动的小时。此量度采用 24 小时制数字格式，用于时间分片以确定峰值使用时间。

   * Analytics context data/Target parameter: `a.HourOfDay`
   * Audience Manager 信号：`c_a_HourOfDay`

* **每周时间**

   应用程序启动的星期数。

   * Analytics context data/Target parameter: `a.DayOfWeek`
   * Audience Manager 信号：`c_a_DayOfWeek`

* **操作系统版本**

   操作系统的版本。

   * Analytics context data/Target parameter: `a.OSVersion`
   * Audience Manager 信号：`c_a_OSVersion`

* **上次升级后间隔天数**

   自应用程序版本号发生更改后间隔的天数。

   >[!IMPORTANT]
   >
   >此量度不会自动存储到某个 Analytics 变量中。您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics context data/Target parameter: `a.DaysSinceLastUpgrade`
   * Audience Manager 信号：`c_a_DaysSinceLastUpgrade`

* **上次升级后的启动次数**

   自应用程序版本号发生更改后的启动次数。

   >[!IMPORTANT]
   >
   >此量度不会自动存储到某个 Analytics 变量中。您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics context data/Target parameter: `a.LaunchesSinceUpgrade`
   * Audience Manager 信号：`c_a_LaunchesSinceUpgrade`

* **设备名称**

   存储设备名称。

   * Analytics context data/Target parameter: `a.DeviceName`
   * Audience Manager 信号：`c_a_DeviceName`

* **运营商名称**

   存储由设备提供的移动设备服务提供商的名称。

   >[!IMPORTANT]
   >
   >此量度不会自动存储到某个 Analytics 变量中。您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics context data/Target parameter: `a.CarrierName`
   * Audience Manager 信号：`c_a_CarrierName`

* **分辨率**

   宽 x 高（以实际像素为单位）。

   * Analytics context data/Target parameter: `a.Resolution`
   * Audience Manager 信号：`c_a_Resolution`

## 其他移动量度和维度 {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

移动设备解决方案变量采用所列的方法来捕获以下量度和维度。

* **位置（精确到 10 千米）**

   由 `trackLocation` 方法填充。

   * Analytics上下文数据/目标参数：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * 受众管理特征：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **位置（精确到 100 米）**

   由 `trackLocation` 方法填充。

   * Analytics上下文数据/目标参数：

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * 受众管理特征：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **位置（精确到 1 米）**

   由 `trackLocation` 方法填充。

   * Analytics上下文数据/目标参数：

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * 受众管理特征：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **目标点名称**

   Populated by `trackLocation` methods when device is within a defined POI.

   * Analytics上下文数据/目标参数：

      * `a.loc.poi`
   * 受众管理特征：

      * `c_a_loc_poi`


* **与目标点中心的距离**

   Populated by `trackLocation` methods when device is within a defined POI.

   * Analytics上下文数据/目标参数：

      * `a.loc.dist`
   * 受众管理特征：

      * `c_a_loc_dist`
