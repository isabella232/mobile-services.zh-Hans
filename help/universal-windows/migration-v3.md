---
description: 此部分介绍如何从 3.x 版本的旧 Windows Mobile SDK 迁移到适用于 Experience Cloud 解决方案的通用 Windows 平台 4.x SDK。
seo-description: 此部分介绍如何从 3.x 版本的旧 Windows Mobile SDK 迁移到适用于 Experience Cloud 解决方案的通用 Windows 平台 4.x SDK。
seo-title: Migrate to 4.x
solution: Marketing Cloud,Analytics
title: Migrate to 4.x
topic: 开发人员和实施
uuid: bdd6c5cd-3892-4e99-b69e-77105ad66e25
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrate to the 4.x SDKs{#migrate-to-x}

本节介绍如何从3.x版Windows移动SDK迁移到适用于Experience cloud解决方案的通用Windows Platform 4.x SDK。

With the move to version 4.x, all functionality is now accessible through static methods. You no longer need to keep track of your own objects.

以下部分将引导您完成从版本 3.x 迁移到版本 4.x 的步骤。

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

您可能注意到下载中包含一个新的 `ADBMobileConfig.json` 文件。此文件包含特定于应用程序的全局设置，并会替换在以前的版本中使用的大部分配置变量。

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

下表列出了需要移到配置文件的配置变量。请将为第一列中的变量设置的值移到第二列中的变量，然后从您的代码中删除旧的配置变量。

### 从3.x迁移

The following table provides a list of variables in the 3.x SDKs and the new name in the 4.x SDKs:

| 配置变量/方法 | Variable in the `ADBMobileConfig.json` file. |
|--- |--- |
| offlineTrackingEnabled | "offlineEnabled" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| setOfflineHitLimit | 删除，不再使用。 |
| linkTrackVars | 删除，不再使用。 |
| linkTrackEvents | 删除，不再使用。 |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

版本 4 SDK 将不使用以 Web 为主的 `Track` 和 `TrackLink` 调用，而是会使用两个在移动设备领域更具意义的方法：

* `TrackState`状态是指您的应用程序中提供的各种视图，例如“主页功能板”、“应用程序设置”、“购物车”等。这些状态与网站中的页面类似，而且 `trackState` 调用会使页面查看次数递增。

* `TrackAction`操作是指您的应用程序中发生的要测量的事件，例如“登录”、“横幅点按”、“信息源订阅”及其他量度。这些调用不会使页面查看次数递增。

用于这两种方法的 `contextData` 参数包含将作为上下文数据发送的名称值对。

### 事件、prop、eVar

If you've looked at the SDK methods, you are probably wondering where to set events, eVars, props, heirs, and lists. [](/help/universal-windows/c-configuration/methods.md)在版本 4 中，您不能再在应用程序中直接分配这些类型的变量。SDK 而是会使用上下文数据和处理规则将您的应用程序数据映射到 Analytics 变量以供报告。

处理规则具备以下优势：

* 您无需向应用商店提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 对发送额外数据的影响甚微。这些值在使用处理规则映射后才会显示在报表中。

For more information, see the Processing rules section in Analytics overview.**[](/help/universal-windows/analytics/analytics.md)

您直接分配到变量的任何值都应当添加到上下文数据中。This means that calls to `SetProp`, `SetEvar`, and assignments to persistent context data should all be removed and the values added to context data.

### AppSection/Server、GeoZip、事务ID、Campaign和其他标准变量

您在测量对象（包括上面列出的变量）中设置的任何其他数据都应添加到上下文数据中。That is, the only data sent in with a  or  call is the payload in the  parameter.`TrackState``TrackAction``data`

**替换跟踪调用**

在您的整个代码中，将以下方法替换为对 `trackState` 或 `trackAction` 的调用：

**从 3.x 迁移：**

* TrackAppState (TrackState)
* TrackEvents (TrackAction)
* Track (TrackAction)
* TrackLinkURL (TrackAction)

## 自定义 ID 服务 {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the  file. `ADBMobileConfig.json`所有其他脱机配置都会自动完成。

在您的整个代码中，删除对以下方法的调用：

**从 3.x 迁移：**

* SetOnline
* SetOffline

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

由于产品变量在处理规则中不可用，因此可以使用以下语法设置 `products`：

```js
// create a processing rule to set the corresponding product event. 
// for example, set the Product Views event when context data a.action = "product view" 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
cdata["&&products"] = ";Cool Shoe"; 
ADB.Analytics.trackAction("product view", cdata);
```

![](assets/prod-view.png)

The value of `"&&products"` (in this example, the value is `";Cool Shoe`") should follow the products string syntax for the type of event that you are tracking.
