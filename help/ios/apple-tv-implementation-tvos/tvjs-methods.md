---
description: 以下是 tvOS 库提供的 TVJS 方法列表。
seo-description: 以下是 tvOS 库提供的 TVJS 方法列表。
seo-title: TVJS 方法
solution: Marketing Cloud,Analytics
title: TVJS 方法
topic: 开发人员和实施
uuid: a7bfa85a-0d6e-4f51-9a9e-70429c2a9806
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# TVJS 方法 {#tvjs-methods}

以下是 tvOS 库提供的 TVJS 方法列表。

## Configuration methods {#section_5F82FD2F6A0546B3B4E80DF832E11634}

* **版本**

   返回 Adobe Mobile 库的当前版本。

   * 下面是这种方法对应的语法：

      ```objective-c
      version()
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      var sdkVersion = ADBMobile.version();
      ```

   * 返回结果: `String`

* **privacyStatus**

   返回当前用户隐私状态枚举的 NSUInteger 表示形式。

   选项如下：

   * `ADBMobilePrivacyStatusOptIn`:点击会立即发送。
   * `ADBMobilePrivacyStatusOptOut`:将丢弃点击。
   * `ADBMobilePrivacyStatusUnknown`：如果启用了离线跟踪，将会保存点击，直到隐私状态更改为选择启用（发送点击）或选择禁用（丢弃点击）。

      如果未启用离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。THe default value is set in the `ADBMobileConfig.json` file.

   * 下面是这种方法对应的语法：

      ```objective-c
      privacyStatus()
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      var privacyStatus = ADBMobile.privacyStatus();
      ```

   * 返回结果: `Number`

* **setPrivacyStatus**

   将当前用户的隐私状态设置为以下值之一：

   * `ADBMobilePrivacyStatusOptIn`: Hits are sent immediately.
   * `ADBMobilePrivacyStatusOptOut`:将丢弃点击。
   * `ADBMobilePrivacyStatusUnknown`:如果启用了脱机跟踪，则会保存点击，直到隐私状态更改为选择加入（发送点击）或选择退出（丢弃点击）。
   如果未启用离线跟踪，则将丢弃点击，直到隐私状态更改为选择启用。

   * 下面是这种方法对应的语法：

      ```objective-c
      setPrivacyStatus(privacyStatus)
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.setPrivacyStatus(ADBMobilePrivacyStatusOptIn);
      ```


* **lifetimeValue**

   返回当前用户的生命周期值。默认值为 `0`.

   * 下面是这种方法对应的语法：

      ```objective-c
      lifetimeValue()
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      var ltv = ADBMobile.lifetimeValue();
      ```

   * 返回结果: `Number`

* **userIdentifier**

   如果设置了自定义标识符，则返回用户标识符。如果未设置自定义标识符，则返回 nil。默认值为 `nil`.

   >[!IMPORTANT]
   >
   >如果您的应用程序从Experience Cloud 3.x升级到4.x SDK，则会检索之前的自定义或自动生成的访客ID，并将其存储为自定义用户标识符。 这样可在 SDK 升级期间保留访客数据。对于 4.x SDK 上的新安装，用户标识符在设置之前为 nil。

   * 下面是这种方法对应的语法：

      ```objective-c
      userIdentifier()
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      var uid = ADBMobile.userIdentifier();
      ```

   * 返回结果: `String`

* **setUserIdentifier**

   设置用户标识符。

   * 下面是这种方法对应的语法：

      ```objective-c
      setUserIdentifier(userId)
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.setUserIdentifier(‘myUserId’);
      ```

   * 返回：N/A

   * 参数:  `userID`

      * 类型：字符串
      * 此用户的新标识符。

* **setAdvertisingIdentifier**

   在SDK中设置IDFA，如果已在SDK中设置IDFA，则IDFA将在生命周期中发送。 此外，也可以在信号（回发）中访问 IDFA。

   >[!IMPORTANT]
   >
   >Retrieve the IDFA from Apple APIs only if you are using an ad service. 如果您检索 IDFA 但并未正确使用它，则您的应用程序可能会被拒绝。

   * 下面是这种方法对应的语法：

      ```objective-c
      setAdvertisingIdentifier(idfa)
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.setAdvertisingIdentifier(‘myIdfa’);
      ```

   * 返回：N/A
   * 参数: `idfa`
      * 类型: `String`
      * 从 Apple API 检索 IDFA。

