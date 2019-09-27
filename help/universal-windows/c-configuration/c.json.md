---
description: 此信息可帮助您使用 ADBMobile JSON 配置文件。
seo-description: 此信息可帮助您使用 ADBMobile JSON 配置文件。
seo-title: ADBMobileConfig.json配置
solution: Marketing Cloud,Analytics
title: ADBMobileConfig.json配置
topic: 开发人员和实施
uuid: cbcb54a3-4b8f-4651-8ce9-2731ac988545
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# ADBMobileConfig.json配置文件 {#adbmobileconfig-json-config}

此信息可帮助您使用 ADBMobile JSON 配置文件。

SDK 当前支持多种 Adobe Experience Cloud 解决方案，其中包括 Analytics、Target 和 Audience Manager。方法将根据解决方案来添加前缀。配置方法具有“Config”前缀。

* **rsids**

   (**Required by Analytics**) One or more report suites to receive Analytics data. 多个报表包 ID 应当以逗号分隔，且彼此之间没有空格。

   * 下面是这种方法对应的语法：

      ```js
      "rsids" : "rsid"
      ```

      ```js
      "rsids" : "rsid1,rsid2"
      ```

* **server**

   (**Required by Analytics and Audience Management**). 基于父节点的 Analytics 或受众管理服务器。This variable should be populated with the server domain, without an `"https://"` or `"https://"` protocol prefix. 协议前缀将由库根据 `ssl` 变量自动处理。

   如果 `ssl` 为 `true`，则对此服务器进行安全连接。如果 `ssl` 为 `false`，则对此服务器进行非安全连接。

* **charset**

   定义将用于发送到 Analytics 的数据的字符集。charset 用于将传入的数据转换为 UTF-8 以便进行存储和报告。For more information, see [s.charSet](https://marketing.adobe.com/resources/help/en_US/sc/implement/charset.html).

* **ssl**

   Enables (`true`) or disables (`false`) sending measurement data via SSL (`HTTPS`). 默认值为 `false`.

* **offlineEnabled**

   When enabled (`true`), hits are queued while the device is offline and sent later when the device is online. 报表包必须启用时间戳才能使用离线跟踪。

   If time stamps are enabled on your report suite, your `offlineEnabled` configuration property *must* be `true`. 如果您的报表包未启用时间戳，则 `offlineEnabled` 配置属性&#x200B;*必须*&#x200B;为 `false`.

   如果配置不正确，数据将会丢失。如果不确定报表包是否启用了时间戳，请与客户关怀联系。 If you are currently reporting AppMeasurement data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data or include a custom timestamp on all JavaScript hits using the `s.timestamp` variable.

   默认值为 `false`.

* **lifecycleTimeout**

   指定应用程序在后一次启动时，必须与前一次启动间隔多长时间，才能被视为新会话（以秒为单位）。此超时也适用于应用程序被发送到后台后又重新启用的情况。会话时间长度不包括应用程序在后台中运行的时间。

   默认值为 300 秒。

* **batchLimit**

   批量发送点击。

   For example, if set to `50`, hits are queued until 50 are stored, then all queued hits are sent. 需 `offlineEnabled=true`要，默认值 `0` 为（无批处理）。

* **privacyDefault**

   选项包括：

   * `optedin` -立即发送点击。
   * `optedout` - hits are discarded.
   * `optunknown` - 如果您的报表包启用了时间戳，将会保存点击，直到隐私状态更改为选择启用（随后将发送点击）或选择禁用（随后将丢弃点击）。如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

      这仅设置默认值。 如果曾在代码中设置或更改此值，则由代码设置的值会保存在本地存储中，并一直使用到它发生更改，或应用程序被卸载后又重新安装时为止。

      默认值为 `optedin`.

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

   (**Required by Target**) Your assigned client code.

* **timeout**

   确定 Target 等待响应的时长。

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
