---
description: 此信息可帮助您从 3.x 或 2.x 版本的 Android 库迁移至 4.x 版本的 Android 库。
keywords: android；库；移动；sdk
seo-description: 此信息可帮助您从 3.x 或 2.x 版本的 Android 库迁移至 4.x 版本的 Android 库。
seo-title: 迁移至 Android 4.x 库
solution: Marketing Cloud，Analytics
title: 迁移至 Android 4.x 库
topic: 开发人员和实施
uuid: 906e83bb-2aa-4aa2-ac9 b-3fba6 b833 c7 e
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrating to the Android 4.x library {#migrating-to-the-android-x-library}

此信息可帮助您从 3.x 或 2.x 版本的 Android 库迁移至 4.x 版本的 Android 库。

>[!IMPORTANT]
>
>The SDK uses `SharedPreferences` to store data that is needed to calculate unique users, lifecycle metrics, and other data related to core SDK functionality.  If you modify or remove the values in `SharedPreferences` that are expected by the SDK, unexpected behavior might result in the form of data inconsistencies.

在 4.x 版本的库中，公共方法都整合到一个标头中。此外，所有功能现在都可通过类级别方法访问，因此您无需跟踪指针、实例或单例。

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

在版本 4 中，您不能再在应用程序中分配变量，例如 event、eVar、prop、heir 和 list。SDK 而是会使用上下文数据和处理规则将您的应用程序数据映射到 Analytics 变量以供报告。

处理规则具备以下优势：

* 您无需向应用商店提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 对发送额外数据的影响甚微。

   这些值在使用处理规则映射后才会显示在报表中。

>[!TIP]
>
>Values that you assigned directly to variables should be added to the `data` HashMap.

## Remove unused properties {#section_145222EAA20F4CC2977DD883FDDBBFC5}

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

## Moving the configuration file and migrating to version 4 {#section_0B844235E0B04DD4B36976A73DB28FB5}

下表列出了需要移到配置文件的配置变量。

### 移动配置文件

1. 将为第一列中的变量设置的值移到第二列中的变量。
1. 从您的代码中删除旧配置变量。

### 从版本 3.x 迁移

要从3.x迁移到4，请将配置变量/方法值移至 `ADBMobileConfig.json` 变量。

| 配置变量或方法 | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| setOfflineTrackingEnabled | "offlineEnabled" |
| setOfflineHitLimit | "batchLimit" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | 删除，不再使用。 |
| linkTrackEvents | 删除，不再使用。 |

### 从版本 2.x 迁移

要从2.x迁移到版本4，请将值从第一列移至第二列中的变量。

| 配置变量 | Variable in the `ADBMobileConfig.json` file |
| --- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server"删除 `"https://"` 前缀。协议前缀将根据 "ssl" 设置自动添加。 |
| trackingServerSecure | 删除。为确保安全连接，请定义 "server"，然后启用 "ssl"。 |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | 删除，不再使用。 |
| linkTrackEvents | 删除，不再使用。 |
| timestamp | 删除，不再可配置。 |
| dc | 删除，不再使用。 |
| userAgent | 删除，不再可配置。 |
| dynamicVariablePrefix | 删除，不再使用。 |
| visitorNamespace | 删除，不再使用。 |
| usePlugins | 删除，不再使用。 |
| useBestPractices所有对流失测量 (getChurnInstance) 的调用 | 删除，由生命周期指标取代。 |

## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

SDK 版本 4 不使用以 Web 为主的 `track` 和 `trackLink` 调用，而是使用以下方法：

* `trackState`这是应用程序中可用的视图，如 `home dashboard`、 `app settings``cart`等。

   这些状态与网站中的页面类似，而且 `trackState` 调用会使页面查看次数递增。

* `trackAction` 应用程序中 `logons``banner taps``feed subscriptions`发生的操作，如您要测量的操作。

The `contextData` parameter for both of these methods is a `HashMap<String, Object>`, which contains the name-value pairs that are sent as context data.

## 事件、prop和eVar

在版本 4 中，您不能再在应用程序中直接分配变量，例如 event、eVar、prop、heir 和 list。SDK 现在会使用上下文数据和处理规则将您的应用程序数据映射到 Analytics 变量以供报告。

处理规则具备以下优势：

* 您无需向应用商店提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 对发送额外数据的影响甚微。

   这些值在使用处理规则映射后才会显示在报表中。有关更多信息，请参阅[处理规则和上下文数据](/help/android/getting-started/proc-rules.md)。

您直接分配到变量的值应当添加到 `data` 哈希映射中。This means that calls to `setProp`, `setEvar`, and assignments to persistent context data should be removed and the values be added to the `data` parameter.

## AppSection/server、Geozip、事务ID、Campaign和其他标准变量

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

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

`ADBMobileConfig.json` 在文件中启用离线跟踪，所有其他脱机配置都自动完成。

删除对以下方法的调用：

**版本 3.x**

* `setOnline`
* `setOffline`

**版本 2.x**

* `forceOffline`
* `forceOnline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

For more information about the products variable, see [Products variable](/help/android/analytics-main/products/products.md).

