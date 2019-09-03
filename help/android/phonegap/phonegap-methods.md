---
description: 您可以使用 iOS PhoneGap 插件方法完成多种任务。
keywords: android；库；移动；sdk
seo-description: 您可以使用 iOS PhoneGap 插件方法完成多种任务。
seo-title: PhoneGap插件方法
solution: Marketing Cloud，Analytics
title: PhoneGap插件方法
topic: 开发人员和实施
uuid: bc3db9ce-81b7-45ec-88aa-6020c1db5d9c
translation-type: tm+mt
source-git-commit: e481b046769c3010c41e1e17c235af22fc762b7e

---


# PhoneGap plug-in methods{#phonegap-plug-in-methods}

您可以使用 Android PhoneGap 插件方法完成多种任务。

In `html` files where you want to use tracking, add the following to the `<head>` tag:

```js
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

## Configuration methods {#section_CC429F68292D4601AEEF0A91445E1185}

* **getPrivacyStatus**

   返回当前用户的隐私状态。

   以下是可用的状态：

   * `ADB.optedIn`：点击将立即发送。
   * `ADB.optedOut`：点击将被丢弃。
   * `ADB.optUnknown`：如果您的报表包 **启用** 了时间戳，则会保存点击，直到隐私状态更改变为加入(点击)或退出(点击被丢弃)。如果您的报表包&#x200B;**未启用**&#x200B;时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

      默认值在 `ADBMobileConfig.json` 文件中设置。

   * 以下是这种方法的代码示例：

      ```java
      getPrivacyStatus(function (value) { myTempVal = value; }, function () {myTempVal = null;}); 
      ```

* **setPrivacyStatus**

   将当前用户的隐私状态设置为 `status`。

   您可以设置以下状态之一：

   * `ADB.optedIn`：点击将立即发送。
   * `ADB.optedOut`：点击将被丢弃。
   * `ADB.optUnknown`：如果您的报表包 **启用** 了时间戳，则会保存点击，直到隐私状态更改变为加入(点击)或退出(点击被丢弃)。如果您的报表包&#x200B;**未启用**&#x200B;时间戳，则将丢弃点击，直到隐私状态更改为选择启用。

   * 以下是这种方法的代码示例：

      ```java
      ADB.setPrivacyStatus('ADB.optedIn');
      ```

* **getLifetimeValue**

   返回当前用户的生命周期值。默认值为 0。

   * 以下是这种方法的代码示例：

      ```java
      ADB.getLifetimeValue(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

* **setDebugLogging**

   Enables (`true`) or disables (`false`) viewing debug information. 默认情况下，此变量为 `false`.

   * 以下是这种方法的代码示例：

      ```java
      ADB.setDebugLogging(true);
      ```

* **getVersion**

   获取库版本。

   * 以下是这种方法的代码示例：

      ```java
      ADB.getVersion(function (value) { versionNum = value }, function () { versionNum = 1.0;});
      ```

* **trackingIdentifier**

   返回自动生成的访客标识符。

   这是特定于应用程序的独特访客 ID，该 ID 在首次启动应用程序时生成，之后会存储并使用该 ID。在应用程序升级期间，会保留该 ID，而在应用程序卸载时，则会将其删除。

   >[!TIP]
   >
   >如果您的应用程序升级从Experience Cloud3.x到4.x SDK，则会检索之前的访客ID(自定义或自动生成)，并作为自定义用户标识符存储。有关更多信息，请参阅下面的 `getUserIdentifier`。此 ID 用于在 SDK 升级期间保留访客数据。

   对于 4.x SDK 上的新安装，用户标识符为 `null`，并且将使用跟踪标识符。

   * 以下是这种方法的代码示例：

      ```java
      ADB.trackingIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

* **getUserIdentifier**

   如果已设置客户的用户标识符，则会返回该标识符；如果未设置该标识符，则会返回 `null`。默认值为 `null`.

   * 以下是这种方法的代码示例：

      ```java
      getUserIdentifier(function(value) { myTempVal = value; }, function () { myTempVal = null; });
      ```

* **setUserIdentifier**

   将用户标识符设置为 `identifier`。

   * 以下是这种方法的代码示例：

      ```java
      ADB.setUserIdentifier('testUser');
      ```

* **setPushIdentifier**

   设置推送通知的设备令牌。

   ```java
   getUserIdentifier(function (value) { myTempVal = value; }, function () { myTempVal = null; });
   ```

   * 下面是这种方法对应的语法：

      ```java
      ADB.setPushIdentifier(pushIdentifier, success, fail);
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.setPushIdentifier('test_push_identifier',function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **keepLifecycleSessionAlive**

   设置使生命周期会话保持活动状态的首选项。

   >[!IMPORTANT]
   >
   >Calling `keepLifecycleSessionAlive` prevents your app from launching a new session the next time it is resumed from background. 仅当您的应用程序在后台注册通知时，才应使用此方法。

   * 以下是这种方法的代码示例：

      ```js
      ADB.keepLifecycleSessionAlive(); 
      ```

* **trackingSendQueuedHits**

   无论当前使用何种批量处理选项，都强制库发送所有排队的点击。

   * 以下是这种方法的代码示例：

      ```js
      ADB.trackingSendQueuedHits();
      ```

* **trackingGetQueueSize**

   获取或设置离线队列中存储的跟踪调用的数量。

   * 以下是这种方法的代码示例：

      ```js
      ADB.trackingGetQueueSize(function (value) { myTempVal = value;}, function () { myTempVal = null;}); 
      ```

* **trackingClearQueue**

   删除离线队列中存储的所有跟踪调用。

   >[!WARNING]
   >
   >手动清除队列时要小心，因为无法撤消它。

   * 以下是这种方法的代码示例：

      ```js
      ADB.trackingClearQueue(function (value) { myTempVal = value; }, function () { myTempVal = null; }); 
      ```

## PII methods {#section_DB27270D2CEB4D369E0090FD9D1A7F81}

* **collectPII**

   提交 PII 收集请求。

   * 下面是这种方法对应的语法：

      ```javascript
      ADB.collectPII(piiData,success, fail);
      ```

   * 以下是这种方法的代码示例：

      ```javascript
      ADB.collectPII({'k1':'v1','k2':'v2','k3':'v3'}, function (value) { alert('success') },function (value) { alert('fail') ;});
      ```


## Tracking methods {#section_7946BB753A4446FE8A3ED728AEF97D04}

* **trackAdobeDeepLink**

   跟踪 Adobe 深层链接点进。

   >[!TIP]
   >
   >如果生命周期调用是启动事件，将附加Adobe链接数据，否则将发送额外的调用。

   * 下面是这种方法对应的语法：

      ```js
      ADB.trackAdobeDeepLink(deeplinkURL, success, fail); 
      ```

   * 以下是这种方法的代码示例：

      ```js
      ADB.trackAdobeDeepLink('xyz-deeplink-url',function (value) { alert('success'); },function (value) { alert('fail') }); 
      ```

* **trackState**

   通过可选的上下文数据跟踪应用程序状态。States are the views that are available in your app, such as such as `home dashboard`, `app settings`, `cart`, and so on. 这些状态与网站中的页面类似，而且 `trackState` 调用会使页面查看次数递增。

   `cData`：在上下文数据中发送的具有键值对的 JSON 对象。

   * 下面是这种方法对应的语法：

      ```js
      ADB.trackState(string stateName[,JSON cData]);
      ```

   * 以下是此方法的代码示例：

      ```js
        ADB.trackState("login&amp;nbsp;page"); 
      ```

      ```js
        ADB.trackState("login page", {"user":"john","remember":"true"});
      ```

* **trackAction**

   跟踪您的应用程序中的操作。Actions include `logins`, `banner taps`, `feed subscriptions`, and other metrics that occur in your app and that you want to measure.

   * 下面是这种方法对应的语法：

      ```js
      ADB.trackAction(string action[,JSON cData]); 
      ```

   * 以下是此方法的代码示例：

      ```js
        ADB.trackAction("login");
      ```

      ```js
        ADB.trackAction("login", {"user":"john","remember":"true"}); 
      ```

* **trackLocation**

   发送当前的 x y 坐标。此方法还使用 `ADBMobileConfig.json` 文件中定义的目标点来确定作为参数提供的位置是否位于您的任何 POI 内。如果当前坐标位于定义的 POI 内，则会填充上下文数据变量，并随 `trackLocation` 调用发送该变量。

   * 下面是这种方法对应的语法：

      ```java
      ADB.trackLocation(x, y[,JSON cData]); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.trackLocation('40.431596', '-111.893713'); 
      ```

* **trackLifetime&#x200B;ValueIncrease**

   向用户的生命周期值中添加 `amount`。

   * 下面是这种方法对应的语法：

      ```java
      ADB.trackLifetimeValueIncrease(amount[,JSON cData]); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.trackLifetimeValueIncrease('10.01'); 
      ```

* **trackTimed&#x200B;ActionStart**

   启动名为 `action` 的定时操作。

   如果对已启动的操作调用此方法，则将覆盖上一个定时操作。

   >[!TIP]
   >
   >这个调用不发送点击。

   * 下面是这种方法对应的语法：

      ```java
      ADB.trackTimedActionStart(action[,JSON cData]);
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.trackTimedActionStart("cartToCheckout"); 
      ```

* **trackTimed&#x200B;ActionUpdate**

   Pass in `cData` to update the context data that is associated with the `action`&gt;.

   传入的 `cData` 将附加到操作的现有数据中，如果已经为 `action` 定义相同的键，则会覆盖数据。

   * 下面是这种方法对应的语法：

      ```java
      ADB.trackTimedActionUpdate(String action[,JSON cData]);
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.trackTimedActionUpdate("cartToCheckout",{'SampleContextDataKey3':'SampleContextDataVal3','SampleContextDataKey4':'SampleContextDataVal4'});
      ```

* **trackTimed&#x200B;ActionEnd**

   结束定时操作。

   * 以下是这种方法的代码示例：

      ```java
      ADB.trackTimedActionEnd("cartToCheckout"); 
      ```

* **trackingTimedActionExists**

   返回定时操作是否正在进行中。

   * 下面是这种方法对应的语法：

      ```java
      ADB.trackingTimedActionExists(function (value) { myTempVal = value }, function () { myTempVal = null; }); 
      ```

## Beacon methods {#section_F9500D6BD95348E08E283C02B657019D}

* **trackBeacon**

   跟踪用户接近信标的时间。

   * 下面是这种方法对应的语法：

      ```js
      ADB.trackBeacon(uuid, major, minor, proximity, cData) 
      ```

   * 以下是这种方法的代码示例：

      ```js
      ADB.trackBeacon('2F234454-CF6D-4A0F-ADF2-F4911BA9FFA6', 1, 2, 
      ADB.beaconUnknown, {'hp':'hp_val','hp.company':'adobe'}
      ```

* **clearCurrentBeacon**

   在用户远离信标后清除信标数据。

   * 下面是这种方法对应的语法：

      ```js
      ADB.clearCurrentBeacon(success, fail)
      ```

   * 以下是这种方法的代码示例：

      ```js
      ADB.clearCurrentBeacon(); 
      ```

## Target methods {#section_8670140C5A3F455E887830AFFDF91D59}

* **targetLoadRequest**

   向您配置的 `Target` 服务器发送请求，并返回选件的字符串值。

   * 下面是这种方法对应的语法：

      ```java
      ADB.targetLoadRequest(success, fail, name, defaultContent, parameters);
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.targetLoadRequest(function&nbsp;(value)
      {myTempVal = value }, function () { myTempVal = null;},'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}); 
      ```

* **targetLoadOrderConfirmRequest**

   向您配置的 `Target` 服务器发送请求。

   * 下面是这种方法对应的语法：

      ```java
      ADB.targetLoadOrderConfirmRequest(success, fail name orderId, orderTotal, productPurchaseId, parameters); 
      ```

   * 下面是这种方法对应的语法：

      ```java
      ADB.targetLoadRequest(function (value) { myTempVal = value }
      , function ()
      { myTempVal = null; } 
      , 'name' 'orderId' 'total', 'purchaseId',
      {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}
      ); 
      ```

* **targetClearCookies**

   从共享的 Cookie 存储中清除 `Target` Cookie。

   * 以下是这种方法的代码示例：

      ```java
      ADB.targetClearCookies(); 
      ```

* **targetLoadRequestWithNameWithLocationParameters**

   Processes a `Target` service request.

   * 下面是这种方法对应的语法：

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters(
        success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters requestLocationParameters
        ); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.targetLoadRequestWithNameWithLocationParameters  (function () { alert('success'); }, function () { alert('fail'); }, ;'bannerOffer', 'none', {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'}, {'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'},{'hp':'hp_val_new','hp.company':'adobe', 'hp.val2':'hp_val2'});
      ```

* **targetLoadRequestWithName**

   Processes a `Target` service request.

   * 下面是这种方法对应的语法：

      ```java
      ADB.targetLoadRequestWithRequestName(success, fail, name, defaultContent, profileParameters, orderParameters, mboxParameters);
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.targetLoadRequestWithName(
      function (value){ // handle target success} ,
      function() { // handle target failure }, 
      "mboxName",
      "defaultContent",
      {"profileParameters":"profileParametervalues"}
      {"orderId" : "32FGJ4XK" , "orderTotal" : "123.33" , "purchasedProductIds":"[46,34]" }
      {"mboxParameters":"mboxParametersvalues"}
      );
      ```

* **targetSessionID**

   获取 Target 服务器为此访客返回的 `SessionID` Cookie 值。

   * 下面是这种方法对应的语法：

      ```java
      ADB.targetSessionID (success, fail); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.targetSessionID(function (value) { alert(value) },function (value){ alert('fail'); });  
      ```

* **targetPcID**

   获取 `PcID` 服务器为此访客返回的 `Target` Cookie 值。

   * 下面是这种方法对应的语法：

      ```java
      ADB.targetPcID (success, fail); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.targetPcID(function  (value) { alert(value) },function (value) { alert('fail'); });
      ```

* **targetSetThirdPartyID**

   为 Target 设置自定义访客 ID。

   * 下面是这种方法对应的语法：

      ```java
      ADB.targetSetThirdPartyID(thirdPartyID, success, fail); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.targetSetThirdPartyID('test-third-party-id' function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **targetThirdPartyID**

   获取 Target 的自定义访客 ID。

   * 下面是这种方法对应的语法：

      ```java
      ADB.targetThirdPartyID(success, fail);
      ```

   * 下面是此方法的代码示例：

      ```java
       ADB.targetThirdPartyID(function (value) { alert(value); },function (value) { alert('fail')__;});
      ```

## Acquisition methods {#section_EDEA25C4B2884487827069E9257A0BA6}

* **acquisitionCampaignStartForApp**

   向您配置的 Target 服务器发送请求，并返回选件的字符串值。

   * 下面是这种方法对应的语法：

      ```java
      ADB.acquisitionCampaignStartForApp(appId, data, success, fail); 
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.acquisitionCampaignStartForApp(“appId”, {‘key’:‘value’});  
      ```

## Advertising identifier {#section_194607D101B047A19C51B19E176E1500}

In the main activity that is generated by Cordova, call `Config.submitAdvertisingIdentifierTask()` in the `onResume()` method. 有关详细信息，请参阅 [配置方法](/help/android/configuration/methods.md)。

## Audience Manager methods {#section_1FD12B29A0AF41D3BEACBB3D624EA0E4}

* **audienceGetVisitorProfile**

   获取访客资料。

   * 下面是这种方法对应的语法：

      ```java
      ADB.audienceGetVisitorProfile(); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.audienceGetVisitorProfile(function(value) { profile = value;}, function() { profile = null; }); 
      ```

* **audienceGetDpuuid**

   返回 DPUUID。

   * 下面是这种方法对应的语法：

      ```java
      ADB.audienceGetDpuuid(success fail);
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.audienceGetDpuuid(function(value) { dpuuid = value;}, function(){dpuuid = null; }); 
      ```

* **audienceGetDpid**

   返回 DPID。

   * 下面是这种方法对应的语法：

      ```java
      ADB.audienceGetDpid(success, fail);
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.audienceGetDpid(function(value){dpid = value;}, function() {dpid =  null;}); 
      ```

* **audienceSetDpidAndDpuuid**

   设置 DPID 和 DPUUID。

   * 下面是这种方法对应的语法：

      ```java
      ADB.audienceSetDpidAndDpuuid(dpid, dpuuid, success, fail); 
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’, function() {…}, function(){…};
      ```

      ```java
      ADB.audienceSetDpidAndDpuuid(‘dpid’, ‘dpuuid’); 
      ```

* **audienceSignalWithData**

   处理 Audience Manager 服务请求。

   * 下面是这种方法对应的语法：

      ```java
      ADB.audienceSignalWithData(success, fail, data);
      ```

   * 以下是此方法的代码示例：

      ```java
       ADB.audienceSignalWithData(function() {}, function() {} {‘key1’: ’value1’ ‘key2’: ‘value2’}); 
      ```

      ```java
      ADB.audienceSignalWithData({‘key1’: ’value1’, ‘key2’:‘value2’}); 
      ```

* **audienceReset**

   Audience Manager UUID并清除当前访客资料。

   * 以下是这种方法的代码示例：

      ```java
      ADB.audienceReset();
      ```

## ID Service methods {#section_840B4FAEA55B466F9754148ABA15EBDA}

* **visitorGetMarketingCloudId**

   从 ID 服务返回 Experience Cloud ID。

   * 下面是这种方法对应的语法：

      ```java
      ADB.visitorGetMarketingCloudId(success, fail); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.visitorGetMarketingCloudId(function (value) { mcid = value;},function (){ mcid = null;});
      ```

* **visitorSyncIdentifiers**

   将提供的标识符与 ID 服务同步。

   * 下面是这种方法对应的语法：

      ```java
      ADB.visitorSyncIdentifiers(identifiers, success, fail); 
      ```

   * 以下是此方法的代码示例：

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’:’value_id_1’}, function() {…}, function() {…}));
      ```

      ```java
      ADB.visitorSyncIdentifiers({‘key_id_1’: ‘value_id_1’});  
      ```

* **visitorSyncIdentifiersWithAuthenticationState**

   将提供的标识符同步到 ID 服务。

   * 下面是这种方法对应的语法：

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState
      (identifiers, authenticationState, success, fail); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.visitorSyncIdentifiersWithAuthenticationState({'k1':'v1','k2':'v2','k3':'v3'}, ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success'); },function (value) { alert('fail'); }); 
      ```

* **visitorSyncIdentifierWithType**

   将提供的标识符同步到 ID 服务。

   * 下面是这种方法对应的语法：

      ```java
      ADB.visitorSyncIdentifierWithType(identifierType, identifier authenticationState, success, fail); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.visitorSyncIdentifierWithType('test-identifier-type', 'test-identifier', ADB.mobileVisitorAuthenticationStateAuthenticated, function (value) { alert('success') },function (value) { alert('fail'); }); 
      ```

* **visitorAppendToURL**

   将访客标识符附加到给定 URL。

   * 下面是这种方法对应的语法：

      ```java
       ADB.visitorAppendToURL(urlToAppend, success, fail); 
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.visitorAppendToURL('test_visitor_url', function (value) alert(value);},'');
      ```

* **visitorGetIDs**

   Returns all `visitorID`s that have been synced.

   * 下面是这种方法对应的语法：

      ```java
      ADB.visitorGetIDs (success, fail);
      ```

   * 以下是这种方法的代码示例：

      ```java
      ADB.visitorGetIDs(function (value) { alert(value); },function (value) { alert('fail') ;}); 
      ```
