---
description: 此信息可帮助您使用 ADBMobile.json 配置文件。
seo-description: 此信息可帮助您使用 ADBMobile.json 配置文件。
seo-title: ADBMobile JSON 配置
solution: Marketing Cloud,Analytics
title: ADBMobile JSON 配置
topic: 开发人员和实施
uuid: 1decf605-7bc3-4e73-ad52-1ecd5821599e
translation-type: tm+mt
source-git-commit: 19264af3f4a675add6f61c27f4cdaf20033b9bb7

---


# ADBMobile JSON config file {#adbmobile-json-config}

此信息可帮助您了解ADBMobile.json配置文件中的变量。

## `ADBMobileConfig.json` 配置文件引用 {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

同一配置文件可用于多个平台上的应用程序：

>[!TIP]
>
>In **Android**, the `ADBMobileConfig.json` file must be placed in the `assets` folder.

以下是JSON文件中的变量列表以及每个变量所需的最低SDK版本：

* **acquisition**
   * 最低 SDK 版本：4.1
   * 启用移动设备应用程序客户获取。
      * `server`，首次启动时在其中检查客户获取反向链接的客户获取服务器。
      * `appid`，客户获取服务器上生成的唯一标识此应用程序的 ID。
   如果缺少此部分，请启用移动设备应用程序客户获取并再次下载 SDK 配置文件。有关详细信息，请参 *阅此变量列表* 中的referrerTimeout。

* **analyticsForwardingEnabled**
   * SDK的最低版本为4.8.0。
   * 默认值为 `false`.

      `audienceManager` 对象中的属性。如果配置了 Audience Manager，并且将 `analyticsForwardingEnabled` 设置为 `true`，则所有 Analytics 流量也将转发至 Audience Manager。

* **backdateSessionInfo**
   * 最低 SDK 版本：4.6.
   * 启用/禁用 Adobe SDK 回溯会话信息点击量的功能。

      会话信息点击量当前包含崩溃次数和会话时长，可以启用或者禁用该功能。

      **启用或禁用点击量**

      * 如果将该值设置为 `false`，则&#x200B;**禁用**&#x200B;点击量。SDK 会返回其 4.1 版本之前的行为，即同时包含上一个会话的会话信息和后续会话的第一次点击信息。Adobe SDK 还会将会话信息附加到当前生命周期，这可避免创建过多的访问。因为不再创建过多的访问，访问计数会立即减少。

      * 如果不提供值，则默认值为 `true`，并&#x200B;**启用**&#x200B;点击量。启用点击量后，Adobe SDK 会将会话信息点击回溯到上一个会话最终点击后 1 秒钟。这意味着崩溃和会话数据将与它们所发生的正确日期相关联。一个不利影响是，SDK 可能会为回溯的点击创建一次访问。每次新启动应用程序时都会有一个回溯的点击。

         >[!IMPORTANT]
         >
         >在会话信息服务器调用中发送回溯的会话点击信息，并且可能会应用其他服务器调用。

* **batchLimit**
   * 最低 SDK 版本：4.1
   * 在连续调用中发送的点击量的阈值。

      例如，如果将 `batchLimit` 设置为 10，则第 10 次点击之前的每次点击都将存储在队列中。当第 10 次点击进入时，将连续发送所有 10 次点击。

      请牢记以下信息：

      * 默认值为 `0`，这表示不启用批量处理。
      * 需要 `offlineEnabled = true`。

* **charset**
   * 最低 SDK 版本：4.0
   * 定义将用于发送到 Analytics 的数据的字符集。

      charset 用于将传入的数据转换为 UTF-8 以便进行存储和报告。

* **clientCode**
   * 最低 SDK 版本：4.0
   * 分配给您的客户端代码。

      >[!IMPORTANT]
      >
      >Target需要此变量。