* **setDebugLogging**

   设置调试日志记录首选项。

   * 下面是这种方法对应的语法：

      ```objective-c
      setDebugLogging(logging)
      ```

   * 以下是这种方法的代码示例：

      ```objective-c
      `ADBMobile.setDebugLogging(true);
      ```

   * 返回：N/A
   * 参数: `logging`
      * 类型: `Bool`
      * 指示 Adobe SDK 是否应登录到调试控制台的值。


## Analytics methods {#section_F3DB9BE225F84F86BE5F8D15164C0379}

* **trackStateData**

   通过可选的上下文数据跟踪应用程序状态。状态是指您的应用程序中提供的各种视图，例如主页功能板、应用程序设置、购物车等。这些状态与网站中的页面类似，而且 trackState 调用会使页面查看次数递增。

   如果状态为空，它会在报表中显示为“应用程序名称 应用程序版本 (内部版本)”。如果您在报表中看到此值，请确保在每个 trackState 调用中设置状态。

   >[!TIP]
   >
   >这是唯一可增加页面查看次数的跟踪调用。

   * 下面是这种方法对应的语法：

      ```objective-c
      trackStateData(stateName [, contextData])
      ```

      * 返回：N/A
      * 参数: `stateName`
         * 类型: `String`
         * Page state name
      * 参数: `contextData`
         * 类型：对象
         * 用于此点击的其他上下文数据。
   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.trackStateData(‘homepage’, {‘userid’:12345});
      ```




* **trackActionData**

   跟踪您的应用程序中的操作。操作是指您的应用程序中发生的要测量的事件，例如登录、横幅点按、信息源订阅及其他量度。

   * 下面是这种方法对应的语法：

      ```objective-c
      trackActionData(actionName [, contextData])
      ```

      * 返回：N/A
      * 参数: `actionName`
         * 类型：字符串
         * 跟踪的操作的名称。
      * 参数: `contextData`
         * 类型：对象
         * 用于此点击的其他上下文数据。
   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.trackActionData(‘likeClicked’, {‘imageName’:’funnyKitty’});
      ```



* **trackLocationWithLatLonData**

   发送当前纬度和经度坐标。

   Also uses points of interest (POI) that are defined in the `ADBMobileConfig.json` file to determine whether the location that you entered as a parameter is in any of your POIs. 如果当前坐标位于定义的 POI 内，则会填充上下文数据变量，并随 `trackLocation` 调用发送该变量。

   * 下面是这种方法对应的语法：

      ```objective-c
      trackLocationWithLatLonData(lat, lon [, contextData]);
      ```

      * 返回：N/A
      * 参数: `lat`
         * 类型：数值
         * 位置的纬度。
      * 参数: `lon`
         * 类型：数值
         * 位置的经度。
      * 参数: `contextData`
         * 类型：对象
         * 用于此点击的其他上下文数据。
   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.trackLocationWithLatLonData(43.36, -116.12, null);
      ```




* **trackLifetimeValueIncreaseJsData**

   向用户的生命周期值中添加数量。

   * 下面是这种方法对应的语法：

      ```objective-c
      trackLifetimeValueIncreaseJsData(increaseAmount)
      ```

      * 返回：N/A
      * 参数: `increaseAmount`
         * 类型：数值
         * 添加到用户当前生命周期值中的数量。
   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.trackLifetimeValueIncreaseJsData(5);
      ```


* **trackTimedActionStartData**

   开始具有指定操作名称的定时操作。如果对已启动的操作调用此方法，则将覆盖上一个定时操作。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 下面是这种方法对应的语法：

      ```objective-c
      trackTimedActionStartData(name [, contextData])
      ```

      * 返回：N/A
      * 参数: `name`
         * 类型：字符串
         * 要启动的定时操作的名称。
      * 参数: `contextData`
         * 类型：对象
         * 用于此点击的其他上下文数据。
   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.trackTimedActionStartData(‘level1’, {‘userId’:42423});
      ```


