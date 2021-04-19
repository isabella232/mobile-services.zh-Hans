---
description: 帮助您使用ADBMobile JSON配置文件的信息。
seo-description: 帮助您使用ADBMobile JSON配置文件的信息。
seo-title: ADBMobileConfig.json 配置
solution: Experience Cloud,Analytics
title: ADBMobileConfig.json 配置
topic-fix: Developer and implementation
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
exl-id: 57d50d30-651c-4943-835e-1cbce7467baf
translation-type: tm+mt
source-git-commit: 4c2a255b343128d2904530279751767e7f99a10a
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 44%

---

# ADBMobileConfig.json配置文件{#adbmobileconfig-json-config}

帮助您使用ADBMobile JSON配置文件的信息。

SDK目前支持多个Adobe Experience Cloud解决方案，包括分析、目标和Audience Manager。 方法将根据解决方案来添加前缀。配置方法的前缀为“配置”。

* **rsids**

   （**Analytics**&#x200B;要求）一个或多个用于接收Analytics数据的报表包。 多个报表包 ID 应以逗号分隔，且中间不应有空格。

   * 以下是此方法的语法：

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Analytics和受众管理所需的**)。 基于父节点的分析或受众管理服务器。 应当使用不含 `"https://"` 或 `"https://"` 协议前缀的服务器域填充此变量。协议前缀由库根据`ssl`变量自动处理。

   如果 `ssl` 为 `true`，则对此服务器进行安全连接。如果 `ssl` 为 `false`，则对此服务器进行非安全连接。

* **charset**

   定义您用于发送到Analytics的数据的字符集。 charset 用于将传入的数据转换为 UTF-8 以便进行存储和报告。有关更多信息，请参阅 [s.charSet](https://docs.adobe.com/content/help/zh-Hans/analytics/implementation/vars/config-vars/charset.html)。

* **ssl**

   启用(`true`)或禁用(`false`)通过SSL发送测量数据(`HTTPS`)。 默认值为 `false`。

* **offlineEnabled**

   启用(`true`)后，点击将在设备脱机时排队，并在设备联机时稍后发送。 报表包必须启用时间戳才能使用离线跟踪。

   如果报表包上启用了时间戳，则`offlineEnabled`配置属性&#x200B;*必须*&#x200B;为`true`。 如果报表包未启用时间戳，则 `offlineEnabled` 配置属性&#x200B;*必须*&#x200B;为 `false`.

   如果未正确配置，数据将丢失。如果您不确定报表包是否已启用时间戳，请与客户服务部门联系。 如果您当前正在将AppMeasurement数据报告到同时从JavaScript收集数据的报表包，则可能需要为移动数据设置单独的报表包，或使用`s.timestamp`变量对所有JavaScript点击加入自定义时间戳。

   默认值为 `false`。

* **lifecycleTimeout**

   指定从应用程序启动到将该启动视为新会话之前必须经过的时长（以秒为单位）。此超时也适用于应用程序被发送到后台后又重新启用的情况。应用程序在后台所用的时间不包括在会话时长中。

   默认值为300秒。

* **batchLimit**

   批量发送点击量。

   例如，如果设置为`50`，则点击将排队，直到存储50次，然后发送所有排队的点击。 需要`offlineEnabled=true`，默认值为`0`（无批处理）。

* **privacyDefault**

   选项有：

   * `optedin` - 立即发送点击。
   * `optedout` - 丢弃点击。
   * `optunknown`  — 如果您的报表包启用了时间戳，则会保存点击，直到隐私状态更改为选择加入（然后发送点击）或选择退出（然后丢弃点击）为止。如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

      这仅设置默认值。 如果曾在代码中设置或更改过此值，则由代码设置的值将保存在本地存储中，并一直使用，直到它发生更改，或者卸载并重新安装应用程序。

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

   (**目标**&#x200B;要求)您分配的客户端代码。

* **timeout**

   确定目标等待响应的时间。

以下是`ADBMobileConfig.json`文件的示例：

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