* **coopUnsafe**
   * 最低 SDK 版本：4.16.1
   * The Boolean property of the `marketingCloud` object that, when set to `true`, causes the device to be opted-out of the Experience Cloud's Device Co-Op.
   * 默认值为 `false`.
   * 这项设置&#x200B;**仅**&#x200B;适用于已配置设备协作的客户。
   对于要求将该值设置为 `true` 的设备协作成员，您需要与相应的协作团队合作，以申请关于您的设备协作帐户上的黑名单标记。不存在启用这些标记的自助途径。

   请牢记以下信息：

   * When `coopUnsafe` is set to `true`, `coop_unsafe=1` will always be appended to Audience Manager and Visitor ID hits.
   * If you enable Analytics server-side forwarding to Audience Manager, you will also see `coop_unsafe=1` Analytics hits.


* **environmentId**
   * 最低 SDK 版本：4.14
   * 您需要使用的环境的 ID。

      您可以指定有效的 ID (`environmentId=8`)，如果没有指定 `environmentId`，则会使用默认的生产环境。

* **lifecycleTimeout**
   * 最低 SDK 版本：4.0
   * 默认值为 300 秒。

      指定应用程序启动（但在启动被视为新会话之前）必须间隔的时长（以秒为单位）。此超时也包括应用程序被发送到后台运行到重新启动应用程序的时间。

      会话时间长度不包括应用程序在后台中运行的时间。

* **messages**

   * 最低 SDK 版本：4.2
   * 由 Adobe Mobile Services 自动生成，定义应用程序内消息传送的设置。有关更多信息，请参阅下面的&#x200B;*消息描述*&#x200B;部分。

* **offlineEnabled**

   * 最低 SDK 版本：4.0
   * 启用后，点击将在设备处于离线状态时排入队列，之后当设备处于在线状态时再进行发送。

      报表包必须启用时间戳才能使用离线跟踪。

      默认值为 `false`.

      >[!IMPORTANT]
      >
      >如果报表包已启用时间戳，那么您的 `offlineEnabled` 配置属性&#x200B;**必须**&#x200B;为 true。如果您的报表包未启用时间戳，则 `offlineEnabled` 配置属性&#x200B;**必须**&#x200B;为 false。
      >
      >如果配置不正确，数据将会丢失。如果您不确定报表包是否已启用时间戳，请联系客户关怀团队或从 Adobe Mobile Services 下载配置文件。

      如果您当前向某个报表包报告 AppMeasurement 数据，而该报表包也从 JavaScript 收集数据，则您可能需要为移动数据设置一个单独的报表包，或在使用 `s.timestamp` 变量的所有 JavaScript 点击中包含自定义时间戳。

* **org**

   * 最低 SDK 版本：4.3
   * 指定 ID 服务的 Experience Cloud 组织 ID。

* **poi**
   * 最低 SDK 版本：4.0
   * 每个目标点 (POI) 数组均保存目标点区域的 POI 名称、纬度、经度和半径（以米为单位）。

      POI 名称可以是任何字符串。在发送 `trackLocation` 调用时，如果当前坐标位于定义的 POI 内，则会填充上下文数据变量，并随 `trackLocation` 调用发送该变量。

      ```javascript
      "poi": [
                 ["san francisco",37.757144,-122.44812,7000]
                 ["santa cruz",36.972935,-122.01725,600]
             ]
      ```

      从版本 4.2 开始，POI 可在 Adobe Mobile 界面中定义并动态同步到应用程序配置文件。此同步需要 `analytics.poi` 设置：

      ```javascript
      “analytics.poi“: `https://assets.adobedtm.com/`
      …/yourfile.json”`,
      ```

      如果未配置此设置，必须更新 `ADBMobile.json` 文件以包含此行。要下载更新的配置文件，请参 [阅启动前](/help/android/getting-started/requirements.md)。

* **postback**
   * 最低 SDK 版本：4.6
   * 以下是有关“回调”消息模板的定义：

      ```javascript
      "payload":{
        "templateurl":"", //required will be token-expanded prior to being sent
        "templatebody":"", //optional - if this length > 0 POST will be used as transport method. This is a base64 encoded blob, which will be decoded and token-expanded prior to being sent.
        "contenttype": "", // optional - if this is length > 0 and POST type is selected this will be set as the Content-Type header.  if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
        "timeout": 0 // optional - number of seconds to wait before timing out.  Default is 2.}
      ```

      The `payload` object in the code is a sample payload for a message definition that goes in the `ADBMobileConfig.json` file. For more information, see [Postbacks](/help/android/analytics-main/postbacks/postbacks.md).

