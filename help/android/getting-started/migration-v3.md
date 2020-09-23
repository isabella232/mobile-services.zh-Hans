---
description: 此信息可帮助您从 3.x 或 2.x 版本的 Android 库迁移至 4.x 版本的 Android 库。
keywords: android;library;mobile;sdk
seo-description: 此信息可帮助您从 3.x 或 2.x 版本的 Android 库迁移至 4.x 版本的 Android 库。
seo-title: 迁移至 Android 4.x 库
solution: Experience Cloud,Analytics
title: 迁移至 Android 4.x 库
topic: Developer and implementation
uuid: 906e83bb-2faf-4aa2-ac9b-3fba6b833c7e
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 59%

---


# 迁移至 Android 4.x 库 {#migrating-to-the-android-x-library}

此信息可帮助您从 3.x 或 2.x 版本的 Android 库迁移至 4.x 版本的 Android 库。

>[!IMPORTANT]
>
>SDK 使用 `SharedPreferences` 来存储计算独特用户数所需的数据、生命周期量度以及与 SDK 核心功能相关的其他数据。如果您修改或删除了 `SharedPreferences` 中 SDK 所预期的值，则可能会出现意外行为，从而导致出现数据不一致的情况。

在版本4.x库中，公共方法合并到一个标头中。 此外，所有功能现在都可通过类级方法访问，因此您不必跟踪指针、实例或单个。

## Event、Prop 和 eVar {#section_76EA6F5611184C5CAE6E62956D84D7B6}

在版本4中，您无法再在应用程序中分配变量，如事件、eVar、prop、继承人和列表。 相反，SDK使用上下文数据和处理规则将应用程序数据映射到Analytics变量以进行报告。

处理规则具有以下优势：

* 您无需向App Store提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 发送额外数据几乎没有影响。

   这些值只有在使用处理规则映射后才会显示在报告中。

>[!TIP]
>
>您直接分配到变量的值应当添加到 `data` 哈希映射中。

## 删除未使用的属性 {#section_145222EAA20F4CC2977DD883FDDBBFC5}

新的 `ADBMobileConfig.json` 文件包含特定于应用程序的全局设置，并会替换在之前版本中使用的大部分配置变量。以下是 `ADBMobileConfig.json` 文件的示例：

```js
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
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

## 移动配置文件并迁移至版本 4 {#section_0B844235E0B04DD4B36976A73DB28FB5}

下表列出了需要移到配置文件的配置变量。

### 移动配置文件

1. 将为第一列中的变量设置的值移动到第二列中的变量。
1. 从代码中删除旧配置变量。

### 从版本 3.x 迁移

要从版本 3.x 迁移至版本 4，请将配置变量/方法值移到 `ADBMobileConfig.json` 变量。

| 配置变量或方法 | `ADBMobileConfig.json` 文件中的变量 |
|--- |--- |
| setOfflineTrackingEnabled | &quot;offlineEnabled&quot; |
| setOfflineHitLimit | &quot;batchLimit&quot; |
| reportSuiteID | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | “货币” |
| ssl | &quot;ssl&quot; |
| linkTrackVars | 删除，不再使用。 |
| linkTrackEvents | 删除，不再使用。 |

### 从版本 2.x 迁移

要从版本 2.x 迁移至版本 4，请将第一列中的值移到第二列中的变量。

| 配置变量 | `ADBMobileConfig.json` 文件中的变量 |
| --- |--- |
| trackOffline | &quot;offlineEnabled&quot; |
| offlineLimit | &quot;batchLimit&quot; |
| account | &quot;rsids&quot; |
| trackingServer | &quot;server&quot;, remove the `"https://"` prefix. 协议前缀会根据“ssl”设置自动添加。 |
| trackingServerSecure | 删除. 要实现安全连接，请定义“服务器”，然后启用“ssl”。 |
| charSet | &quot;charset&quot; |
| currencyCode | “货币” |
| ssl | &quot;ssl&quot; |
| linkTrackVars | 删除，不再使用。 |
| linkTrackEvents | 删除，不再使用。 |
| timestamp | 删除，不再可配置。 |
| dc | 删除，不再使用。 |
| userAgent | 删除，不再可配置。 |
| dynamicVariablePrefix | 删除，不再使用。 |
| visitorNamespace | 删除，不再使用。 |
| usePlugins | 删除，不再使用。 |
| useBestPractices所有对客户流失度量的调用(getChurnInstance) | 删除，替换为生命周期量度。 |

## 更新跟踪调用和跟踪变量 {#section_96E7D9B3CDAC444789503B7E7F139AB9}

SDK 版本 4 不使用以 Web 为主的 `track` 和 `trackLink` 调用，而是使用以下方法：

* `trackState`，这是您的应用程序中可用的一些视图，例如 `home dashboard`、`app settings`、`cart` 等等。

   这些状态与网站中的页面类似，而且 `trackState` 调用会使页面查看次数递增。

* `trackAction`，跟踪您的应用程序中发生的要测量的操作，例如 `logons`、`banner taps`、`feed subscriptions` 等。

用于这两种方法的 `contextData` 参数是 `HashMap<String, Object>`，其中包含作为上下文数据发送的名称值对。

## Event、Prop 和 eVar

在版本4中，您无法再直接在应用程序中分配变量，如事件、eVar、prop、继承人和列表。 SDK现在使用上下文数据和处理规则将您的应用程序数据映射到Analytics变量以进行报告。

处理规则具有以下优势：

* 您无需将更新提交到应用商店即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 发送额外数据几乎没有影响。

   这些值只有在使用处理规则映射后才会显示在报告中。 有关详细信息，请参 [阅处理规则和上下文数据](/help/android/getting-started/proc-rules.md)。

您直接分配到变量的值应当添加到 `data` 哈希映射中。这意味着应删除对 `setProp`、`setEvar` 的调用和对永久性上下文数据的分配，并将值添加到 `data` 参数中。

## AppSection/服务器、GeoZip、交易 ID、促销活动和其他标准变量

您在测量对象（包括上面列出的变量）中设置的数据应当添加到 `data` 哈希映射中。随 `trackState` 或 `trackAction` 调用发送的唯一数据是 `data` 参数中的有效负荷。

### 替换跟踪调用

将以下方法替换为对 `trackState` 或 `trackAction` 的调用：

* **从版本 3.x 迁移**

   * `trackAppState (trackState)`
   * `trackEvents (trackAction)`
   * `track (trackAction)`
   * `trackLinkURL (trackAction)`

* **从版本 2.x 迁移**

   * `track (trackState)`
   * `trackLink (trackAction)`

## 自定义访客 ID {#section_2CF930C13BA64F04959846E578B608F3}

将 `visitorID` 变量替换为对 `setUserIdentifier` 的调用。

## 离线跟踪 {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

离线跟踪在 `ADBMobileConfig.json` 文件中已启用，并且所有其他离线配置均已自动完成。

删除对以下方法的调用：

**版本 3.x**

* `setOnline`
* `setOffline`

**版本 2.x**

* `forceOffline`
* `forceOnline`

## 产品变量 {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

有关产品变量的更多信息，请参阅[产品变量](/help/android/analytics-main/products/products.md)。

