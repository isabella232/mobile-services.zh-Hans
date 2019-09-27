---
description: 此信息可帮助您从 3.x 或 2.x 版本的 iOS 库迁移至 4.x 版本的 iOS 库。
seo-description: 此信息可帮助您从 3.x 或 2.x 版本的 iOS 库迁移至 4.x 版本的 iOS 库。
seo-title: 迁移到4.x iOS库
solution: Marketing Cloud,Analytics
title: Migrating to the 4.x iOS library
topic: 开发人员和实施
uuid: 5668972b-f355-4e03-9df0-8c82ddf6809b
translation-type: tm+mt
source-git-commit: 68bc21f1c6dba2faeed332495592114af90c8f61

---


# Migrating to the 4.x iOS library{#migrating-to-the-x-ios-library}

此信息可帮助您从 3.x 或 2.x 版本的 iOS 库迁移至 4.x 版本的 iOS 库。

>[!IMPORTANT]
>
>The SDK uses `NSUserDefaults` to store data that is needed to calculate unique users, lifecycle metrics, and other data related to core SDK functionality.  If you modify or remove the values in `NSUserDefaults` that are expected by the SDK, unexpected behavior might result in the form of data inconsistencies.

In the version 4.x of the iOS SDK library, the public methods are consolidated into one header. 此外，该功能现在可通过类级方法访问，因此您不必跟踪指针、实例或单个。

## Events, props, and eVars {#section_76EA6F5611184C5CAE6E62956D84D7B6}

在版本 4 中，您不能再在应用程序中直接分配变量，例如 event、eVar、prop、heir 和 list。SDK 而是会使用上下文数据和处理规则将您的应用程序数据映射到 Analytics 变量以供报告。

处理规则具备以下优势：

* 您无需向应用商店提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 对发送额外数据的影响甚微。

   这些值在使用处理规则映射后才会显示在报表中。

>[!TIP]
>
>Values that you were assigning directly to variables should now be added to the `data` NSDictionary.

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


### 移动配置文件

要移动配置文件，请执行以下操作：

1. 将为第一列中的变量设置的值移到第二列中的变量。
1. 从您的代码中删除旧配置变量。

### Migration information

下表列出了需要移到配置文件的配置变量。

#### 从版本 3.x 迁移

将第一列中的值移到第二列中的变量。

| 配置变量 | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| offlineTrackingEnabled | "offlineEnabled" |
| offlineHitLimit | "batchLimit" |
| reportSuiteIDs | "rsids" |
| trackingServer | "server" |
| charSet | "charset" |
| currencyCode | "currency" |
| ssl | "ssl" |
| linkTrackVars | 删除，不再使用。 |
| linkTrackEvents | 删除，不再使用。 |


#### 从版本 2.x 迁移

将第一列中的值移到第二列中的变量。

| 配置变量 | Variable in the `ADBMobileConfig.json` file |
|--- |--- |
| trackOffline | "offlineEnabled" |
| offlineLimit | "batchLimit" |
| account | "rsids" |
| trackingServer | "server", remove the `"https://"` prefix. 协议前缀将根据 "ssl" 设置自动添加。 |
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
| useBestPractices所有对流失测量 (getChurnInstance) 的调用 | Remove, replaced by lifecycle metrics. 有关更多信息，请参阅[生命周期量度](//help/ios/metrics.md)。 |


## Update track calls and tracking variables {#section_96E7D9B3CDAC444789503B7E7F139AB9}

SDK 版本 4 不使用以 Web 为主的 `track` 和 `trackLink` 调用，而是使用以下方法：

* `trackState:data:` states are the views that are available in your app, such as , , , and so on.`home dashboard``app settings``cart`

   这些状态与网站中的页面类似，而且 `trackState` 调用会使页面查看次数递增。

* `trackAction:data:` actions , such as , , , and other metrics that occur in your app and that you want to measure.`logons``banner taps``feed subscriptions`

用于这两种方法的 `data` 参数是 `NSDictionary`，其中包含作为上下文数据发送的名称值对。

### Events, props, eVars

在版本 4 中，您不能再在应用程序中直接分配变量，例如 event、eVar、prop、heir 和 list。SDK 现在会使用上下文数据和处理规则将您的应用程序数据映射到 Analytics 变量以供报告。

处理规则具备以下优势：

* 您无需向应用商店提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 对发送额外数据的影响甚微。

   这些值在使用处理规则映射后才会显示在报表中。有关更多信息，请参阅[处理规则和上下文数据](/help/ios/getting-started/proc-rules.md)。

您直接分配到变量的值应当添加到 `data``NSDictionary`   中。This means that calls to `setProp`, `setEvar`, and assignments to persistent context data should all be removed and the values be added to the `data` parameter.

### AppSection/Server、GeoZip、事务ID、Campaign和其他标准变量

您在测量对象（包括上面列出的变量）中设置的数据应当添加到 `data``NSDictionary`   中。随 `trackState` 或 `trackAction` 调用发送的唯一数据是 `data` 参数中的有效负荷。

### 替换跟踪调用

在您的代码中，将以下方法替换为对 `trackState` 或 `trackAction` 的调用：

#### 从版本 3.x 迁移

* `trackAppState (trackState)`
* `trackEvents (trackAction)`
* `track (trackAction)`
* `trackWithContextData (trackAction)`
* `trackLinkURL (trackAction)`

#### 从版本 2.x 迁移

* `track (trackState)`
* `trackLink (trackAction)`

## Custom visitor ID {#section_2CF930C13BA64F04959846E578B608F3}

Replace the `visitorID` variable with a call to `setUserIdentifier:`.

## Offline tracking {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

Offline tracking is enabled in the `ADBMobileConfig.json` file, and all other offline configuration is done automatically.

在您的代码中，删除对以下方法的调用：

### 版本 3.x

* `setOnline`
* `setOffline`

### 版本 2.x

* `forceOffline`
* `forceOnline`

## Products variable {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

由于产品变量在处理规则中不可用，因此可以使用以下语法设置 `products`：

```objective-c
//create a processing rule to set the corresponding product event. 
// for example, set prodView event when context data a.action = "product view" 
[ADBMobile trackAction:@"LikeButtonClicked"  
                  data:@{@"&&products" : @";Cool Shoe"}];
```

![](assets/prod-view.png)