---
description: 本节介绍如何从先前的Windows移动SDK的3.x版本迁移到通用型Windows平台4.x SDK forExperience Cloud解决方案。
seo-description: 本节介绍如何从先前的Windows移动SDK的3.x版本迁移到通用型Windows平台4.x SDK forExperience Cloud解决方案。
seo-title: 迁移至 4.x
solution: Experience Cloud,Analytics
title: 迁移至 4.x
topic: Developer and implementation
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 26%

---


# 迁移到4.x SDK{#migrate-to-x}

本节介绍如何从3.x版Windows移动SDK迁移到通用型Windows平台4.x SDK forExperience Cloud解决方案。

移动到4.x版后，现在可通过静态方法访问所有功能。 您不再需要跟踪自己的对象。

以下部分将指导您从3.x版迁移到4.x版。

## 删除未使用的属性 {#section_145222EAA20F4CC2977DD883FDDBBFC5}

您可能注意到下载 `ADBMobileConfig.json` 中包含一个新文件。 此文件包含特定于应用程序的全局设置，并替换先前版本中使用的大多数配置变量。

以下是 `ADBMobileConfig.json` 文件的示例：

```js
{ 
    "version" : "1.0", 
    "analytics" : { 
        "rsids" : "coolApp", 
        "server" : "my.CoolApp.com", 
        "charset" : "UTF-8", 
        "ssl" : true, 
        "offlineEnabled" : true, 
        "lifecycleTimeout" : 300, 
        "privacyDefault" : "optedin", 
        "poi" : [ 
                    ["san francisco",37.757144,-122.44812,7000], 
                    ["santa cruz",36.972935,-122.01725,600] 
                ] 
    }, 
 "target" : { 
  "clientCode" : "myTargetClientCode", 
  "timeout" : 5 
 }, 
 "audienceManager" : { 
  "server" : "myServer.demdex.com" 
 } 
}
```

下表列出了需要移到配置文件的配置变量。将第一列中变量的设置值移动到第二列中的变量，然后从代码中删除旧配置变量。

### 从3.x迁移

下表提供3.x SDK中的变量列表和4.x SDK中的新名称：

| 配置变量／方法 | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| setOfflineHitLimit | 删除，不再使用。 |
| linkTrackVars | 删除，不再使用。 |
| linkTrackEvents | 删除，不再使用。 |

## 更新跟踪调用和跟踪变量 {#section_96E7D9B3CDAC444789503B7E7F139AB9}

版本4 SDK不使用 `Track` 以 `TrackLink` Web为中心的调用，而是使用两种在移动世界中更有意义的方法：

* `TrackState` 状态是您的应用程序中可用的视图，如“主仪表板”、“应用程序设置”、“购物车”等。 这些状态与网站中的页面类似，而且 `trackState` 调用会使页面查看次数递增。

* `TrackAction` 操作是您要衡量的应用程序中发生的事情，如“登录”、“横幅点击”、“源订阅”和其他指标。 这些调用不会增加页面视图。

The `contextData` parameter for both of these methods contains name-value pairs that are sent as context data.

### Event、Prop、eVar

如果您已经研究过SDK [方法](/help/universal-windows/c-configuration/methods.md)，您可能会想知道在哪里设置事件、eVar、prop、继承人和列表。 在版本4中，您无法再直接在应用程序中分配这些类型的变量。 反而，SDK 使用上下文数据和处理规则将应用程序数据映射到 Analytics 变量以便进行报告。

处理规则具有以下优势：

* 您无需向应用商店提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 对发送额外数据的影响很小。这些值只有在使用处理规则映射后才会显示在报告中。

有关详细信息，请参阅 *Analytics概述* 中的处理 [规则部分](/help/universal-windows/analytics/analytics.md)。

您直接分配给变量的任何值都应添加到上下文数据中。 This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

### AppSection/服务器、GeoZip、交易 ID、促销活动和其他标准变量

您在测量对象上设置的任何其他数据（包括上面列出的变量）应改为添加到上下文数据。 即，随或调用发送的唯一数 `TrackState` 据 `TrackAction` 是参数中的有效负 `data` 荷。

**替换跟踪调用**

Throughout your code, replace the following methods with a call to `trackState` or `trackAction`:

**从3.x迁移：**

* TrackAppState(TrackState)
* TrackEvents(TrackAction)
* 跟踪（跟踪操作）
* TrackLinkURL(TrackAction)

## 自定义ID服务 {#section_2CF930C13BA64F04959846E578B608F3}

将 `visitorID` 变量替换为对 `setUserIdentifier` 的调用。

## 离线跟踪 {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file. All other offline configuration is done automatically.

在整个代码中，删除对以下方法的调用：

**从3.x迁移：**

* SetOnline
* SetOffline

## 产品变量 {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

由于产品变量在处理规则中不可用，因此可以使用以下语法设置 `products`：

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

值(在 `"&&products"` 本示例中，该值为 `";Cool Shoe`“)应遵循您所跟踪的事件类型的产品字符串语法。