* **privacyDefault**
   * 最低 SDK 版本：4.0
   * 默认值为 `optedin`.
      * 如果为 `optedin`，将会立即发送点击。
      * 如果为 `optedout`，将会丢弃点击。
      * 如果为 `optunknown`，当您的报表包启用了时间戳时，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。
      If your report suite is not timestamp-enabled, hits are discarded until the privacy status changes to `optedin`.  这仅设置初始值。如果在代码中设置或更改了此值，则会使用新值，直到再次进行更改或者卸载并重新安装应用程序为止。


* **referrerTimeout**
   * 最低 SDK 版本：4.1
   * SDK 在首次启动时等待客户获取反向链接数据多少秒才被视为超时。如果您使用客户获取，我们建议采用 5 秒超时。

      >[!IMPORTANT]
      >
      >客户获取需要此变量。 如果将该变量设置为 `0` 或未包含该变量，SDK 将不会等待客户获取数据，而且也不会跟踪客户获取量度。

* **remotes**
   * 最低 SDK 版本：4.2
   * 自动配置并定义动态配置文件的 Adobe 托管端点。

      每次启动时会针对当前版本检查每个配置文件的最近更新时间，并且会下载并保存所做的更新。
      * `analytics.poi` 是托管的 POI 配置的端点。
      * `messages` 是托管的应用程序内消息配置的端点。

* **rsids**
   * 最低 SDK 版本：4.0
   * 一个或多个用于接收 Analytics 数据的报表包。多个报表包 ID 应当以逗号分隔，且彼此之间没有空格。

      ```javascript
        "rsids" "rsid"
      ```

      ```javascript
        "rsids" "rsid1,rsid2"
      ```

      >[!IMPORTANT]
      >
      >This variable is required by Analytics.

* **server**
   * 最低 SDK 版本：4.0
   * 基于父节点的 Analytics 或受众管理服务器。This variable should be populated with the server domain, without an `https://` or `https://` protocol prefix. 此前缀基于 `ssl` 变量，将由库自动处理。如果 `ssl` 为 `true`，则对此服务器进行安全连接。如果 `ssl` 为 `false`，则对此服务器进行非安全连接。

* **ssl**
   * 最低 SDK 版本：4.0
   * 默认值为 `false`.

      启用 (`true`) 或禁用 (`false`) 使用 SSL (HTTPS) 发送测量数据的功能。

      “回调”消息模板的定义如下所示：

      ```javascript
      "payload": {
          "templateurl":"",//required-will be token-expanded prior to being sent 
          "templatebody": "", //optional - if this length >  0 POST will be used& as transport method. This is a base64 encoded blob, which will be  decoded and token-expanded prior to being sent.
          "contenttype": "" // optional - if this is length > 0 POST type is selected this will be set as the Content-Type header. if this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded"
          "timeout": 0 // optional - number of seconds to wait before timing& out. Default is 2.}
      ```

* **timeout**
   * 最低 SDK 版本：4.0
   * 确定 Target 等待响应的时间。


## Sample `ADBMobileConfig.json` file {#section_4655EF79744649E5A5AE19E3224C472C}

以下是一个 `ADBMobileConfig.json` 示例文件：