* **trackTimedActionUpdateData**

   传入数据，以更新与给定操作关联的上下文数据。

   传入的数据将附加到给定操作的现有数据中，如果已经为操作定义相同的键，则会覆盖数据。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 下面是这种方法对应的语法：

      ```objective-c
      trackTimedActionUpdateData(name [, contextData])
      ```

      * 返回：N/A
      * 参数: `name`
         * 类型：字符串
         * 要更新的定时操作的名称。
      * 参数: `contextData`
         * 类型：对象
         * 用于此点击的其他上下文数据。
   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.trackTimedActionUpdateData(‘level1’);
      ```



* **trackTimedActionEndJsLogic**

   结束定时操作。

   如果提供回调函数，您可以访问最终时间值。如果未提供回调，或者回调返回 true，Adobe SDK 将自动发送点击。When a false is returned from the callback, the timed action hit is suppressed.

   * 下面是这种方法对应的语法：

      ```objective-c
      trackTimedActionEndJsLogic(name [, callback])
      ```

      * 返回：N/A
      * 参数: `name`
         * 类型：字符串
         * 要结束的定时操作的名称。
      * 参数: `callback`
         * 类型: `function(inAppDuration, totalDuration, data)`
         * Callback method that will have `inAppDuration` (number), `totalDuration` (number), and `data` (context data object) in its parameters.

            You can suppress the final hit from being sent by the SDK by returning `false` in your callback function.
      * 以下是这种方法的代码示例：

         ```objective-c
         ADBMobile.trackTimedActionEndJsLogic(‘level1’, 
         function(inAppDuration, totalDuration, data) {
             // do something with final values
             return true;
             });
         ```



* **trackingTimedActionExistsJs**

   返回定时操作是否正在进行中。

   * 下面是这种方法对应的语法：

      ```objective-c
      trackingTimedActionExistsJs(name)
      ```

      * 返回：布尔
      * 参数: `name`
         * 类型: `String`
         * 需要检查其是否存在的定时操作的名称。
   * 以下是这种方法的代码示例：


      ```objective-c
      var actionExists = ADBMobile.trackTimedActionExistsJs(‘level1’);
      ```


* **trackingIdentifier**

   返回自动生成的访客标识符。

   这是由 Adobe 服务器生成的特定于应用程序的独特访客 ID。如果在生成时无法访问 Adobe 服务器，则将使用 Apple 的 CFUUID 生成该 ID。该值在首次启动时生成，之后会存储并使用该值。在应用程序升级期间，会保留该 ID；在标准应用程序备份过程中，会保存并恢复该 ID；而在应用程序卸载时，则会删除该 ID。

   >[!TIP]
   >
   >如果您的应用程序从Experience Cloud 3.x升级到4.x SDK，则会检索之前的自定义或自动生成的访客ID，并将其存储为自定义用户标识符。 这样可在 SDK 升级期间保留访客数据。对于 4.x SDK 上的新安装，用户标识符为 `nil`，并且将使用跟踪标识符。有关更多信息，请参阅下面的 userIdentifier 行。

   * 下面是这种方法对应的语法：

      ```objective-c
      trackingIdentifier()
      ```

      * 返回结果: `String`
      * 参数：无
   * 以下是这种方法的代码示例：

      ```objective-c
      var trackingId = ADBMobile.trackingIdentifier();
      ```


* **trackingSendQueuedHits**

   强制库发送离线队列中的所有点击，而不考虑当前排队的点击量。

   * 下面是这种方法对应的语法：

      ```objective-c
      trackingSendQueuedHits()
      ```

      * 返回：N/A
      * 参数：无
   * 以下是这种方法的代码示例：


      ```objective-c
      ADBMobile.trackingSendQueuedHits();
      ```


* **trackingClearQueue**

   清除离线队列中的所有点击。

   * 下面是这种方法对应的语法：

      ```objective-c
      trackingClearQueue()
      ```

      * 返回：N/A
      * 参数：无
   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.trackingClearQueue();
      ```


