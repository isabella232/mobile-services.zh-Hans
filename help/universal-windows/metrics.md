---
description: 列出可由移动设备库自动测量的量度和维度。
keywords: Android;库;移动;SDK
solution: Experience Cloud,Analytics
title: 生命周期量度
topic-fix: Developer and implementation
uuid: f958c3ef-1d79-4b30-8966-ef74bd48a5d6
exl-id: 19572f15-c5df-40fe-9979-3a5bdd581f2b
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 84%

---

# 生命周期量度 {#lifecycle-metrics}

列出可由移动设备库自动测量的量度和维度。

有关更多信息，请参阅[生命周期数据疑难解答](https://helpx.adobe.com/cn/analytics/kb/troubleshoot-lifecycle-data.html)。


## 生命周期量度和维度 {#section_78F036C4296F4BA3A47C2044F79C86C1}

配置后，生命周期量度会在上下文数据参数中发送到 Analytics，随每个 mbox 调用在参数中发送到 Target，并作为信号发送到受众管理。Analytics 和 Target 使用相同的格式，而受众管理则对每个量度使用不同的前缀。

对于Analytics，将使用量度或维度自动捕获并报告随每个生命周期跟踪调用发送的上下文数据。 内容中记录了例外情况。

## 量度

* **首次启动次数**

   安装或重新安装后，在首次运行时触发。

   * Analytics 上下文数据/Target 参数：`a.InstallEvent`
   * Audience Manager 信号：`c_a_InstallEvent`

* **升级**

   升级后或版本号变更后，在首次运行时触发。

   * Analytics 上下文数据/Target 参数：`a.UpgradeEvent`
   * Audience Manager 信号：`c_a_UpgradeEvent`

* **每日参与的用户数**

   当特定的某天使用应用程序时触发。

   >[!IMPORTANT]
   >
   >此量度不会自动存储到某个 Analytics 量度中。您必须创建一个处理规则，以设置一个自定义事件用来捕获此量度。

   * Analytics 上下文数据/Target 参数：`a.DailyEngUserEvent`
   * Audience Manager 信号：`c_a_DailyEngUserEvent`

* **每月参与的用户数**

   当特定的某月使用应用程序时触发。

   >[!IMPORTANT]
   >
   >此量度不会自动存储到某个 Analytics 量度中。您必须创建一个处理规则，以设置一个自定义事件用来捕获此量度。

   * Analytics 上下文数据/Target 参数：`a.MonthlyEngUserEvent`
   * Audience Manager 信号：`c_a_MonthlyEngUserEvent`

* **启动次数**

   在每次运行时触发，包括崩溃次数和安装次数。在超出生命周期会话超时后，当从后台恢复应用程序时也会触发。

   * Analytics 上下文数据/Target 参数：`a.LaunchEvent`
   * Audience Manager 信号：`c_a_LaunchEvent`

* **崩溃**

   当应用程序在关闭前未转入后台时触发。当应用程序在崩溃后启动时会发送该事件。Adobe Mobile 崩溃报告不实施全局未捕获异常处理程序。

   * Analytics 上下文数据/Target 参数：`a.CrashEvent`
   * Audience Manager 信号：`c_a_CrashEvent`

* **上一会话时长**

   根据应用程序在前台打开时间的长短，报告应用程序上一次会话持续的秒数。

   * Analytics 上下文数据/Target 参数：`a.PrevSessionLength`
   * Audience Manager 信号：`c_a_PrevSessionLength`


## 维度

* **安装日期**

   安装后首次启动的日期。日期格式为 `MM/DD/YYYY`。

   * Analytics 上下文数据/Target 参数：`a.InstallDate`
   * Audience Manager 信号：`c_a_InstallDate`

* **应用程序 ID**

   采用 `[AppName] [BundleVersion]` 格式存储应用程序名称和版本。例如，`myapp 1.1` 便采用了上述格式。

   * Analytics 上下文数据/Target 参数：`a.AppID`
   * Audience Manager 信号：`c_a_AppID`

* **启动次数**

   应用程序启动或移出后台的次数。

   * Analytics 上下文数据/Target 参数：`a.Launches`
   * Audience Manager 信号：`c_a_Launches`

* **首次使用后间隔天数**

   首次运行后间隔的天数。

   * Analytics 上下文数据/Target 参数：`a.DaysSinceFirstUse`
   * Audience Manager 信号：`c_a_DaysSinceFirstUse`

* **上次使用后间隔天数**

   自上次使用以来经过的天数。

   * Analytics 上下文数据/Target 参数：`a.DaysSinceLastUse`
   * Audience Manager 信号：`c_a_DaysSinceLastUse`

* **每天时间**

   测量应用程序启动的小时。此量度采用 24 小时制数字格式，用于时间分片以确定峰值使用时间。

   * Analytics 上下文数据/Target 参数：`a.HourOfDay`
   * Audience Manager 信号：`c_a_HourOfDay`

* **每周时间**

   应用程序启动的星期数。

   * Analytics 上下文数据/Target 参数：`a.DayOfWeek`
   * Audience Manager 信号：`c_a_DayOfWeek`

* **操作系统版本**

   操作系统版本。

   * Analytics 上下文数据/Target 参数：`a.OSVersion`
   * Audience Manager 信号：`c_a_OSVersion`

* **上次升级后间隔天数**

   自应用程序版本号发生更改后间隔的天数。

   >[!IMPORTANT]
   >
   >此量度不会自动存储到某个 Analytics 变量中。您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics 上下文数据/Target 参数：`a.DaysSinceLastUpgrade`
   * Audience Manager 信号：`c_a_DaysSinceLastUpgrade`

* **上次升级后的启动次数**

   自应用程序版本号发生更改后的启动次数。

   >[!IMPORTANT]
   >
   >此量度不会自动存储到某个 Analytics 变量中。您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics 上下文数据/Target 参数：`a.LaunchesSinceUpgrade`
   * Audience Manager 信号：`c_a_LaunchesSinceUpgrade`

* **设备名称**

   存储设备名称。

   * Analytics 上下文数据/Target 参数：`a.DeviceName`
   * Audience Manager 信号：`c_a_DeviceName`

* **运营商名称**

   存储由设备提供的移动设备服务提供商的名称。

   >[!IMPORTANT]
   >
   >此量度不会自动存储到某个 Analytics 变量中。您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics 上下文数据/Target 参数：`a.CarrierName`
   * Audience Manager 信号：`c_a_CarrierName`

* **分辨率**

   宽 x 高（以实际像素为单位）。

   * Analytics 上下文数据/Target 参数：`a.Resolution`
   * Audience Manager 信号：`c_a_Resolution`


## 其他移动量度和维度 {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

以下量度和维度通过以下方法在移动设备解决方案变量中捕获：

### 量度

* **总操作时间**

   由 `trackTimedAction` 方法填充。

   * Analytics 上下文数据/Target 参数：`a.action.time.total`
   * Audience Manager 信号：`c_a_action_time_total`

* **应用程序中的操作时间**

   由 `trackTimedAction` 方法填充。
   * Analytics 上下文数据/Target 参数：`a.action.time.inapp`
   * Audience Manager 信号：`c_a_action_time_inapp`

* **生命周期值（事件）**

   由 `trackLifetimeValue` 方法填充。

   * Analytics 上下文数据/Target 参数：`a.ltv.amount`
   * Audience Manager 信号：`c_a_ltv_amount`

### 维度

* **位置（精确到 10 千米）**

   由 `trackLocation` 方法填充。

   * Analytics上下文数据/Target参数：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Manager特征：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **位置（精确到 100 米）**

   由 `trackLocation` 方法填充。

   * Analytics上下文数据/Target参数：

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager特征：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **位置（精确到 1 米）**

   由 `trackLocation` 方法填充。

   * Analytics上下文数据/Target参数：

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager特征：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **目标点名称**

   当设备位于定义的POI中时，由`trackLocation`方法填充。

   * Analytics 上下文数据/Target 参数：`a.loc.poi`
   * Audience Manager特征：`c_a_loc_poi`

* **与目标点中心的距离**

   当设备位于定义的POI内时，由`trackLocation`方法填充。

   * Analytics 上下文数据/Target 参数：`a.loc.dist`
   * Audience Manager特征：`c_a_loc_dist`

* **生命周期值（转化变量）**

   由 `trackLifetimeValue` 方法填充。

   * Analytics 上下文数据/Target 参数：  `a.ltv.amount`
   * Audience Manager特征：`c_a_ltv_amount`
