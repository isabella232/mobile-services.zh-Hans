---
description: 列表可由移动库自动测量的指标和维度。
keywords: android;library;mobile;sdk
seo-description: 列表可由移动库自动测量的指标和维度。
seo-title: 生命周期量度
solution: Experience Cloud,Analytics
title: 生命周期量度
topic: Developer and implementation
uuid: c483271f-f620-46f4-aad8-d5f02d763f7d
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 61%

---


# 生命周期量度{#lifecycle-metrics}

列表可由移动库自动测量的指标和维度。

有关详细信息，请参 [阅生命周期数据疑难解答](https://helpx.adobe.com/cn/analytics/kb/troubleshoot-lifecycle-data.html)。

## 生命周期量度和维度 {#section_78F036C4296F4BA3A47C2044F79C86C1}

配置后，生命周期指标将以上下文数据参数的形式发送到Analytics，以参数形式发送到每个mbox调用的目标，并作为信号发送到Audience Manager。 分析和目标使用相同的格式，Audience Manager对每个指标使用不同的前缀。

对于Analytics，在中自动捕获每次生命周期跟踪调用时发送的上下文数据，并使用下面列出的度量或维度进行报告，并记录异常情况。

### 量度

* **首次启动次数**

   安装或重新安装后，在首次运行时触发。

   * Analytics context data/Target parameter: `a.InstallEvent`
   * Audience Manager 信号：`c_a_InstallEvent`

* **升级**

   升级后或版本号变更后，在首次运行时触发。

   * Analytics context data/Target parameter: `a.UpgradeEvent`
   * Audience Manager 信号：`c_a_UpgradeEvent`

* **每日参与的用户数**

   当特定的某天使用应用程序时触发。

   >[!TIP]
   >
   >此量度不会自动存储到某个 Analytics 量度中。您必须创建一个处理规则，以设置一个自定义事件用来捕获此量度。

   * Analytics context data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager 信号：`c_a_DailyEngUserEvent`

* **每月参与的用户数**

   当特定的某月使用应用程序时触发。

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

   * Analytics context data/Target: `a.InstallDate`
   * Audience Manager：`c_a_InstallDate`

* **应用程序 ID**

   采用 `[AppName] [BundleVersion]` 格式存储应用程序名称和版本。例如，`myapp 1.1` 便采用了上述格式。

   * Analytics context data/Target: `a.AppID`
   * Audience Manager：`c_a_AppID`

* **启动次数**

   应用程序启动或移出后台的次数。

   * Analytics context data/Target: `a.Launches`
   * Audience Manager：`c_a_Launches`

* **首次使用后间隔天数**

   首次运行后间隔的天数。

   * Analytics context data/Target: `a.DaysSinceFirstUse`
   * Audience Manager：`c_a_DaysSinceFirstUse`

* **上次使用后间隔天数**

   自上次使用以来经过的天数。

   * Analytics context data/Target: `a.DaysSinceLastUse`
   * Audience Manager：`c_a_DaysSinceLastUse`

* **每天时间**

   测量应用程序启动的小时。此量度采用 24 小时制数字格式，用于时间分片以确定峰值使用时间。

   * Analytics context data/Target: `a.HourOfDay`
   * Audience Manager：`c_a_HourOfDay`

* **每周时间**

   应用程序启动的星期数。

   * Analytics context data/Target: `a.DayOfWeek`
   * Audience Manager：`c_a_DayOfWeek`

* **操作系统版本**

   操作系统版本。

   * Analytics context data/Target: `a.OSVersion`
   * Audience Manager：`c_a_OSVersion`

* **上次升级后间隔天数**

   自应用程序版本号发生更改后间隔的天数。

   >[!IMPORTANT]
   >
   >此量度不会自动存储到某个 Analytics 变量中。您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics context data/Target: `a.DaysSinceLastUpgrade`
   * Audience Manager：`c_a_DaysSinceLastUpgrade`

* **上次升级后的启动次数**

   自应用程序版本号发生更改后的启动次数。

   >[!IMPORTANT]
   >
   >此量度不会自动存储到某个 Analytics 变量中。您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics context data/Target: `a.LaunchesSinceUpgrade`
   * Audience Manager：`c_a_LaunchesSinceUpgrade`

* **设备名称**

   存储设备名称。

   * Analytics context data/Target: `a.DeviceName`
   * Audience Manager：`c_a_DeviceName`

* **运营商名称**

   存储由设备提供的移动设备服务提供商的名称。

   >[!IMPORTANT]
   >
   >此量度不会自动存储到某个 Analytics 变量中。您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics context data/Target: `a.CarrierName`
   * Audience Manager：`c_a_CarrierName`

* **分辨率**

   宽 x 高（以实际像素为单位）。

   * Analytics context data/Target: `a.Resolution`
   * Audience Manager：`c_a_Resolution`


## 其他移动量度和维度 {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

以下指标和维度通过说明中列出的方法捕获在移动解决方案变量中。

### 量度

* **总操作时间**

   由 `trackTimedAction` 方法填充。

   * Analytics context data/Target parameter: `a.action.time.total`
   * Audience Manager trait: `c_a_action_time_total`

* **应用程序中的操作时间**

   由 `trackTimedAction` 方法填充。

   * Analytics context data/Target parameter: `a.action.time.inapp`
   * Audience Manager trait: `c_a_action_time_inapp`

* **生命周期值（事件）**

   由 `trackLifetimeValue` 方法填充。

   * Analytics context data/Target parameter: `a.ltv.amount`
   * Audience Manager trait: `c_a_ltv_amount`

## 维度

* **位置（精确到 10 千米）**

   由 `trackLocation` 方法填充。

   * Analytics上下文数据/目标参数：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience Manager特征：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **位置（精确到 100 米）**

   由 `trackLocation` 方法填充。

   * Analytics上下文数据/目标参数：

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience Manager特征：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **位置（精确到 1 米）**

   由 `trackLocation` 方法填充。

   * Analytics上下文数据/目标参数：

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Manager特征：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **目标点名称**

   Populated by `trackLocation` methods when device is within a defined POI.

   * Analytics context data/Target parameter: `a.loc.poi`
   * Audience Manager trait: `c_a_loc_poi`

* **与目标点中心的距离**

   Populated by `trackLocation` methods when device is within a defined POI.

   * Analytics context data/Target parameter: `a.loc.dist`
   * Audience Manager trait: `c_a_loc_dist`

* **生命周期值（转化变量）**

   由 `trackLifetimeValue` 方法填充。

   * Analytics context data/Target parameter: `a.ltv.amount`
   * Audience Manager trait: `c_a_ltv_amount`
