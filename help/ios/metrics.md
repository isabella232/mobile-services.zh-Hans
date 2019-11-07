---
description: 下表列出了实施生命周期后可由移动设备库自动测量的量度和维度。
seo-description: 下表列出了实施生命周期后可由移动设备库自动测量的量度和维度。
seo-title: 生命周期量度
solution: Marketing Cloud,Analytics
title: 生命周期量度
topic: 开发人员和实施
uuid: b795e383-d59b-4a3c-9e14-ffe8fb58412c
translation-type: ht
source-git-commit: a6608bf4d36a6fb6aca00f50cc058c09dbd931b1

---


# 生命周期量度 {#lifecycle-metrics}

以下是实施生命周期后可由移动设备库自动测量的量度和维度。

## 新的 Adobe Experience Platform Mobile SDK 发行版本

查找与 Adobe Experience Platform Mobile SDK 相关的信息和文档？单击[此处](https://aep-sdks.gitbook.io/docs/)可获取最新的文档。

在 2018 年 9 月，我们发布了一个新的 SDK 主要版本。这些新的 Adobe Experience Platform Mobile SDK 可通过 [Experience Platform Launch](https://www.adobe.com/cn/experience-platform/launch.html) 进行配置。

* 要开始配置，请转到 [Experience Platform Launch](https://launch.adobe.com/)。
* 要查看 Experience Platform SDK 存储库中的内容，请转到 [Github：Adobe Experience Platform SDK](https://github.com/Adobe-Marketing-Cloud/acp-sdks)。


## 生命周期量度和维度 {#section_78F036C4296F4BA3A47C2044F79C86C1}

配置生命周期量度后，这些量度会在上下文数据参数中发送到 Analytics，随每个 mbox 调用在参数中发送到 Target，以及作为信号发送到 Audience Manager。Analytics 和 Target 使用相同的格式，而 Audience Manager 则对每个量度使用不同的前缀。

对于 Analytics，系统将使用第一列中列出的量度或维度，自动捕获并报告随每个生命周期跟踪调用发送的上下文数据。

>[!TIP]
>
>该描述中提供了例外情况。

### 量度

* **首次启动次数**

   安装或重新安装后，在首次运行时触发。

   * Analytics 上下文数据/Target 参数：`a.InstallEvent`
   * Audience Manager 信号：`c_a_InstallEvent`

* **升级**

   升级后或每当版本号变更后，在首次运行时触发。

   * Analytics 上下文数据/Target 参数：`a.UpgradeEvent`
   * Audience Manager 信号：`c_a_UpgradeEvent`

* **每日参与的用户数**

   当特定的某天使用应用程序时触发。

   * Analytics 上下文数据/Target 参数：`a.DailyEngUserEvent`
   * Audience Manager 信号：`c_a_DailyEngUserEvent`

* **每月参与的用户数**

   当特定的某月使用应用程序时触发。

   * Analytics 上下文数据/Target 参数：`a.MonthlyEngUserEvent`
   * Audience Manager 信号：`c_a_MonthlyEngUserEvent`

* **启动次数**

   在每次运行时触发，包括崩溃次数和安装次数。当应用程序在超过生命周期会话超时后从后台恢复时也会触发。

   * Analytics 上下文数据/Target 参数：`a.LaunchEvent`
   * Audience Manager 信号：`c_a_LaunchEvent`

* **崩溃**

   当应用程序在关闭前未转入后台时触发。当应用程序在崩溃后再次启动时会发送该事件。Adobe Mobile 崩溃报告不实施全局未捕获异常处理程序。

   * Analytics 上下文数据/Target 参数：`a.CrashEvent`
   * Audience Manager 信号：`c_a_CrashEvent`

* **上一会话时长**

   根据应用程序在前台打开时间的长短，报告应用程序上一次会话持续的秒数。

   * Analytics 上下文数据/Target 参数：`a.PrevSessionLength`
   * Audience Manager 信号：`c_a_PrevSessionLength`

>[!IMPORTANT]
>
> “每日参与的用户数”**&#x200B;和“每月参与的用户数”**&#x200B;量度不会自动存储到 Analytics 量度中。您必须创建一个处理规则，以设置一个自定义事件来捕获这些量度。

#### 维度

* **安装日期**

   安装后首次启动的日期。日期格式为 `MM/DD/YYYY`。

   * Analytics 上下文数据/Target：`a.InstallDate`
   * 受众管理：`c_a_InstallDate`

* **应用程序 ID**

   采用 `[AppName] [BundleVersion]` 格式存储应用程序名称和版本。例如：`myapp 1.1`。

   * Analytics 上下文数据/Target：`a.AppID`
   * 受众管理：`c_a_AppID`

* **启动次数**

   应用程序启动或移出后台的次数。

   * Analytics 上下文数据/Target：`a.Launches`
   * 受众管理：`c_a_Launches`

* **首次使用后间隔天数**

   自首次运行以来经过的天数。

   * Analytics 上下文数据/Target：`a.DaysSinceFirstUse`
   * 受众管理：`c_a_DaysSinceFirstUse`

* **上次使用后间隔天数**

   上次使用后间隔的天数。

   * Analytics 上下文数据/Target：`a.DaysSinceLastUse`
   * 受众管理：`c_a_DaysSinceLastUse`

* **每天时间**

   测量应用程序启动的小时，采用 24 小时制数字格式。用于时间分片以确定峰值使用时间。

   * Analytics 上下文数据/Target：`a.HourOfDay`
   * 受众管理：`c_a_HourOfDay`

* **每周时间**

   应用程序星期几启动。

   * Analytics 上下文数据/Target：`a.DayOfWeek`
   * 受众管理：`c_a_DayOfWeek`

* **操作系统版本**

   自应用程序版本号发生更改后间隔的天数。

   * Analytics 上下文数据/Target：`a.OSVersion`
   * 受众管理：`c_a_OSVersion|OS version`

* **上次升级后间隔天数**

   上次升级后间隔天数。

   * Analytics 上下文数据/Target：`a.DaysSinceLastUpgrade`
   * 受众管理：`c_a_DaysSinceLastUpgrade`

* **上次升级后的启动次数**

   自应用程序版本号发生更改后的启动次数。

   * Analytics 上下文数据/Target：`a.LaunchesSinceUpgrade`
   * 受众管理：`c_a_LaunchesSinceUpgrade`

* **设备名称**

   存储设备名称。以逗号分隔的两位数字字符串，用于标识 iOS 设备。第一个数字通常代表第几代设备，第二个数字通常表示设备系列的不同成员。有关常用设备名称的列表，请参阅“iOS 设备版本”。

   * Analytics 上下文数据/Target：`a.DeviceName`
   * 受众管理：`c_a_DeviceName`

* **运营商名称**

   存储由设备提供的移动设备服务提供商的名称。

   * Analytics 上下文数据/Target：`a.CarrierName`
   * 受众管理：`c_a_CarrierName`

* **分辨率**

   宽 x 高（以实际像素为单位）。

   * Analytics 上下文数据/Target：`a.Resolution`
   * 受众管理：`c_a_Resolution`
   >[!IMPORTANT]
   >
   >“上次升级后间隔天数”**、“上次升级后的启动次数”**&#x200B;以及“运营商名称”**&#x200B;维度不会自动存储到 Analytics 变量中。您必须创建一个处理规则以将这些值复制到 Analytics 变量中以便进行报告。


## 其他移动量度和维度 {#section_0B32BBF9CA734103BEDB5E755FFE5B31}

移动设备解决方案变量采用所列的方法来捕获以下量度和维度。

### 量度

* **总操作时间**

   由 trackTimedAction 方法填充。

   * Analytics 上下文数据/Target 参数：`a.action.time.total`
   * 受众管理特征：`c_a_action_time_total`

* **应用程序中的操作时间**

   由 trackTimedAction 方法填充。

   * Analytics 上下文数据/Target 参数：`a.action.time.inapp`
   * 受众管理特征：`c_a_action_time_inapp`

* **生命周期值（事件）**

   由 trackLifetimeValue 方法填充。

   * Analytics 上下文数据/Target 参数：`a.ltv.amount`
   * 受众管理特征：`c_a_ltv_amount`


### 维度

* **位置（精确到 10 千米）**

   由 `trackLocation` 方法填充。

   * Analytics 上下文数据/Target 参数：

      * `a.loc.lat.a`
      * `a.loc.lon.a`
   * 受众管理特征：

      * `c_a_loc_lat_a`
      * `c_a_loc_lon_a`


* **位置（精确到 100 米）**

   由 trackLocation 方法填充。

   * Analytics 上下文数据/Target 参数：

      * `a.loc.lat.b`
      * `a.loc.lon.b`
   * 受众管理特征：

      * `c_a_loc_lat_b`
      * `c_a_loc_lon_b`


* **位置（精确到 1 米）**

   由 `trackLocation` 方法填充。

   * Analytics 上下文数据/Target 参数：

      * `a.loc.lat.c`
      * `a.loc.lon.c`
   * 受众管理特征：

      * `c_a_loc_lat_c`
      * `c_a_loc_lon_c`


* **目标点名称**

   当设备位于定义的 POI 中时，由 trackLocation 方法填充。

   * Analytics 上下文数据/Target 参数：`a.loc.poi`
   * 受众管理特征：`c_a_loc_poi`

* **与目标点中心的距离**

   当设备位于定义的 POI 中时，由 trackLocation 方法填充。

   * Analytics 上下文数据/Target 参数：`a.loc.dist`
   * 受众管理特征：`c_a_loc_dist`

* **生命周期值（转化变量）**

   由 trackLifetimeValue 方法填充。

   * Analytics 上下文数据/Target 参数：`a.ltv.amount`
   * 受众管理特征：`c_a_ltv_amount`

* **跟踪代码**

   由移动设备应用程序客户获取填充。由 Adobe Mobile Services 自动生成。

   * Analytics 上下文数据/Target 参数：`a.referrer.campaign.trackingcode`
   * 受众管理特征：`c_a_referrer_campaign_trackingcode`

* **Campaign**

   促销活动的名称，也存储在促销活动变量中。由移动设备应用程序客户获取填充。

   * Analytics 上下文数据/Target 参数：`a.referrer.campaign.name`
   * 受众管理特征：`c_a_referrer_campaign_name`

* **促销活动内容**

   显示链接的内容名称或内容 ID。由移动设备应用程序客户获取填充。

   * Analytics 上下文数据/Target 参数：`a.referrer.campaign.content`
   * 受众管理特征：`c_a_referrer_campaign_content`

* **促销活动媒介**

   营销媒介，如横幅或电子邮件。由移动设备应用程序客户获取填充。

   * Analytics 上下文数据/Target 参数：`a.referrer.campaign.medium`
   * 受众管理特征：`c_a_referrer_campaign_medium`

* **促销活动来源**

   原始反向链接，如新闻稿或社交媒体网络。由移动设备应用程序客户获取填充。

   * Analytics 上下文数据/Target 参数：`a.referrer.campaign.source`
   * 受众管理特征：`c_a_referrer_campaign_source`

* **促销活动搜索词**

   要通过此客户获取跟踪的付费关键词或其他搜索词。由移动设备应用程序客户获取填充。

   * Analytics 上下文数据/Target 参数：`a.referrer.campaign.term`
   * 受众管理特征：`c_a_referrer_campaign_term`
