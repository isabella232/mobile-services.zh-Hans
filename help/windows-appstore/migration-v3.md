---
description: 本节介绍如何从先前Windows移动SDK的3.x版本迁移到Windows 8.1通用App Store 4.x SDK for Experience Cloud解决方案。
seo-description: 本节介绍如何从先前Windows移动SDK的3.x版本迁移到Windows 8.1通用App Store 4.x SDK for Experience Cloud解决方案。
seo-title: 迁移到4.x SDK
solution: Experience Cloud,Analytics
title: 迁移到4.x SDK
topic-fix: Developer and implementation
uuid: e0fe3b7b-cda5-4a91-834c-2c7e17a501a3
exl-id: d6dc34f2-61b7-4026-a66a-19284e21e69c
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 24%

---

# 迁移到4.x SDK {#migrate-to-the-x-sdks}

本节介绍如何从先前Windows移动SDK的3.x版本迁移到Windows 8.1通用App Store 4.x SDK for Experience Cloud解决方案。

迁移到4.x版后，所有功能现在都可通过静态方法访问，因此无需再跟踪您自己的对象。

以下部分将指导您从3.x版迁移到4.x版。

## 删除未使用的属性 {#section_145222EAA20F4CC2977DD883FDDBBFC5}

您可能注意到下载中包含一个新的`ADBMobileConfig.json`文件。 此文件包含特定于应用程序的全局设置，并替换在早期版本中使用的大多数配置变量。 以下是 `ADBMobileConfig.json` 文件的示例：

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

## 从3.x迁移

| 配置变量/方法 | `ADBMobileConfig.json`文件中的变量。 |
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

版本4 SDK没有使用以Web为焦点的`Track`和`TrackLink`调用，而是使用两种在移动世界中意义更大的方法：

* `TrackState` 状态是您的应用程序中提供的视图，如“主仪表板”、“应用程序设置”、“购物车”等。这些状态与网站中的页面类似，而且 `trackState` 调用会使页面查看次数递增。

* `TrackAction` 操作是您要衡量的应用程序中发生的事情，如“登录”、“横幅点击”、“源订阅”和其他量度。这些调用不会增加页面视图。

这两种方法的`contextData`参数都包含作为上下文数据发送的名称 — 值对。

## 事件、Prop、eVar

如果您已查看[SDK方法](/help/windows-appstore/c-configuration/methods.md)，您可能会想知道在哪里设置事件、eVar、prop、继承和列表。 在版本4中，您无法再直接在应用程序中分配这些类型的变量。 反而，SDK 使用上下文数据和处理规则将应用程序数据映射到 Analytics 变量以便进行报告。

处理规则为您提供了几个优势：

* 您无需向应用商店提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 对发送额外数据的影响很小。使用处理规则映射这些值之前，这些值不会显示在报表中。

有关详细信息，请参阅[Analytics](/help/windows-appstore/analytics/analytics.md)中的&#x200B;*处理规则*。

您直接分配给变量的任何值都应添加到上下文数据中。 这意味着应全部删除对`SetProp`、`SetEvar`的调用以及对永久上下文数据的分配以及添加到上下文数据的值。

**AppSection/Server、GeoZip、事务ID、活动和其他标准变量**

您在测量对象上设置的任何其他数据（包括上面列出的变量）应该添加到上下文数据中。

简单地说，随`TrackState`或`TrackAction`调用发送的唯一数据是`data`参数中的有效负荷。

### 替换跟踪调用

在整个代码中，将以下方法替换为对`trackState`或`trackAction`的调用：

### 从3.x迁移

* `TrackAppState` (TrackState)
* `TrackEvents` (TrackAction)
* `Track` (TrackAction)
* `TrackLinkURL` (TrackAction)

## 自定义访客 ID {#section_2CF930C13BA64F04959846E578B608F3}

将 `visitorID` 变量替换为对 `setUserIdentifier` 的调用。

## 离线跟踪 {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

在`ADBMobileConfig.json`文件中启用脱机跟踪。所有其他脱机配置都会自动完成。

在整个代码中，删除对以下方法的调用：

### 从3.x迁移

* `SetOnline`
* `SetOffline`

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

在此示例中，`"&&products"`的值为`";Cool Shoe`&quot;，并应遵循您所跟踪的事件类型的产品字符串语法。
