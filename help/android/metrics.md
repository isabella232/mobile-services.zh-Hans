---
description: 以下是在实施生命周期后可由移动设备库自动测量的量度和维度，以及生命周期数据疑难解答链接。
keywords: android;library;mobile;sdk
seo-description: 以下是在实施生命周期后可由移动设备库自动测量的量度和维度，以及生命周期数据疑难解答链接。
seo-title: 生命周期量度
solution: Marketing Cloud,Analytics
title: 生命周期量度
topic: 开发人员和实施
uuid: a8f3ebac-be3b-4948-82bb-105d46cfff6d
translation-type: tm+mt
source-git-commit: b690ec677cf5aedfb2673b707f82716af1851124

---


# Lifecycle metrics{#lifecycle-metrics}

本节提供有关在实施生命周期后由移动库自动测量的指标和维度的信息，以及生命周期数据疑难解答的链接。 For more information about troubleshooting, go to [Troubleshoot Lifecycle data](https://helpx.adobe.com/analytics/kb/troubleshoot-lifecycle-data.html).

## New Adobe Experience Platform Mobile SDK Release

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 进行配置。

* To get started, go to Adobe Experience Platform Launch.
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。

## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

配置后，生命周期量度会在上下文数据参数中发送到 Analytics，随每个 mbox 调用在参数中发送到 Target，以及作为信号发送到受众管理。Analytics 和 Target 使用相同的格式，而受众管理则对每个量度使用不同的前缀。

对于Analytics，使用度量或维度自动捕获和报告与每个生命周期跟踪调用一起发送的上下文数据，并记录异常情况。

### 量度

* **首次启动次数**

   安装或重新安装后，在首次运行时触发。

   * Analytics 上下文数据/Target 参数: `a.InstallEvent`
   * Audience Manager 信号: `c_a_InstallEvent`

* **升级**

   升级后或版本号变更后，在首次运行时触发。

   * Analytics 上下文数据/Target 参数: `a.UpgradeEvent`
   * Audience Manager 信号: `c_a_UpgradeEvent`

* **每日参与的用户数**

   当特定的某天使用应用程序时触发。

   >[!IMPORTANT]
   >
   >此量度不会自动存储在Analytics量度中。 您必须创建一个处理规则，以设置一个自定义事件用来捕获此量度。

   * Analytics 上下文数据/Target 参数: `a.DailyEngUserEvent`
   * Audience Manager 信号: `c_a_DailyEngUserEvent`

* **每月参与的用户**

   当特定的某月使用应用程序时触发。

   >[!IMPORTANT]
   >
   >此量度不会自动存储在Analytics量度中。 您必须创建一个处理规则，以设置一个自定义事件用来捕获此量度。

   * Analytics 上下文数据/Target 参数: `a.MonthlyEngUserEvent`
   * Audience Manager 信号: `c_a_MonthlyEngUserEvent`

* **启动次数**

   在每次运行时触发，包括崩溃次数和安装次数。在超过生命周期会话超时后从后台恢复时也会触发。

   >[!IMPORTANT]
   >
   >此量度不会自动存储在Analytics量度中。 您必须创建一个处理规则，以设置一个自定义事件用来捕获此量度。

   * Analytics 上下文数据/Target 参数: `a.LaunchEvent`
   * Audience Manager 信号: `c_a_LaunchEvent`

* **崩溃**

   当应用程序在关闭前未转入后台时触发。当应用程序在崩溃后启动时会发送该事件。Adobe Mobile 崩溃报告不实施全局未捕获异常处理程序。

   * Analytics 上下文数据/Target 参数: `a.CrashEvent`
   * Audience Manager 信号: `c_a_CrashEvent`

* **上一会话时长**

   根据应用程序在前台打开时间的长短，报告应用程序上一次会话持续的秒数。

   * Analytics 上下文数据/Target 参数: `a.PrevSessionLength`
   * Audience Manager 信号: `c_a_PrevSessionLength`


### 维度

* **安装日期**

   安装后首次启动的日期。日期格式为 MM/DD/YYYY。

   * Analytics 上下文数据/Target 参数: `a.InstallDate`
   * Audience Manager: `c_a_InstallDate`

* **应用程序 ID**

   Stores the application name and version in the `[AppName] [BundleVersion]` format. 例如，`myapp 1.1` 便采用了上述格式。

   * Analytics 上下文数据/Target 参数: `a.AppID`
   * Audience Manager: `c_a_AppID`

* **启动次数**

   应用程序启动或移出后台的次数。

   * Analytics 上下文数据/Target 参数: `a.Launches`
   * Audience Manager: `c_a_Launches`

* **首次使用后间隔天数**

   首次运行后间隔的天数。

   * Analytics 上下文数据/Target 参数: `a.DaysSinceFirstUse`
   * Audience Manager: `c_a_DaysSinceFirstUse`

* **上次使用后间隔天数**

   自上次使用以来经过的天数。

   * Analytics 上下文数据/Target 参数: `a.DaysSinceLastUse`
   * Audience Manager: `c_a_DaysSinceLastUse`

* **每天时间**

   测量应用程序启动的小时。此量度采用 24 小时制数字格式，用于时间分片以确定峰值使用时间。

   * Analytics 上下文数据/Target 参数: `a.HourOfDay`
   * Audience Manager: `c_a_HourOfDay`

* **每周时间**

   应用程序启动的星期数。

   * Analytics 上下文数据/Target 参数: `a.DayOfWeek`
   * Audience Manager: `c_a_DayOfWeek`

* **操作系统版本**

   操作系统版本。

   * Analytics 上下文数据/Target 参数: `a.OSVersion`
   * Audience Manager: `c_a_OSVersion`

* **上次升级后间隔天数**

   自应用程序版本号发生更改后间隔的天数。

   >[!IMPORTANT]
   >
   >此量度不会自动存储在Analytics变量中。 您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics 上下文数据/Target 参数: `a.DaysSinceLastUpgrade`
   * Audience Manager: `c_a_DaysSinceLastUpgrade`

* **上次升级后的启动次数**

   自应用程序版本号发生更改后的启动次数。

   >[!IMPORTANT]
   >
   >此量度不会自动存储在Analytics变量中。 您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics 上下文数据/Target 参数: `a.LaunchesSinceUpgrade`
   * Audience Manager: `c_a_LaunchesSinceUpgrade`

* **设备名称**

   存储设备名称。

   * Analytics 上下文数据/Target 参数: `a.DeviceName`
   * Audience Manager: `c_a_DeviceName`

* **运营商名称**

   存储由设备提供的移动设备服务提供商的名称。重要信息：此量度不会自动存储到某个 Analytics 变量中。您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   >[!IMPORTANT]
   >
   >此量度不会自动存储在Analytics变量中。 您必须创建一个处理规则以将此值复制到 Analytics 变量中以便进行报告。

   * Analytics 上下文数据/Target 参数: `a.CarrierName`
   * Audience Manager: `c_a_CarrierName`

* **分辨率**

   宽 x 高（以实际像素为单位）。

   * Analytics 上下文数据/Target 参数: `a.Resolution`
   * Audience Manager: `c_a_Resolution`

## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

以下量度和维度由&#x200B;**描述**&#x200B;列中列出的方法在移动设备解决方案变量中捕获。

### 量度

* **总操作时间**

   Populated by `trackTimedAction` methods.

   * Analytics 上下文数据/Target 参数: `a.action.time.total`
   * Audience Manager Trait: `c_a_action_time_total`

* **应用程序中的操作时间**

   Populated by `trackTimedAction` methods.

   * Analytics 上下文数据/Target 参数: `a.action.time.inapp`
   * Audience manager特征： `c_a_action_time_inapp`

* **生命周期值（事件）**

   Populated by `trackLifetimeValue` methods.

   * Analytics 上下文数据/Target 参数: `a.ltv.amount`
   * Audience Manager Trait: `c_a_ltv_amount`

### 维度

* **位置（精确到 10 千米）**

   Populated by `trackLocation` methods.

   * Analytics Context Data/Target Parameters:

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * Audience manager特征：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **位置（精确到 100 米）**

   由 trackLocation 方法填充。

   * Analytics上下文数据／目标参数：

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * Audience manager特征：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **位置（精确到 1 米）**

   由 trackLocation 方法填充。

   * Analytics上下文数据／目标参数：

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience manager特征：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **目标点名称**

   当设备位于定义的 POI 中时，由 trackLocation 方法填充。

   * Analytics Context Data/Target Parameters: `a.loc.poi`
   * Audience manager特征： `c_a_loc_poi`

* **与目标点中心的距离**

   当设备位于定义的 POI 中时，由 trackLocation 方法填充。

   * Analytics Context Data/Target Parameters: `a.loc.dist`
   * Audience manager特征： `c_a_loc_dist`

* **生命周期值（转化变量）**

   由 trackLifetimeValue 方法填充。

   * Analytics Context Data/Target Parameters: `a.ltv.amount`
   * Audience manager特征： `c_a_ltv_amount`

* **跟踪代码**

   由移动设备应用程序客户获取填充，并由 Adobe Mobile Services 自动生成。

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.trackingcode`
   * Audience manager特征： `c_a_referrer_campaign_trackingcode`

* ** Campaign

   促销活动的名称，也存储在促销活动变量中。由移动设备应用程序客户获取填充。

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.name`
   * Audience manager特征： `c_a_referrer_campaign_name`

* **促销活动内容**

   显示链接的内容名称或内容 ID。由移动设备应用程序客户获取填充。

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.content`
   * Audience manager特征： `c_a_referrer_campaign_content`

* **促销活动媒介**

   营销媒介，如横幅或电子邮件。由移动设备应用程序客户获取填充。

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.medium`
   * Audience manager特征： `c_a_referrer_campaign_medium`

* **促销活动来源**

   原始反向链接，如新闻稿或社交媒体网络。由移动设备应用程序客户获取填充。

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.source`
   * Audience manager特征： `c_a_referrer_campaign_source`

* **促销活动搜索词**

   要通过此客户获取跟踪的付费关键词或其他搜索词。由移动设备应用程序客户获取填充。

   * Analytics Context Data/Target Parameters: `a.referrer.campaign.term`
   * Audience manager特征： `c_a_referrer_campaign_term`
