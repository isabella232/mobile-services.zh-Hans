---
description: 此信息可帮助您从 3.x 或 2.x 版本的 iOS 库迁移至 4.x 版本的 iOS 库。
seo-description: 此信息可帮助您从 3.x 或 2.x 版本的 iOS 库迁移至 4.x 版本的 iOS 库。
seo-title: 迁移至 4.x iOS 库
solution: Experience Cloud,Analytics
title: 迁移至 4.x iOS 库
topic: Developer and implementation
uuid: 5668972b-f355-4e03-9df0-8c82ddf6809b
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '895'
ht-degree: 100%

---


# 迁移至 4.x iOS 库{#migrating-to-the-x-ios-library}

此信息可帮助您从 3.x 或 2.x 版本的 iOS 库迁移至 4.x 版本的 iOS 库。

>[!IMPORTANT]
>
>SDK 使用 `NSUserDefaults` 来存储计算独特用户数所需的数据、生命周期量度以及与 SDK 核心功能相关的其他数据。如果您修改或删除了 `NSUserDefaults` 中 SDK 所预期的值，则可能会出现意外行为，从而导致出现数据不一致的情况。

在 4.x 版本的 iOS SDK 库中，公共方法都整合到一个标头中。此外，功能现在可通过类级别方法访问，因此您无需跟踪指针、实例或单例。

## Event、Prop 和 eVar {#section_76EA6F5611184C5CAE6E62956D84D7B6}

在版本 4 中，您无法再在应用程序中直接分配变量，例如事件、eVar、prop、继承人和列表。反而，SDK 使用上下文数据和处理规则将应用程序数据映射到 Analytics 变量以便进行报告。

处理规则具有以下优势：

* 您无需向应用商店提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 对发送额外数据的影响很小。

   直到在使用处理规则映射后这些值才会显示在报表中。

>[!TIP]
>
>现在，应当将您直接分配到变量的值添加到 `data` NSDictionary 中。

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


### 移动配置文件

要移动配置文件，请执行以下操作：

1. 将为第一列中的变量设置的值移动到第二列中的变量。
1. 从代码中删除旧配置变量。

### 迁移信息

下表列出了需要移到配置文件的配置变量。

#### 从版本 3.x 迁移

将值从第一列移动到第二列中的变量。

| 配置变量 | `ADBMobileConfig.json` 文件中的变量 |
|--- |--- |
| offlineTrackingEnabled | &quot;offlineEnabled&quot; |
| offlineHitLimit | &quot;batchLimit&quot; |
| reportSuiteIDs | &quot;rsids&quot; |
| trackingServer | &quot;server&quot; |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | 删除，不再使用。 |
| linkTrackEvents | 删除，不再使用。 |


#### 从版本 2.x 迁移

将值从第一列移动到第二列中的变量。

| 配置变量 | `ADBMobileConfig.json` 文件中的变量 |
|--- |--- |
| trackOffline | &quot;offlineEnabled&quot; |
| offlineLimit | &quot;batchLimit&quot; |
| account | &quot;rsids&quot; |
| trackingServer | &quot;server&quot;，删除 `"https://"` 前缀。会根据 &quot;ssl&quot; 设置自动添加协议前缀。 |
| trackingServerSecure | 删除。 要实现安全连接，请定义 &quot;server&quot;，然后启用 &quot;ssl&quot;。 |
| charSet | &quot;charset&quot; |
| currencyCode | &quot;currency&quot; |
| ssl | &quot;ssl&quot; |
| linkTrackVars | 删除，不再使用。 |
| linkTrackEvents | 删除，不再使用。 |
| timestamp | 删除，不再可配置。 |
| dc | 删除，不再使用。 |
| userAgent | 删除，不再可配置。 |
| dynamicVariablePrefix | 删除，不再使用。 |
| visitorNamespace | 删除，不再使用。 |
| usePlugins | 删除，不再使用。 |
| useBestPractices 所有对流失测量 (getChurnInstance) 的调用 | 删除，替换为生命周期量度。有关更多信息，请参阅[生命周期量度](//help/ios/metrics.md)。 |


## 更新跟踪调用和跟踪变量 {#section_96E7D9B3CDAC444789503B7E7F139AB9}

SDK 版本 4 不使用以 Web 为主的 `track` 和 `trackLink` 调用，而是使用以下方法：

* `trackState:data:` 状态是您的应用程序中可用的一些视图，例如 `home dashboard`、`app settings`、`cart` 等等。

   这些状态与网站中的页面类似，而且 `trackState` 调用会使页面查看次数递增。

* `trackAction:data:` 操作，跟踪您的应用程序中发生的要测量的操作，例如 `logons`、`banner taps`、`feed subscriptions` 和其他量度。

用于这两种方法的 `data` 参数是 `NSDictionary`，其中包含作为上下文数据发送的名称值对。

### Event、Prop、eVar

在版本 4 中，您无法再在应用程序中直接分配变量，例如事件、eVar、prop、继承人和列表。现在，SDK 使用上下文数据和处理规则将应用程序数据映射到 Analytics 变量以便进行报告。

处理规则具有以下优势：

* 您无需向应用商店提交更新即可更改数据映射。
* 您可以对数据使用有意义的名称，而不是设置特定于报表包的变量。
* 对发送额外数据的影响很小。

   直到在使用处理规则映射后这些值才会显示在报表中。有关更多信息，请参阅[处理规则和上下文数据](/help/ios/getting-started/proc-rules.md)。

您直接分配到变量的值应当添加到 `data` `NSDictionary` 中。这意味着应全部删除对 `setProp`、`setEvar` 的调用和对永久性上下文数据的分配，并将值添加到 `data` 参数中。

### AppSection/服务器、GeoZip、交易 ID、促销活动和其他标准变量

您在测量对象（包括上面列出的变量）中设置的数据应当添加到 `data` `NSDictionary` 中。随 `trackState` 或 `trackAction` 调用发送的唯一数据是 `data` 参数中的有效负荷。

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

## 自定义访客 ID {#section_2CF930C13BA64F04959846E578B608F3}

将 `visitorID` 变量替换为对 `setUserIdentifier:` 的调用。

## 离线跟踪 {#section_5D4CD8CD1BE041A79A8657E31C0D24C6}

离线跟踪在 `ADBMobileConfig.json` 文件中已启用，并且所有其他离线配置均已自动完成。

在您的代码中，删除对以下方法的调用：

### 版本 3.x

* `setOnline`
* `setOffline`

### 版本 2.x

* `forceOffline`
* `forceOnline`

## 产品变量 {#section_AFBA36F3718C44D29AF81B9E1056A1B4}

由于产品变量在处理规则中不可用，因此可以使用以下语法设置 `products`：

```objective-c
//create a processing rule to set the corresponding product event. 
// for example, set prodView event when context data a.action = "product view" 
[ADBMobile trackAction:@"LikeButtonClicked"  
                  data:@{@"&&products" : @";Cool Shoe"}];
```

![](assets/prod-view.png)