* **trackingGetQueueSize**

   检索离线队列中的当前点击量。

   * 下面是这种方法对应的语法：

      ```objective-c
      trackingGetQueueSize()
      ```

      * 返回：数值
      * 参数：无
   * 以下是这种方法的代码示例：

      ```objective-c
      var queueSize = ADBMobile.trackingGetQueueSize();
      ```


## Audience Manager methods {#section_0155C4DF04644EDAAF6159C420A158DE}

* **audienceVisitorProfile**

   返回最近获取的访客资料。

   如果尚未提交任何信号，则返回 null。访客资料保存在 `NSUserDefaults` 中，以供在多次启动应用程序时轻松访问。

   * 下面是这种方法对应的语法：

      ```objective-c
      audienceVisitorProfile()
      ```

      * 返回：对象
      * 参数：无
   * 以下是这种方法的代码示例：

      ```objective-c
      var profile = ADBMobile.audienceVisitorProfile();
      ```


* **audienceDpid**

   返回当前 DPID。

   * 下面是这种方法对应的语法：

      ```objective-c
      audienceDpid()
      ```

      * 返回：字符串
      * 参数：无
   * 以下是这种方法的代码示例：

      ```objective-c
      var dpid = ADBMobile.audienceDpid();
      ```


* **audienceDpuuid**

   返回当前 DPUUID。

   * 下面是这种方法对应的语法：

      ```objective-c
      audienceDpuuid()
      ```

      * 返回结果: `String`
      * 参数：无
   * 以下是这种方法的代码示例：

      ```objective-c
      var dpuuid = ADBMobile.audienceDpuuid();
      ```


* **audienceSetDpidDpuuid**

   设置 dpid 和 dpuuid，设置后，它们将随每个信号一起发送。

   * 下面是这种方法对应的语法：

      ```objective-c
      audienceSetDpidDpuuid(dpid, dpuuid)
      ```

      * 返回：N/A
      * 参数: `dpid`
         * 类型: `String`
         * Audience Manager 数据提供程序 ID。
      * 参数: `dpuuid`
         * 类型: `String`
         * 用户和数据提供程序组合的标识符。
   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.audienceSetDpidDpuuid(‘myDpid’, ‘userDpuuid’);
      ```


* **audienceSignalWithDataJsCallback**

   向 Audience Manager 发送一个具有特征的信号，并获取回调函数中返回的匹配区段。

   * 下面是这种方法对应的语法：

      ```objective-c
      audienceSignalWithDataJsCallback(traits [, callback])
      ```

      * 参数: `traits`
         * 类型：对象
         * 此用户的特征词典。
      * 参数: `callback`
         * 类型：函数(配置文件)
         * 在回调函数的参数中从 Audience Manager 返回的配置文件。
   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.audienceSignalWithDataJsCallback({‘trait’:’something’}, 
      function(profile) {
          //do something with the user’s segments found in profile
           });
      ```



* **audienceReset**

   重置 Audience Manager UUID 并清除当前访客资料。

   * 以下是这种方法的代码示例：

      ```objective-c
      audienceReset()
      ```

      * 返回：N/A
      * 参数：无
   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.audienceReset();
      ```


## ID Service methods {#section_BEB6DA612EA4423FB354B65ECC941335}

* **visitorMarketingCloudID**

   从 ID 服务中检索 Experience Cloud ID。

   * 下面是这种方法对应的语法：

      ```objective-c
      visitorMarketingCloudID()
      ```

      * 返回：字符串
      * 参数：无
   * 以下是这种方法的代码示例：

      ```objective-c
      var mcid = ADBMobile.visitorMarketingCloudID();
      ```


* **visitorSyncIdentifiers**

   除了 Experience Cloud ID 之外，您还可以设置其他与每个访客关联的客户 ID。访客 API 接受同一访客具有多个客户 ID，并且使用客户类型标识符区分不同客户 ID 的适用范围。此方法对应于 JavaScript 库中的 setCustomerIDs。

   * 下面是这种方法对应的语法：

      ```objective-c
      visitorSyncIdentifiers(identifiers)
      ```

      * 返回：N/A
      * 参数: `identifiers`

         * 类型: `Object`
         * 用于同步到此用户的 ID 服务的标识符。
   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.visitorSyncIdentifiers({‘idType’:’idValue’});
      ```