```js
 { 
    "version": "2014-08-05T19:18:28.169Z", 
    "marketingCloud" : { 
        "org": "016D5C175213CCA80A490D05@AdobeOrg", 
        "coopUnsafe": false 
    }, 
    "target": { 
        "clientCode": "", 
        "timeout": 5, 
        "environmentId": 8 
    }, 
    "audienceManager": { 
        "server": "", 
        "analyticsForwardingEnabled": false 
    }, 
    "acquisition": { 
        "server": "c00.adobe.com", 
        "appid": "10a77a60192fbb628376e1b1daeeb65debf934e2c807e067ceb2963a41b165ee" 
    }, 
    "analytics": { 
        "rsids": "coolApp", 
        "server": "my.CoolApp.com", 
        "ssl": true, 
        "offlineEnabled": true, 
        "charset": "UTF-8", 
        "lifecycleTimeout": 300, 
        "privacyDefault": "optedin", 
        "batchLimit": 0, 
        "referrerTimeout": 5, 
        "poi": [ 
            ["san francisco",37.757144,-122.44812,7000],  
            ["santa cruz",36.972935,-122.01725,600] 
        ] 
    }, 
    "messages": [ 
        { 
            "messageId": "cb426565-a563-497a-a889-9dbeb451f8ae", 
            "template": "fullscreen", 
            "payload": { 
                 "html": "<!DOCTYPE html><html><head><meta charset=\"utf-8\" /><title></title><style></style></head><body><iframe src=\"https://www.adobe.com/\" frameborder=\"0\"></iframe></body></html>" 
            }, 
            "showOffline": false, 
            "showRule": "always", 
            "endDate": 2524730400, 
            "startDate": 0, 
            "audiences": [], 
            "triggers": [ 
                { 
                    "key": "pev2", 
                    "matches": "eq", 
                    "values": [ 
                        "AMACTION:custom" 
                    ] 
                } 
            ] 
        } 
    ], 
    "remotes": { 
        "analytics.poi": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0faadc2f9ed92bc00003b.json", 
        "messages": "https://assets.adobedtm.com/staging/42a6fc9b77cd9f29082cf19b787bae75b7d1f9ca/scripts/satellite-53e0f9e2c2f9ed92bc000032.json" 
    } 
}
```

## 消息描述 {#section_B97D654BA92149CE91F525268D7AD71F}

消息节点由 Adobe Mobile Services 自动生成，通常不需要手动更改。下面提供的描述仅供疑难解答之用：

* "messageId"
* 生成的 ID，必需
* "template"
   * "alert"、"fullscreen" 或 "local"
   * 必需

* "showOffline"
   * true 或 false
   * 默认为 false

* "showRule"
   * "always"、"once" 或 "untilClick"
   * 必需

* "endDate"
   * 自 1970 年 1 月 1 日以来的秒数
   * 默认为 2524730400

* "startDate"
   * 自 1970 年 1 月 1 日以来的秒数
   * 默认为 0

* "payload"
   * "html"
      * 仅全屏模板，必需
      * 定义消息的 html
   * "image"
      * 仅全屏，可选
      * 用于全屏图像的图像 url
   * "altImage"
      * 仅全屏，可选
      * 当
         * image
         * 中指定的 url 不可访问时要使用的捆绑图像的名称
   * "title"
      * 全屏和警报，必需
      * 全屏或警报消息的标题文本
   * "content"
      * 警报和本地通知，必需
      * 警报消息的子文本，或本地通知消息的通知文本
   * "confirm"
      * 警报，可选
      * 确认按钮中使用的文本
   * "cancel"
      * 警报，必需
      * 取消按钮中使用的文本
   * "url"
      * 警报，可选
      * 单击确认按钮时要加载的 url 操作
   * "wait"
      * 本地通知，必需
      * 等待符合条件后发布本地通知的时间（以秒为单位）



* "audiences"
   * 定义消息应如何显示的对象数组
   * "key"
      * 要在点击中查找的变量名称，必需
* "matches"
   * 进行比较时使用的匹配符类型
   * eq = 等于
   * ne = 不等于
   * co = 包含
   * nc = 不包含
   * sw = 开始于
   * ew = 结束于
   * ex = 存在
   * nx = 不存在
   * lt = 小于
   * le = 小于或等于
   * gt = 大于
   * ge = 大于或等于
* "values"
   * 一个值数组，用于匹配在
      * key
      * 中命名的变量值，匹配符类型位于
      * matches
* "triggers"
   * 与 audiences 相同，但这是操作而不是受众
   * "key"
   * "matches"
   * "values"
