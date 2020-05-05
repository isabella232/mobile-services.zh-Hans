---
description: 此信息可帮助您使用ADBMobile.json配置文件。
seo-description: 此信息可帮助您使用ADBMobile.json配置文件。
seo-title: ADBMobile JSON 配置
solution: Marketing Cloud,Analytics
title: ADBMobile JSON 配置
topic: Developer and implementation
uuid: d9708d59-e30a-4f6c-ab1b-d9499855d0c2
translation-type: tm+mt
source-git-commit: 82b3dc38a0325b3aa733b491ddad9b59dbe84eaa

---


# ADBMobile JSON 配置 {#adbmobile-json-config}

此信息可帮助您使用 `ADBMobile.json` 配置文件。

## ADBMobileConfig.json 配置文件引用 {#section_5AD4EDF87E304980B4AC4A5657FDA8B9}

同一配置文件可用于多个平台上的应用程序：

>[!TIP]
>
>在 **iOS** 中，可将 `ADBMobileConfig.json` 文件置于包内的任何可访问位置。

* **acquisition**

   启用移动设备应用程序客户获取。

   如果缺少此部分，请启用移动设备应用程序客户获取并再次下载 SDK 配置文件。For more information, see *referrerTimeout* below.

   * `server` - 首次启动时在其中检查客户获取反向链接的客户获取服务器。
   * `appid` - 客户获取服务器上生成的唯一标识此应用程序的 ID。
   * 最低 SDK 版本：4.1

* **analyticsForwardingEnabled**

   `audienceManager` 对象中的属性。如果配置了 `Audience Manager`，并且将 `analyticsForwardingEnabled` 设置为 `true`，则所有 Analytics 流量也将转发至 Audience Manager。默认值为 `false`。

   * 最低 SDK 版本：4.8.0

* **backdateSessionInfo**

   启用/禁用 Adobe SDK 回溯会话信息点击量的功能。

   会话信息点击当前由崩溃和会话长度组成，可以启用或禁用。

   * 如果将该值设置为 `false`，则&#x200B;**禁用**&#x200B;点击量。

      SDK返回其4.1之前的行为，将上一会话的会话信息与后续会话的第一次点击相混合。 Adobe SDK还将会话信息附加到当前生命周期中，这可避免创建夸大访问。 由于不再产生夸大的访问，访问计数会立即下降。

   * 如果不提供值，则默认值为 `true`，并&#x200B;**启用**&#x200B;点击量。

      启用点击后，Adobe SDK会将会话信息点击回溯到上一会话中最后一次点击后的1秒。 这意味着崩溃数据和会话数据将与它们发生的正确日期相关。 一个副作用是SDK可能创建对追溯点击的访问。 每次新启动应用程序时都会有一个回溯的点击。

   * 最低 SDK 版本：4.6
   >[!IMPORTANT]
   >
   >回溯的会话点击信息是在会话信息服务器调用中发送的，其他服务器调用也可能适用。


* **batchLimit**

   在连续调用中发送的点击量的阈值。例如，如果将 `batchLimit` 设置为 10，则第 10 次点击之前的每次点击都将存储在队列中。当第 10 次点击进入时，将连续发送所有 10 次点击。

   * 默认值为 `0`，这表示不启用批量处理。
   * 需要 `offlineEnabled = true`。
   * 最低 SDK 版本：4.1