* **visitorSyncIdentifiersAuthenticationState**

   将提供的标识符同步到 ID 服务。

   * 下面是这种方法对应的语法：

      ```objective-c
      visitorSyncIdentifiersAuthenticationState(identifiers, authState)
      ```

      * 返回：N/A
      * 参数: `identifiers`
         * 类型: `Object`
         * 用于同步到此用户的 ID 服务的标识符。
      * 参数: `authState`
         * 类型：ADBMobileVisitorAuthenticationState
         * 用户的身份验证状态和可能的值包括：
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.visitorSyncIdentifiersAuthenticationState({'myIdType':'valueForUser'}, ADBMobileVisitorAuthenticationStateLoggedOut)
      ```



* **visitorSyncIdentifierWithTypeIdentifierAuthenticationState**

   将提供的标识符类型和值同步到 ID 服务。

   * 下面是这种方法对应的语法：

      ```objective-c
      visitorSyncIdentifierWithTypeIdentifierAuthenticationState(idType, identifier, authState)
      ```

      * 退货：N/A
      * 参数: `idType`
         * 类型: `String`
         * 正在同步的标识符类型。
      * 参数: `identifier`
         * 类型: `String`
         * 正在同步的标识符值。
      * 参数: `authState`
         * 类型：ADBMobileVisitorAuthenticationState用户的身份验证状态。 可能的值包括：
            * `ADBMobileVisitorAuthenticationStateUnknown`
            * `ADBMobileVisitorAuthenticationStateAuthenticated`
            * `ADBMobileVisitorAuthenticationStateLoggedOut`
   * 以下是这种方法的代码示例：

      ```objective-c
      ADBMobile.visitorSyncIdentifierWithTypeIdentifierAuthenticationState('myIdType', 'valueForUser', 
      ADBMobileVisitorAuthenticationStateAuthenticated);
      ```


* **visitorGetIDsJs**

   检索只读 ADBVisitorID 对象的数组。以下代码示例是一个 VisitorID 对象示例：

   ```js
   {
       idType: "abc",
       authenticationState: 1, 
       identifier: "123"
   }
   ```

   * 下面是这种方法对应的语法：

      ```objective-c
      visitorGetIDsJs()
      ```

      * 返回结果: `Array [Object]`

      * 参数：无
   * 以下是这种方法的代码示例：

      ```objective-c
      var myVisitorIds = ADBMobile.visitorGetIDsJs();
      ```


## Target methods {#section_F9F7EC2B9B7C41AFBCA2458F9F138634}

* **targetThirdPartyID**

   返回第三方 ID。

   * 下面是这种方法对应的语法：

      ```objective-c
      targetThirdPartyID()
      ```

      * 返回结果: `String`
      * 参数：无
   * 以下是这种方法的代码示例：

      ```objective-c
      var thirdPartyID = ADBMobile.targetThirdPartyID();
      ```


* **targetSetThirdPartyID**

   设置第三方 ID。

   * 下面是这种方法对应的语法：

      ```objective-c
      targetSetThirdPartyID(thirdPartyID)
      ```

      * 返回：N/A
      * 参数: `thirdPartyID`
         * 类型: `String`
         * 用于目标请求的第三方 ID。
   * 以下是这种方法的代码示例：
   ```objective-c
   ADBMobile.targetSetThirdPartyID(‘thirdPartyID’);
   ```

* **targetPcID**

   返回 PcID。

   * 下面是这种方法对应的语法：

      ```objective-c
      targetPcID()
      ```

      * 返回结果: `String`
      * 参数：无
   * 以下是这种方法的代码示例：

      ```objective-c
      var pcID = ADBMobile.targetPcID();
      ```


* **targetSessionID**

   返回会话 ID。

   * 下面是这种方法对应的语法：

      ```objective-c
      targetSessionID()
      ```

      * 返回结果: `String`
      * 参数：无
   * 以下是这种方法的代码示例：

      ```objective-c
      var sessionID = ADBMobile.targetSessionID();
      ```
