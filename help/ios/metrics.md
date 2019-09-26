---
description: 下表列出了实施生命周期后可由移动设备库自动测量的量度和维度。
seo-description: 下表列出了实施生命周期后可由移动设备库自动测量的量度和维度。
seo-title: 生命周期量度
solution: Marketing Cloud,Analytics
title: 生命周期量度
topic: 开发人员和实施
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
translation-type: tm+mt
source-git-commit: a6608bf4d36a6fb6aca00f50cc058c09dbd931b1

---


# Lifecycle metrics {#lifecycle-metrics}

以下是在实施生命周期后，移动库可以自动测量的指标和维度。

## 新版Adobe Experience Platform Mobile SDK

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html) 进行配置。

* To get started, go to [Experience Platform Launch](https://launch.adobe.com/).
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。


## Lifecycle metrics and dimensions {#section_78F036C4296F4BA3A47C2044F79C86C1}

配置生命周期量度后，这些量度会在上下文数据参数中发送到 Analytics，随每个 mbox 调用在参数中发送到 Target，以及作为信号发送到 Audience Manager。Analytics 和 Target 使用相同的格式，而 Audience Manager 则对每个量度使用不同的前缀。

对于 Analytics，系统将使用第一列中列出的量度或维度，自动捕获并报告随每个生命周期跟踪调用发送的上下文数据。

>[!TIP]
>
>说明中提供了例外。

### 量度

* **首次启动次数**

   安装或重新安装后，在首次运行时触发。

   * Analytics Context Data/Target parameter: `a.InstallEvent`
   * Audience Manager signal: `c_a_InstallEvent`

* **升级**

   升级后或每当版本号变更后，在首次运行时触发。

   * Analytics Context Data/Target parameter: `a.UpgradeEvent`
   * Audience Manager signal: `c_a_UpgradeEvent`

* **每日参与的用户数**

   当特定的某天使用应用程序时触发。

   * Analytics Context Data/Target parameter: `a.DailyEngUserEvent`
   * Audience Manager signal: `c_a_DailyEngUserEvent`

* **每月参与的用户**

   当特定的某月使用应用程序时触发。

   * Analytics Context Data/Target parameter: `a.MonthlyEngUserEvent`
   * Audience Manager signal: `c_a_MonthlyEngUserEvent`

* **启动次数**

   在每次运行时触发，包括崩溃次数和安装次数。当应用程序在超过生命周期会话超时后从后台恢复时也会触发。

   * Analytics Context Data/Target parameter: `a.LaunchEvent`
   * Audience Manager signal: `c_a_LaunchEvent`

* **崩溃**

   当应用程序在关闭前未转入后台时触发。当应用程序在崩溃后再次启动时会发送该事件。Adobe Mobile 崩溃报告不实施全局未捕获异常处理程序。

   * Analytics Context Data/Target parameter: `a.CrashEvent`
   * Audience Manager signal: `c_a_CrashEvent`

* **上一会话时长**

   根据应用程序在前台打开时间的长短，报告应用程序上一次会话持续的秒数。

   * Analytics Context Data/Target parameter: `a.PrevSessionLength`
   * Audience Manager signal: `c_a_PrevSessionLength`

>[!IMPORTANT]
>
> “每 *日参与的用户* ”和“ *每月参与的用户* ”量度不会自动存储在“分析”量度中。 您必须创建一个处理规则，以设置自定义事件以捕获这些度量。

#### 维度

* **安装日期**

   安装后首次启动的日期。日期格式为 `MM/DD/YYYY`。

   * Analytics 上下文数据/Target: `a.InstallDate`
   * 受众管理: `c_a_InstallDate`

* **应用程序 ID**

   Stores the Application name and version in the `[AppName] [BundleVersion]` format. 例如：`myapp 1.1`。

   * Analytics 上下文数据/Target: `a.AppID`
   * 受众管理: `c_a_AppID`

* **启动次数**

   应用程序启动或移出后台的次数。

   * Analytics 上下文数据/Target: `a.Launches`
   * 受众管理: `c_a_Launches`

* **首次使用后间隔天数**

   自首次运行以来经过的天数。

   * Analytics 上下文数据/Target: `a.DaysSinceFirstUse`
   * 受众管理: `c_a_DaysSinceFirstUse`

* **上次使用后间隔天数**

   上次使用后间隔的天数。

   * Analytics 上下文数据/Target: `a.DaysSinceLastUse`
   * 受众管理: `c_a_DaysSinceLastUse`

* **每天时间**

   测量应用程序启动的小时，采用 24 小时制数字格式。用于时间分片以确定峰值使用时间。

   * Analytics 上下文数据/Target: `a.HourOfDay`
   * 受众管理: `c_a_HourOfDay`

* **每周时间**

   应用程序星期几启动。

   * Analytics 上下文数据/Target: `a.DayOfWeek`
   * 受众管理: `c_a_DayOfWeek`

* **操作系统版本**

   自应用程序版本号发生更改后间隔的天数。

   * Analytics 上下文数据/Target: `a.OSVersion`
   * 受众管理: `c_a_OSVersion|OS version`

* **上次升级后间隔天数**

   上次升级后间隔天数.

   * Analytics 上下文数据/Target: `a.DaysSinceLastUpgrade`
   * 受众管理: `c_a_DaysSinceLastUpgrade`

* **上次升级后的启动次数**

   自应用程序版本号发生更改后的启动次数。

   * Analytics 上下文数据/Target: `a.LaunchesSinceUpgrade`
   * 受众管理: `c_a_LaunchesSinceUpgrade`

* **设备名称**

   存储设备名称。以逗号分隔的两位数字字符串，用于标识 iOS 设备。第一个数字通常代表第几代设备，第二个数字通常表示设备系列的不同成员。有关常用设备名称的列表，请参阅  iOS 设备版本.

   * Analytics 上下文数据/Target: `a.DeviceName`
   * 受众管理: `c_a_DeviceName`

* **运营商名称**

   存储由设备提供的移动设备服务提供商的名称。

   * Analytics 上下文数据/Target: `a.CarrierName`
   * 受众管理: `c_a_CarrierName`

* **分辨率**

   宽 x 高（以实际像素为单位）。

   * Analytics 上下文数据/Target: `a.Resolution`
   * 受众管理: `c_a_Resolution`
   >[!IMPORTANT]
   >
   >上次 *升级后的天数*、上次 *升级后的启动次数*** ，以及运营商名称维度不会自动存储在Analytics变量中。 You must create a processing rule to copy the values to an Analytics variable for reporting.


## Additional mobile metrics and dimensions {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

以下指标和维度通过列出的方法在移动解决方案变量中捕获。

### 量度

* **总操作时间**

   由 trackTimedAction 方法填充。

   * Analytics Context Data/Target parameter: `a.action.time.total`
   * Audience Management trait: `c_a_action_time_total`

* **应用程序中的操作时间**

   由 trackTimedAction 方法填充。

   * Analytics Context Data/Target parameter: `a.action.time.inapp`
   * Audience Management trait: `c_a_action_time_inapp`

* **生命周期值（事件）**

   由 trackLifetimeValue 方法填充。

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`


### 维度

* **位置（精确到 10 千米）**

   Populated by `trackLocation` methods.

   * Analytics Context Data/Target参数：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * 受众管理特征：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **位置（精确到 100 米）**

   由 trackLocation 方法填充。

   * Analytics Context Data/Target参数：

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * 受众管理特征：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **位置（精确到 1 米）**

   Populated by `trackLocation` methods.

   * Analytics Context Data/Target parameter:

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * Audience Management trait:

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **目标点名称**

   当设备位于定义的 POI 中时，由 trackLocation 方法填充。

   * Analytics Context Data/Target parameter: `a.loc.poi`
   * Audience Management trait: `c_a_loc_poi`

* **与目标点中心的距离**

   当设备位于定义的 POI 中时，由 trackLocation 方法填充。

   * Analytics Context Data/Target parameter: `a.loc.dist`
   * Audience Management trait: `c_a_loc_dist`

* **生命周期值（转化变量）**

   由 trackLifetimeValue 方法填充。

   * Analytics Context Data/Target parameter: `a.ltv.amount`
   * Audience Management trait: `c_a_ltv_amount`

* **跟踪代码**

   由移动设备应用程序客户获取填充。由 Adobe Mobile Services 自动生成。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.trackingcode`
   * Audience Management trait: `c_a_referrer_campaign_trackingcode`

* **Campaign**

   促销活动的名称，也存储在促销活动变量中。由移动设备应用程序客户获取填充。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.name`
   * Audience Management trait: `c_a_referrer_campaign_name`

* **促销活动内容**

   显示链接的内容名称或内容 ID。由移动设备应用程序客户获取填充。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.content`
   * Audience Management trait: `c_a_referrer_campaign_content`

* **促销活动媒介**

   营销媒介，如横幅或电子邮件。由移动设备应用程序客户获取填充。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.medium`
   * Audience Management trait: `c_a_referrer_campaign_medium`

* **促销活动来源**

   原始反向链接，如新闻稿或社交媒体网络。由移动设备应用程序客户获取填充。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.source`
   * Audience Management trait: `c_a_referrer_campaign_source`

* **促销活动搜索词**

   要通过此客户获取跟踪的付费关键词或其他搜索词。由移动设备应用程序客户获取填充。

   * Analytics Context Data/Target parameter: `a.referrer.campaign.term`
   * Audience Management trait: `c_a_referrer_campaign_term`