* **charset**

   定义将用于发送到 Analytics 的数据的字符集。charset 用于将传入的数据转换为 UTF-8 以便进行存储和报告。有关更多信息，请参阅 [s.charSet](https://docs.adobe.com/content/help/en/analytics/implementation/vars/config-vars/charset.html)。

   * 最低 SDK 版本：4.0

* **clientCode**

   分配给您的客户端代码。

   >[!IMPORTANT]
   >
   >这是 Target 的必需变量。

   * 最低 SDK 版本：4.0

* **coopUnsafe**

   对于要求将该值设置为 `true` 的设备协作成员，您需要与相应的协作团队合作，以申请关于您的设备协作帐户上的黑名单标记。不存在启用这些标记的自助途径。

   请牢记以下信息：

   * 如果将 `coopUnsafe` 设置为 `true`，则会始终将 `coop_unsafe=1` 附加到 Audience Manager 和访客 ID 点击中。
   * 如果启用到 Audience Manager 的 Analytics 服务器端转发，则还将会在 Analytics 点击中看到 `coop_unsafe=1`。
   以下是一些附加信息：

   * 最低 SDK 版本：4.16.1
   * `marketingCloud` 对象的布尔属性，将该属性设置为 `true` 后，会导致设备退出 Experience Cloud 设备协作。
   * 默认值为 `false`。
   * 这项设置&#x200B;**仅**&#x200B;适用于已配置设备协作的客户。



* **environmentId**

   您需要使用的环境的 ID。您可以指定有效的 ID (`environmentId=8`)，如果没有指定 `environmentId`，则会使用默认的生产环境。

   * 最低 SDK 版本：4.14

* **lifecycleTimeout**

   默认值为300秒。

   指定在应用程序启动之间、但在启动被视为新会话之前必须经历的时长（以秒为单位）。 此超时也适用于应用程序被发送到后台后又重新启用的情况。应用程序在后台所花费的时间不包括在会话长度中。

   * 最低 SDK 版本：4.0

* **messages**

   由Adobe Mobile Services自动生成，定义应用程序内消息传递的设置。 有关详细信息，请参阅下 *面的消息* 说明部分。

   * 最低 SDK 版本：4.2

* **offlineEnabled**

   启用后，点击将在设备处于离线状态时排入队列，之后当设备处于在线状态时再进行发送。报表包必须启用时间戳才能使用离线跟踪。默认值为 `false`。

   以下是一些重要信息：

   * 如果报表包已启用时间戳，则 `offlineEnabled` 配置属性&#x200B;*必须*&#x200B;为 true。
   * 如果报表包未启用时间戳，则 `offlineEnabled` 配置属性&#x200B;*必须*&#x200B;为 false。

      如果未正确配置，则数据将丢失。 如果您不确定报表包是否启用时间戳，请与客户服务联系或从Adobe Mobile Services下载配置文件。 如果您当前向某个报表包报告 AppMeasurement 数据，而该报表包也从 JavaScript 收集数据，则您可能需要为移动数据设置一个单独的报表包，或在使用 `s.timestamp` 变量的所有 JavaScript 点击中包含自定义时间戳。

   * 最低 SDK 版本：4.0

* **org**

   指定 Adobe Experience Platform Identity Service 的 Experience Cloud 组织 ID。

   * 最低 SDK 版本：4.3

* **poi**

   每个 POI 数组均保存目标点区域的 POI 名称、纬度、经度和半径（以米为单位）。POI 名称可以是任何字符串。在发送 `trackLocation` 调用时，如果当前坐标位于定义的 POI 内，则会填充上下文数据变量，并随 `trackLocation` 调用发送该变量。

   * 最低 SDK 版本：4.0

   ```js
   "poi" [ 
           ["sanfrancisco",37.757144,-122.44812,7000]
           ["santacruz",36.972935,-122.01725,600]
         ] 
   ```

   >[!TIP]
   >
   >从版本 4.2 开始，POI 可在 Adobe Mobile 界面中定义并动态同步到应用程序配置文件。此同步需要 `analytics.poi` 设置：

   ```js
   “analytics.poi”: “`https://assets.adobedtm.com/…/yourfile.json`”,
   ```

   如果未配置此设置，必须更新 `ADBMobile.json` 文件以包含此行。要下载更新的配置文件，请参阅[开始之前](/help/ios/getting-started/requirements.md)。

* **postback**

   “回调”消息模板的定义如下所示：

   ```js
   "payload":{
       "templateurl":"",//required- will be token-expanded prior to being sent
       "templatebody":"", //optional-if this length > 0 POST will be used as transport method. This is a base-64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"", //optional-if this is length > 0 and POST type is selected, this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout": 0 //optional-number of seconds to wait before timingout.Defaultis2.}
   ```

   代码中的 `payload` 对象是用于消息定义的有效负荷示例，将会进入 `ADBMobileConfig.json` 文件中。有关更多信息，请参阅[回发](/help/ios/analytics-main/postback/postback.md)。

   * 最低 SDK 版本：4.6

* **privacyDefault**

   * 如果为 `optedin`，将会立即发送点击。
   * 如果为 `optedout`，将会丢弃点击。
   * 如果为 `optunknown`，当您的报表包启用了时间戳时，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。

      如果您的报表包未启用时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

      这仅设置初始值。 如果在代码中设置或更改了此值，则会使用新值，直到再次进行更改或者卸载并重新安装应用程序为止。默认值为 `optedin`。

   * 最低 SDK 版本：4.0

* **referrerTimeout**

   SDK在初始启动时等待获取推荐人数据的秒数，然后超时。 如果您使用客户获取，我们建议使用5秒超时。

   >[!IMPORTANT]
   >
   >这是客户获取的必需变量。如果将该变量设置为 `0` 或未包含该变量，SDK 将不会等待客户获取数据，而且也不会跟踪客户获取量度。

   * 最低 SDK 版本：4.1

* **remotes**

   自动配置并定义动态配置文件的 Adobe 托管端点。每次启动时会针对当前版本检查每个配置文件的最近更新时间，并且会下载并保存所做的更新。

   * `analytics.poi` 是托管的 POI 配置的端点。

   * `messages` 是托管的应用程序内消息配置的端点。

   * 最低 SDK 版本：4.2

* **rsids**

   一个或多个用于接收Analytics数据的报表包。 多个报表包ID应以逗号分隔，中间不应有空格。

   ```js
   "rsids": "rsid"
   ```

   ```js
   "rsids" : "rsid1,rsid2" 
   ```

   >[!IMPORTANT]
   >
   >这是 Analytics 的必需变量。

   * 最低 SDK 版本：4.0

* **server**

   基于父节点的 Analytics 或受众管理服务器。

   应当使用不含 `https://` 或 `https://` 协议前缀的服务器域填充此变量。此前缀基于 `ssl` 变量，将由库自动处理。

   如果 `ssl` 为 `true`，则对此服务器进行安全连接。如果 `ssl` 为 `false`，则对此服务器进行非安全连接。

   >[!IMPORTANT]
   >
   >这是 Analytics 和/或受众管理的必需变量。

   * 最低 SDK 版本：4.0

* **ssl**

   >[!IMPORTANT]
   >
   > 从版本 4.10.0 开始，如果未设置标记，则 SSL 默认为 true。

   启用 (`true`) 或禁用 (`false`) 使用 SSL (HTTPS) 发送测量数据的功能。

   “回调”消息模板的定义如下所示：

   ```js
   "payload":{
       "templateurl":"",//required-will be token-expanded prior to being sent
       "templatebody":"",//optional-if this length > 0, POST will be used as transport method. This is a base64 encoded blob,which will be decoded and token-expanded prior to being sent.
       "contenttype":"",//optional-if this is length > 0 and POST type is selected this will be set as the Content-Typeheader. if this is not supplied for a POST request,the default will be "application/x-www-form-urlencoded"
       "timeout":0//optional-numberofsecondstowaitbeforetimingout.Defaultis2.} 
   ```

   代码中的 `payload` 对象是用于消息定义的有效负荷示例，将会进入 `ADBMobileConfig.json` 文件中。有关更多信息，请参阅[回发](/help/ios/analytics-main/postback/postback.md)。

   * 最低 SDK 版本：4.0

* **timeout**

   确定 Target 等待响应的时间。

   * 最低 SDK 版本：4.0


## `ADBMobileConfig.json` 示例文件 {#section_52FA7C71A99147AFA9BE08D2177D8DA7}

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

消息节点由Adobe Mobile Services自动生成，通常不需要手动更改。 提供以下说明用于故障排除：

* &quot;messageId&quot;

   * 生成的ID，必需

* “模板”

   * “alert”、“fullscreen”或“local”
   * 必需

* &quot;有效负荷&quot;

   * &quot;html&quot;

      * 仅限全屏模板，必需
      * 定义消息的html
   * &quot;image&quot;

      * 仅限全屏，可选
      * 要用于全屏图像的图像的url
   * &quot;altImage&quot;

      * 仅限全屏，可选
      * 在
         `image` 中指定的 url 不可访问时要使用的捆绑图像的名称
   * “标题”

      * 全屏和警报，必需
      * 全屏或警报消息的标题文本
   * “内容”

      * 警报和本地通知，必需
      * 警报消息的子文本或本地通知消息的通知文本
   * &quot;确认&quot;

      * 警报，可选
      * “确认”按钮中使用的文本
   * “取消”

      * 警报，必需
      * “取消”按钮中使用的文本
   * &quot;url&quot;

      * 警报，可选
      * 单击确认按钮时要加载的url操作
   * “等待”

      * 本地通知，必需
      * 在匹配本地通知标准后等待发布的时间（以秒为单位）









* &quot;showOffline&quot;

   * true或false
   * default为false

* &quot;showRule&quot;

   * “always”、“once”或“untilClick”
   * 必需

* &quot;endDate&quot;

   * 自1970年1月1日以来的秒数
   * 默认为 2524730400

* &quot;startDate&quot;

   * 自1970年1月1日以来的秒数
   * 默认为 0

* &quot;audiences&quot;

   一个用来定义消息显示方式的对象数组：

   * &quot;key&quot;

      要在点击中查找的变量名称，它是必需的。

   * &quot;matches&quot;

      进行比较时使用的匹配程序类型：

      * eq =等于
      * ne =不等于
      * co =包含
      * nc =不包含
      * sw =开始
      * ew =结尾
      * ex =存在
      * nx =不存在
      * lt =小于
      * le =小于或等于
      * gt =大于
      * ge =大于或等于
   * &quot;values&quot;

      一个用来匹配以下命名的变量值的值数组：

      * key
      * 匹配器类型
      * matches


* &quot;triggers&quot;

   与受众相同，不过，这里是操作而非受众：

   * &quot;key&quot;
   * &quot;matches&quot;
   * &quot;values&quot;
