---
description: 帮助您使用ADBMobile JSON配置文件的信息。
seo-description: 帮助您使用ADBMobile JSON配置文件的信息。
seo-title: ADBMobileConfig.json配置
solution: Experience Cloud,Analytics
title: ADBMobileConfig.json配置
topic: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 40%

---


# ADBMobileConfig.json config file {#adbmobileconfig-json-config}

帮助您使用ADBMobile JSON配置文件的信息。

SDK目前支持多个Adobe Experience Cloud解决方案，包括分析、目标和Audience Manager。 方法将根据解决方案来添加前缀。配置方法前缀为“配置”。

* **rsids**

   (**Analytics要求**)一个或多个报表包，用于接收Analytics数据。 多个报表包 ID 应以逗号分隔，且中间不应有空格。

   * 以下是此方法的语法：

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**分析和受众管理需要**)。 基于父节点的分析或受众管理服务器。 应当使用不含 `"https://"` 或 `"https://"` 协议前缀的服务器域填充此变量。协议前缀由库根据变量自动处 `ssl` 理。

   如果 `ssl` 为 `true`，则对此服务器进行安全连接。如果 `ssl` 为 `false`，则对此服务器进行非安全连接。

* **charset**

   定义您用于发送到Analytics的数据的字符集。 charset 用于将传入的数据转换为 UTF-8 以便进行存储和报告。有关更多信息，请参阅 [s.charSet](https://docs.adobe.com/content/help/zh-Hans/analytics/implementation/vars/config-vars/charset.html)。

* **ssl**

   启用(`true`)或禁用(`false`)通过SSL()发送测量`HTTPS`数据。 默认值为 `false`。

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. 报表包必须启用时间戳才能使用离线跟踪。

   If time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. 如果报表包未启用时间戳，则 `offlineEnabled` 配置属性&#x200B;*必须*&#x200B;为 `false`.

   如果未正确配置，数据将丢失。如果不确定报表包是否启用时间戳，请与客户关怀联系。 If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   默认值为 `false`。

* **lifecycleTimeout**

   指定在启动被视为新会话之前，应用程序启动之间必须经历的时长（以秒为单位）。 此超时也适用于应用程序被发送到后台后又重新启用的情况。应用程序在后台所用的时间不包括在会话时长中。

   默认值为300秒。

* **batchLimit**

   批量发送点击量。

   例如，如果设置为， `50`则在存储50个点击之前对点击进行排队，然后发送所有排队的点击。 需 `offlineEnabled=true`要，默认值为( `0` 无批处理)。

* **privacyDefault**

   选项有：

   * `optedin` - 立即发送点击。
   * `optedout` - 丢弃点击。
   * `optunknown` -如果报表包启用时间戳，则会保存点击，直到隐私状态更改为选择加入（然后发送点击）或选择退出（然后丢弃点击）。 如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

      这仅设置默认值。 如果在代码中设置或更改了此值，则由代码设置的值将保存在本地存储中，并一直使用，直到它更改，或卸载并重新安装应用程序。

      默认值为 `optedin`。

* **poi**

   每个 POI 数组均保存目标点区域的 POI 名称、纬度、经度和半径（以米为单位）。POI 名称可以是任何字符串。在发送 `trackLocation` 调用时，如果当前坐标位于定义的 POI 内，则会填充上下文数据变量，并随 `trackLocation` 调用发送该变量。

   * 以下是此变量的代码示例：

      ```js
       "poi" [ 
                ["san francisco",37.757144,-122.44812,7000], 
                ["santa cruz",36.972935,-122.01725,600] 
             ]
      ```

* **clientCode**

   (**目标要求**)您分配的客户代码。

* **timeout**

   确定目标等待响应的时间。

The following is an example of an `ADBMobileConfig.json` file:

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
  "timeout" : 1
 },
 "audienceManager" : {
  "server" : "myServer.demdex.com"
 }
}
```
