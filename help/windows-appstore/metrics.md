---
description: 列出可由移动设备库自动测量的量度和维度。
keywords: android；库；移动；sdk
seo-description: 列出可由移动设备库自动测量的量度和维度。
seo-title: 生命周期量度
solution: Marketing Cloud,Analytics
title: 生命周期量度
topic: 开发人员和实施
uuid: c483271f-f620-46f4-aad8-d5f02d763f7d
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Lifecycle metrics{#lifecycle-metrics}

列出可由移动设备库自动测量的量度和维度。

有关详细信息，请参阅 [生命周期数据疑难解答](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html)。

## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

配置后，生命周期量度会在上下文数据参数中发送到 Analytics，随每个 mbox 调用在参数中发送到 Target，以及作为信号发送到 Audience Manager。Analytics和Target使用相同的格式，Audience manager对每个指标使用不同的前缀。

对于Analytics，使用下面列出的度量或维度自动捕获并报告与每个生命周期跟踪调用一起发送的上下文数据，并记录异常情况。

### 量度

* **首次启动次数**

   安装或重新安装后，在首次运行时触发。

   * Analytics context data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **升级**

   升级后或版本号变更后，在首次运行时触发。

   * Analytics context data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **每日参与的用户数**

   当特定的某天使用应用程序时触发。

   >[!TIP]
   >
   >此量度不会自动存储在Analytics量度中。 您必须创建一个处理规则，以设置一个自定义事件用来捕获此量度。

   * Analytics context data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **每月参与的用户**

   当特定的某月使用应用程序时触发。

   >[!IMPORTANT]
   >
   >此量度不会自动存储在Analytics量度中。 您必须创建一个处理规则，以设置一个自定义事件用来捕获此量度。

   * Analytics context data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **启动次数**

   在每次运行时触发，包括崩溃次数和安装次数。在超过生命周期会话超时后从后台恢复时也会触发。

   * Analytics context data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **崩溃**

   当应用程序在关闭前未转入后台时触发。当应用程序在崩溃后启动时会发送该事件。Adobe Mobile 崩溃报告不实施全局未捕获异常处理程序。

   * Analytics context data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **上一会话时长**

   根据应用程序在前台打开时间的长短，报告应用程序上一次会话持续的秒数。

   * Analytics context data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`

### 维度

* **安装日期**

   安装后首次启动的日期。日期格式为 `MM/DD/YYYY`。

   * Analytics context data/Target: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **应用程序 ID**

   Stores the application name and version in the `[AppName] [BundleVersion]` format. 例如，`myapp 1.1` 便采用了上述格式。

   * Analytics context data/Target: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **启动次数**

   应用程序启动或移出后台的次数。

   * Analytics context data/Target: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **首次使用后间隔天数**

   首次运行后间隔的天数。

   * Analytics context data/Target: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **上次使用后间隔天数**

   自上次使用以来经过的天数。

   * Analytics context data/Target: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **每天时间**

   测量应用程序启动的小时。此量度采用 24 小时制数字格式，用于时间分片以确定峰值使用时间。

   * Analytics context data/Target: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **每周时间**

   应用程序启动的星期数。

   * Analytics context data/Target: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **操作系统版本**

   操作系统版本。

   * Analytics context data/Target: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **上次升级后间隔天数**

   自应用程序版本号发生更改后间隔的天数。

   >[!IMPORTANT]
   >
   >此量度不会自动存储在Analytics变量中。 您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics context data/Target: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **上次升级后的启动次数**

   自应用程序版本号发生更改后的启动次数。

   >[!IMPORTANT]
   >
   >此量度不会自动存储在Analytics变量中。 您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics context data/Target: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **设备名称**

   存储设备名称。

   * Analytics context data/Target: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **运营商名称**

   存储由设备提供的移动设备服务提供商的名称。

   >[!IMPORTANT]
   >
   >此量度不会自动存储在Analytics变量中。 您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics context data/Target: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **分辨率**

   宽 x 高（以实际像素为单位）。

   * Analytics context data/Target: `a.Resolution`
   * Audience Manager: `c_a_Resolution`


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

The following metrics and dimensions are captured in mobile solution variables by the methods listed in the description.

### 量度

* **总操作时间**

   Populated by `trackTimedAction` methods.

   * Analytics context data/Target parameter: `a.action.time.total`
   * Audience manager特征： `c_a_action_time_total`

* **应用程序中的操作时间**

   Populated by `trackTimedAction` methods.

   * Analytics context data/Target parameter: `a.action.time.inapp`
   * Audience manager特征： `c_a_action_time_inapp`

* **生命周期值（事件）**

   Populated by `trackLifetimeValue` methods.

   * Analytics context data/Target parameter: `a.ltv.amount`
   * Audience manager特征： `c_a_ltv_amount`

## 维度

* **位置（精确到 10 千米）**

   Populated by `trackLocation` methods.

   * Analytics上下文数据/Target参数：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience manager特征：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **位置（精确到 100 米）**

   Populated by `trackLocation` methods.

   * Analytics上下文数据/Target参数：

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager trait:

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **位置（精确到 1 米）**

   Populated by `trackLocation` methods.

   * Analytics上下文数据/Target参数：

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager trait:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **目标点名称**

   当设备位于定义的 POI 中时，由 `trackLocation` 方法填充。

   * Analytics context data/Target parameter: `a.loc.poi`
   * Audience Manager trait: `c_a_loc_poi`

* **与目标点中心的距离**

   当设备位于定义的 POI 中时，由 `trackLocation` 方法填充。

   * Analytics context data/Target parameter: `a.loc.dist`
   * Audience Manager trait: `c_a_loc_dist`

* **生命周期值（转化变量）**

   Populated by `trackLifetimeValue` methods.

   * Analytics context data/Target parameter: `a.ltv.amount`
   * Audience manager特征： `c_a_ltv_amount`
